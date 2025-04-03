---
tags: ""
datetimeCreate: 2025-04-03 15:17
---
エラーの原因は認証情報の取得方法にありました。解決された主な問題は以下の通りです：

1. 認証情報の取得方法:

- 修正前: 環境変数（GCP_SERVICE_ACCOUNT_EMAIL、GCP_PRIVATE_KEY）から認証情報を取得しようとしていました

- 修正後: ファイルシステムから直接google-credentials.jsonファイルを読み込むように変更しました

1. 具体的な問題点:

- 環境変数として設定された認証情報と、実際のGCPアカウント情報に不一致があった

- 特にclient_emailが正確でなかった可能性が高い（環境変数ではfinancial@gen-lang-client-0102928246.iam.gserviceaccount.comが正しく設定されていなかった）

- private_keyの形式や改行コードの扱いに問題があった可能性もあります

1. 他の要因:

- 環境変数の値が設定されていなくても、コードはエラーチェックを行わず処理を継続していた

- JSON形式の認証情報ファイルが一般的なGoogle Cloud認証の方法であり、より信頼性が高い

この解決により、正確な認証情報がGoogle Cloud APIに渡されるようになり、「invalid_grant: account not found」エラーが解消されました。JSONファイルから直接認証情報を読み込む方法は、環境変数による方法よりも安全で確実です。





```dataviewjs
dv.header(3, "関連ノート");
var maxLoop = Math.min(dv.current().file.tags.length, 3);
for(let i=0;i<maxLoop;i++){
dv.span(dv.current().file.tags[i]);
dv.list(dv.pages(dv.current().file.tags[i]).sort(f=>f.file.mtime.ts,"desc").limit(15).file.link);
}

for (let outgo of dv.pages('outgoing([[' + dv.current().file.name + ']])')) {
    dv.header(4, outgo.file.name);
    dv.list(outgo.file.inlinks.sort());
}
```