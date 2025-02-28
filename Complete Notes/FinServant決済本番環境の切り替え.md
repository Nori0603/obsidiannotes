---
tags:
  - FinServant
  - supabase
  - stripe
datetimeCreate: 2025-02-28 08:41
---

1. 開発環境では：
   - `IS_PRODUCTION=false`
   - `STRIPE_BASIC_PRICE_ID_DEV`と`STRIPE_PLUS_PRICE_ID_DEV`が使用されます
   - `SITE_URL`はローカルホストを指します

2. 本番環境に切り替える際は：
   - `IS_PRODUCTION=true`に変更
   - `STRIPE_BASIC_PRICE_ID_PROD`と`STRIPE_PLUS_PRICE_ID_PROD`が使用されます
   - `SITE_URL`を本番のURLに変更

本番環境に切り替える際は、以下のコマンドを実行します：

```bash
supabase secrets set IS_PRODUCTION=true
supabase secrets set SITE_URL=https://your-production-domain.com
```

また、実際のStripe Price IDを設定する際は、それぞれの環境のIDを正しく設定してください：

```bash
# 開発環境のPrice ID
supabase secrets set STRIPE_BASIC_PRICE_ID_DEV=price_XXXXX
supabase secrets set STRIPE_PLUS_PRICE_ID_DEV=price_XXXXX

# 本番環境のPrice ID
supabase secrets set STRIPE_BASIC_PRICE_ID_PROD=price_XXXXX
supabase secrets set STRIPE_PLUS_PRICE_ID_PROD=price_XXXXX
```

これらの値は、StripeのダッシュボードでそれぞれのプランのPrice IDを確認して設定してください。





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