---
tags: ""
datetimeCreate: 2025-04-02 22:49
---
このアプリケーションは、個人の財務状況を管理・分析するためのツールであると考えられます。主な機能として以下の3つが挙げられます。

1. ダッシュボード機能 (src/pages/dashboard/index.tsx)

- ユーザーの財務状況全体の概要を視覚的に表示します。

- 登録された資産の合計額 (AssetSummary) や、月ごとの収入・支出の推移 (MonthlyAnalytics)、カレンダー形式での取引履歴 (CalendarView)、収支の内訳を示す円グラフ (IncomeExpensePieChart) などが表示されるようです。

- 特定の年月に絞ってデータを表示する機能 (YearMonthSelector) も備えています。

- 定期的な収入や支出 (regularTransactionData) を考慮し、将来のキャッシュフロー予測なども行える可能性があります。

1. 資産管理機能 (src/pages/assets/)

- ユーザーが保有する様々な資産（例: 現金、銀行預金、株式、投資信託など）を登録し、管理するための機能です。

- 資産登録 (src/pages/assets/register/index.tsx): 新しい資産の種類、名称、現在の評価額などを入力して登録します。

- 資産一覧 (src/pages/assets/list/index.tsx): 登録されている資産を一覧で表示します。総資産額のサマリーや、資産の種類（預金・現金、投資など）ごとにグループ化されたリストが表示されるようです。

- 資産詳細 (src/pages/assets/[id]/index.tsx): 個別の資産に関する詳細情報を表示します。基本情報に加え、その資産に関する取引履歴（入金、出金、振替、評価額更新など）を確認したり、新しい取引を記録したりできます。

- 資産編集 (src/pages/assets/edit/[id].tsx): 登録済みの資産情報（名称、目標額、メモなど）を編集したり、資産自体を削除したりできます。

1. プロジェクト管理機能 (src/pages/projects/)

- 特定の目的（例: 旅行資金、住宅購入資金）や期間に基づいた予算管理を行うための機能です。「プロジェクト」という単位で財務計画を立て、進捗を追跡します。

- 新規プロジェクト作成 (src/pages/projects/new.tsx): プロジェクト名、期間、説明などを設定し、新しいプロジェクトを作成します。予算テンプレート (BudgetTemplateSelector) を利用して、関連する収入や支出の計画 (BulkPlanManager) を効率的に立てることも可能です。

- プロジェクト一覧 (src/pages/projects/index.tsx): 作成したプロジェクトを一覧で表示し、管理します。各プロジェクトの詳細ページへのリンクや編集・削除機能があります。

- プロジェクト詳細 (src/pages/projects/[id].tsx): 特定のプロジェクトの詳細情報を表示します。プロジェクトの基本情報に加え、専用の財務ダッシュボード (FinancialDashboard) や予算管理コンポーネント (BudgetManagement) を通じて、プロジェクトの収支状況や予算達成度などを確認できるようです。





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