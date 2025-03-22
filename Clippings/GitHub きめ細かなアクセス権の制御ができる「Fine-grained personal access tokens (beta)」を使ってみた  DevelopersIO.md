---
title: "[GitHub] きめ細かなアクセス権の制御ができる「Fine-grained personal access tokens (beta)」を使ってみた | DevelopersIO"
source: "https://dev.classmethod.jp/articles/github-fine-grained-personal-access-tokens/"
author:
  - "[[若槻龍太]]"
published:
created: 2025-03-10
description:
tags:
  - "clippings"
---
こんにちは、CX事業本部 IoT事業部の若槻です。

GitHubのOAuth Appsの設定を見直そうと久しぶりにDeveloper settingの画面を見ていたところ、[Personal access tokens](https://github.com/settings/tokens)メニューに**Fine-grained personal access tokens**なる項目が追加されていました。  
![](https://www.evernote.com/l/APcja-RUyFJFaozwZ9KuqtxI7LPMwWQBu88B/image.png)

昨年の10/18にBetaリリースされた機能で、従来のPersonal access tokens（classic PATs）に比べてセキュリティレベルが強化されているとのことです。

- [Introducing fine-grained personal access tokens for GitHub | The GitHub Blog](https://github.blog/2022-10-18-introducing-fine-grained-personal-access-tokens-for-github/)

## classic PATsの課題

従来のPATでは、PATを利用してアクセスできるAccount（OrganizationやUser）およびRepositoryで制限できず、また実行可能なスコープも粒度がとても粗いものでした。  
![](https://www.evernote.com/l/APeMggPxTBFKkryXN565Qxo4aadUF4v6T80B/image.png)

そのため必要以上の権限をアクセストークンに付与することになり、トークン漏洩時の影響範囲が大きくなる可能性がありました。

Fine-grained PATsではAccountやスコープをきめ細かく制御できるようになっています。

## classic PATsは近い将来使えなくなるかも

また従来のPATsは「(classic)」と付いており、Fine-grained PATsがGAされたら移行期間を設けた後に廃止されそうな雰囲気ですね。

しかし現時点ではclassic PATsを使う必要があるユースケースもあるようです。

> There are some cases where it isn’t possible to use a fine-grained PAT – yet. For now, you need to use PATs (classic) for access beyond organizations you’re a member of. That means some open source and innersource contributions cannot yet be managed with a fine-grained PAT. In addition, integrating with the enterprise account APIs also requires a PAT (classic) or oAuth app.

## Fine-grained PATsを試してみた

### トークン発行

[https://github.com/settings/tokens?type=beta](https://github.com/settings/tokens?type=beta) にアクセスして、\[Generate new token\]をクリック。  
![](https://www.evernote.com/l/APe0hiHc46NPfohs04MK-X1Jnv7Z3yPk9rkB/image.png)

アクセス対象のRepositoryを指定します。\[Resource owner\]でAccount（OrganizationまたはUser）、\[Repository access\]でRepositoryを指定します。  
![](https://www.evernote.com/l/APf69oNRCfZKObiNW95aVqUWQ4eacv9-VwMB/image.png)

そして\[Repository permissions\]でRepositoryに対して実行可能としたいパーミッションを指定します。Actionsごとに`No access`、`Read-only`および`Read and write`から指定可能です。  
![](https://www.evernote.com/l/APf-s5NcLHJHco17W6P02vQPsXcg_2PjkLEB/image.png)

下記にパーミッションとREST APIエンドポインの対応がまとまっています。

- [Permissions required for fine-grained personal access tokens - GitHub Docs](https://docs.github.com/en/rest/overview/permissions-required-for-fine-grained-personal-access-tokens?apiVersion=2022-11-28)

![](https://www.evernote.com/l/APcx_-21pJ9Fbo5t2H-O8P92VirCPLmLsRUB/image.png)

また\[Account permissions\]ではaccountに対するパーミッションを設定可能です。  
![](https://www.evernote.com/l/APdTueRFgCJNbJxheiktJR4AXLrZAc6LENcB/image.png)

最後に\[Generate token\]でトークンを発行します。  
![](https://www.evernote.com/l/APcKsD12PCFHD4NxQHUqyAvfnkVahtiR0IIB/image.png)

トークンを発行できました。  
![](https://www.evernote.com/l/APe8WBfGX3VGvb25G2ox_v4_T1g9xcccPlkB/image.png)

### トークンを使ってみる

発行したトークンを使ってREST APIへのアクセスを試してみます。

発行したトークンの\[Issues\]のパーミッションは`Read-only`としていました。  
![](https://www.evernote.com/l/APfQK_0BJ-lKh7ZAyF9eV1_AZQsCw4onymYB/image.png)

権限のあるRepositoryへのIssue一覧取得リクエストは成功します。

```shell
curl \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer ${GH_TOKEN}"\
  -H "X-GitHub-Api-Version: 2022-11-28" \
  "https://api.github.com/repos/${OWNER}/${REPO}/issues"

# -- 取得結果 --
```

権限のあるRepositoryであっても、Issue作成リクエストは、Writeパーミッションが許可されていないため、PATのパーミッション不足により失敗します。

```shell
curl \
  -X POST \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer ${GH_TOKEN}"\
  -H "X-GitHub-Api-Version: 2022-11-28" \
  https://api.github.com/repos/${OWNER}/${REPO}/issues \
  -d '{"title":"Found a bug"}'

{
  "message": "Resource not accessible by personal access token",
  "documentation_url": "https://docs.github.com/rest/reference/issues#create-an-issue"
}
```

また同じAccountがオーナーであるが権限の無いRepositoryへIssue一覧取得リクエストをすると、リソースを見つけられず失敗します。

```shell
curl \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer ${GH_TOKEN}"\
  -H "X-GitHub-Api-Version: 2022-11-28" \
  "https://api.github.com/repos/${OWNER}/${REPO2}/issues"
{
  "message": "Not Found",
  "documentation_url": "https://docs.github.com/rest/reference/issues#list-repository-issues"
}
```

ちゃんときめ細かいアクセス制御ができていますね。

## おわりに

GitHubできめ細かなアクセス権の制御ができる「Fine-grained personal access tokens (beta)」を使ってみました。

GitHubのアップデートがしっかりキャッチアップできておらず、昨年10月でのリリースを見逃していたのは痛恨の極みでした。

個人的なトークンの利用で、以前まではきめ細かい権限のアクセストークンの発行にGitHub Appsを使用していました（以下記事参照）が、期限の短い一時トークンしか発行できず頻繁にトークンを発行し直す必要があったため、今後はFine-grained personal access tokensと上手く使い分けていこうと思います。

- [GitHub Apps + GitHub Actionsで必要なアクセス権限のみ付与した一時的なアクセストークンを発行する | DevelopersIO](https://dev.classmethod.jp/articles/getting-an-access-token-with-only-the-necessary-permissions-on-github-appsgithub-actions/)

以上