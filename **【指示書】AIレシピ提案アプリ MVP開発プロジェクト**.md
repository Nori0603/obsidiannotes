---
tags: ""
datetimeCreate: 2025-02-27 07:37
---


**1. プロジェクト名**  
AIレシピ提案アプリ MVP開発プロジェクト

**2. 目的**  
ユーザーが入力した食材に基づき、AIがWeb検索結果を参考にレシピを生成・提案するというコアバリューが、ユーザーにとって価値があるかを検証する。同時に、選択した技術スタック（Next.js, Mastra, Vercel AI SDK, Supabase）を用いた基本機能の実装可能性と、APIコスト（Web検索API、LLM API）の概算を把握する。

**3. スコープ（範囲）**

- **含める機能 (In Scope):**
    
    - シンプルな食材入力インターフェース（テキスト入力）。
        
    - 入力食材に基づき、AIエージェントがWeb検索APIを実行する機能。
        
    - Web検索結果（スニペット等）を参考に、LLMがレシピ（材料リスト、手順）を生成する機能。
        
    - 生成されたレシピを画面に表示する機能。
        
    - 基本的なアプリケーションの骨組み（Next.js）。
        
    - （任意・推奨）APIコスト把握のための簡易的なログ収集。
        
- **含めない機能 (Out of Scope):**
    
    - ユーザー認証、アカウント作成、プロフィール機能。
        
    - レシピの保存、お気に入り機能。
        
    - 高度なパーソナライズ機能（アレルギー考慮、好み反映など）。
        
    - プレミアム機能（栄養分析、買い物リスト生成、回数無制限など）。
        
    - 音声入力。
        
    - 複雑なUI/UXデザイン、アニメーション。
        
    - Supabaseの高度な利用（リアルタイム機能、詳細なデータ管理など、初期設定は可）。
        
    - 収益化機能（決済連携など）。
        

**4. 主要機能詳細**

- **(機能1) 食材入力:**
    
    - ユーザーが1つまたは複数の食材名をテキストで入力できるシンプルなフォームを設ける。
        
- **(機能2) レシピ生成リクエスト:**
    
    - 入力された食材情報は、Next.jsのAPIルートに送信される。
        
- **(機能3) AIエージェントによる検索実行 (Mastra):**
    
    - APIルートはMastraエージェントを呼び出す。
        
    - Mastraエージェントは、受け取った食材キーワードを基に、設定されたWeb検索API（例: Tavily API, Brave Search API等、低コスト/無料枠を優先）を実行し、関連性の高いページの検索結果（URL、タイトル、スニペット）を取得する。
        
- **(機能4) LLMによるレシピ生成 (Vercel AI SDK):**
    
    - Mastraは取得した検索スニペットと食材情報をまとめ、Vercel AI SDK経由で指定のLLM（コスト効率の良いモデルを優先: 例 GPT-3.5 Turbo, Claude Haiku, Gemini 1.0 Pro/Flash等）に送信する。
        
    - LLMへのプロンプトには、「以下の食材とWeb検索結果を参考に、実用的なレシピ（材料リストと手順を含む）を生成してください」といった指示を含める。
        
- **(機能5) レシピ表示:**
    
    - LLMが生成したレシピテキストを、Next.jsのフロントエンドで整形し、ユーザーに表示する。ストリーミング表示が可能であれば実装を検討する。
        

**5. 技術スタック (MVP版)**

- **フロントエンド/API:** Next.js
    
- **AIエージェント/ツール連携:** Mastra (Web検索API実行、プロンプト生成補助)
    
- **AIレシピ生成:** Vercel AI SDK + LLM (低コストモデルを選択)
    
- **Web検索API:** Brave Search API
    
- **データベース:** Supabase (プロジェクト設定のみ、または簡易ログ用。必須ではない)
    
- **デプロイ:** Vercel
    

**6. 開発のポイント・注力事項**

- **コア機能の確実な実装:** 食材入力からレシピ表示までの基本フローを最優先で完成させる。
    
- **プロンプトエンジニアリング:** 生成されるレシピの品質を可能な限り高めるため、LLMへの指示（プロンプト）の工夫に注力する。検索スニペットを効果的に活用する方法を探る。
    
- **APIコストの意識:** 開発中から各APIの呼び出し回数やトークン数を意識し、概算コストを把握する。利用するAPIの無料枠や低コストプランを最大限活用する。
    
- **シンプルさの維持:** MVPのスコープ外の機能を作り込まないように注意し、開発速度を優先する。
    
- **早期のフィードバック:** 開発途中の段階でも、想定ユーザー（または協力者）に触ってもらい、コア機能に関するフィードバックを得る。
    

**7. 成果物**

- 上記のMVPスコープで定義された機能を持つ、動作可能なWebアプリケーション。
    
- ソースコード一式（GitHub等で管理）。
    
- （可能であれば）APIコストの概算レポート。
    
- （可能であれば）初期ユーザーからのフィードバック概要。
    

**8. 検証方法**

- 開発したMVPをターゲットユーザー（または協力者）に利用してもらい、アンケートやインタビューを通じて以下の点を評価する。
    
    - 生成されたレシピは役立つか、魅力的か？
        
    - アプリの操作は簡単か？
        
    - このサービス（の将来像）にお金を払う価値を感じるか？
        
- 開発を通じて得られたAPIコストの概算値を基に、将来的な収益モデル（価格設定、無料プラン制限など）の実現可能性を評価する。




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