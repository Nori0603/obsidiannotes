---
tags: ""
datetimeCreate: 2025-04-24 21:38
---


問題の原因は次のとおりです：

## 根本原因
1. **クライアントとサーバーの認証方法の不一致**
   - Supabaseのデフォルト設定では認証トークンがローカルストレージにのみ保存され、クッキーには保存されていなかった
   - サーバーサイドAPI (`/api/auth/session`) はクッキーからトークンを探していたため、常に401エラーが返されていた

2. **認証フロー処理の不完全な実装**
   - OAuth認証（Google）後のコールバック処理でトークンがローカルストレージには保存されるが、APIが使用するクッキーに保存されていなかった
   - その結果、クライアント側では認証済みなのに、サーバー側では常に未認証状態と判断されていた

3. **トークン同期の欠如**
   - 認証状態が変化しても、ローカルストレージとクッキーの間でトークン情報が同期されていなかった
   - `/api/auth/session`エンドポイントが401エラーを返すため、フロントエンドが常にログインページにリダイレクトする無限ループが発生

## 検証ログでの証拠
```
すべてのクッキー一覧: [
  { name: '__stripe_mid', ... },
  { name: 'NEXT_LOCALE', ... },
  ...
]
リフレッシュトークン状態: { '存在': false, '長さ': undefined, '値の一部': 'なし' }
リフレッシュ失敗: リフレッシュトークンがありません
```

このログから明らかなように、認証後もクッキーに`sb-access-token`と`sb-refresh-token`が存在していませんでした。

## 解決策のポイント
1. 認証トークンをローカルストレージとクッキーの両方に保存するよう実装
2. 認証状態変更時に常にクッキーも更新するリスナーを追加
3. 複数のバックアップ戦略を実装し、どの方法でもトークンを取得できるよう堅牢化

今回の問題は、フロントエンドとバックエンドの認証状態の不一致という、SPAとサーバーサイドレンダリングを組み合わせた現代的なWebアプリケーションでよく見られる問題でした。





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