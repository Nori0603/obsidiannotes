---
tags: 
datetimeCreate: 2025-05-17 13:04
---
動作成功おめでとうございます！解決できて何よりです。

今回の問題と修正点をまとめると、以下のようになります。

**問題の核心:**

Stripeのチェックアウト処理を開始するAPI (`/api/stripe/create-checkout-session`) を呼び出す際に、フロントエンド (`PricingPlans.tsx`) が**有効なアクセストークンをAPIリクエストのヘッダーに正しく付与できていなかった**ことが主な原因でした。

これにより、API側は「誰からのリクエストか不明（認証されていない）」と判断し、401 Unauthorizedエラーを返していました。

さらに、このアクセストークンを取得しようとしていた `PricingPlans.tsx` 内の `supabase.auth.getSession()` が `null` を返していたのは、**クライアントサイドのSupabase JSライブラリが管理するセッション情報と、カスタムフック `useAuthSession` が (間接的にCookie経由で) サーバーサイドから取得するセッション情報との間で、同期が取れていなかった**ためです。

具体的には：

1.  `useAuthSession` は `/api/auth/session` というAPIを呼び出し、このAPIは主にHTTP Cookieを使ってユーザーがログイン済みか判断し、ユーザー情報を返していました。この時点では、ユーザーはログインしていると認識されていました。
2.  しかし、`PricingPlans.tsx` で `supabase.auth.getSession()` を実行した際、こちらはSupabaseのクライアントライブラリがブラウザの `localStorage` などに保存しているセッショントークンを見に行きます。この `localStorage` に有効なトークンが保存されていなかった（または `/api/auth/session` がCookieで認識しているセッションと同期が取れていなかった）ため、`session` が `null` で返ってきていました。

**主な修正点:**

1.  **アクセストークンの取得元の一元化:**
    *   **`/api/auth/session/route.ts` の修正**:
        *   このAPIが、ユーザー情報やサブスクリプション情報に加えて、**有効なSupabaseのアクセストークンもレスポンスに含めて返す**ように変更しました。
        *   トークンの有効期限が切れていてリフレッシュ処理が走った場合も、新しいアクセストークンを返すようにしました。
    *   **`src/hooks/useAuthSession.tsx` の修正**:
        *   `/api/auth/session` から返されるようになったアクセストークンを受け取り、フックの利用側コンポーネント (例: `PricingPlans.tsx`) にそのアクセストークンを渡せるようにしました。
    *   **`src/components/blocks/PricingPlans.tsx` の修正**:
        *   問題の原因となっていたクライアントサイドでの `supabase.auth.getSession()` の呼び出しを**完全に削除**しました。
        *   代わりに、`useAuthSession` フックから直接アクセストークンを受け取り、それをStripeチェックアウトAPI (`/api/stripe/create-checkout-session`) 呼び出し時の `Authorization` ヘッダーに設定するようにしました。
        *   また、`useAuthSession` から渡される `authLoading` フラグをチェックし、認証情報が完全にロードされるまで処理を開始しないようにしました。

**なぜこれで解決したか:**

*   アクセストークンの「信頼できる唯一の情報源」を `/api/auth/session` エンドポイント（最終的にはCookieベースのサーバーサイド認証に依存）に統一しました。
*   フロントエンドのコンポーネントは、この信頼できる情報源から渡されたアクセストークンをそのまま使うようになったため、クライアントサイドの `localStorage` の状態とサーバーサイドのセッション状態の不整合に悩まされることがなくなりました。
*   結果として、StripeのAPIを呼び出す際に、常に有効なアクセストークンが付与されるようになり、401エラーが解消されました。

簡単に言うと、**「アクセストークン、どこから持ってくるのが一番確実？」という問題に対して、「サーバーが認証して発行（または検証）したトークンを、カスタムフック経由で直接コンポーネントに渡す」という流れに整理した**ことで、問題が解決しました。

この一連の修正で、アプリケーションの認証フローがより堅牢で一貫性のあるものになったかと思います。






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