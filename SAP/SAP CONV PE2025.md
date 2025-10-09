---
tags: ""
datetimeCreate: 2025-10-09 21:55
---

## SAP S/4HANA Cloud Private Edition 2025 へのコンバージョンガイド

**公開**

**文書バージョン:** 1.0 – 2025-10-08

---

**THE BEST RUN SAP**

---

**(画像: ビジネスパーソンが複数のモニターでグラフを見ながら議論している様子)**

---

## 目次

| No. | 項目 | ページ |
| :--- | :--- | :--- |
| 1 | SAP S/4HANA Cloud Private Edition へのコンバージョンガイド | 5 |
| 2 | 導入 | 6 |
| 2.1 | コンバージョンに関する文書、ツール、およびSAPノート | 7 |
| 2.2 | コンバージョンシナリオ | 10 |
| 2.3 | コンバージョンプロセスの概要 | 12 |
| 2.4 | RISE with SAP システム移行ワークベンチ | 16 |
| 3 | コンバージョンの計画 | 18 |
| 3.1 | 分散システムランドスケープでのコンバージョン | 18 |
| 3.2 | 技術的なコンバージョンパスの選択 | 19 |
| 3.2.1 | DMOVE2S4: ステップバイステッププロセス | 21 |
| 3.3 | ランタイムの最適化 | 23 |
| 4 | コンバージョンの準備 | 25 |
| 4.1 | クラウドインフラストラクチャへの移行の準備 | 25 |
| 4.2 | システム要件 | 27 |
| 4.3 | システムランドスケープへの影響 | 28 |
| 4.4 | サポートされている開始リリース | 30 |
| 4.5 | データボリュームの削減 | 30 |
| 4.6 | メンテナンスプランナー | 31 |
| 4.7 | Simplification Item-Check | 32 |
| 4.8 | カスタムコード分析 | 35 |
| 4.9 | データ移行の検証 | 36 |
| 4.10 | アプリケーション非依存の準備作業 | 37 |
| 4.10.1 | メンテナンスプランナーの使用準備 | 37 |
| 4.10.2 | クライアント 066 の削除 | 38 |
| 4.10.3 | SAP Fiori アプリのアンインストール | 38 |
| 4.10.4 | 権限のコンバージョン準備 | 39 |
| 4.10.5 | SAP Fiori UX 有効化のためのコンバージョン準備 | 39 |
| 4.11 | アプリケーション固有の準備作業リスト | 39 |
| 5 | コンバージョンの実現 | 41 |
| 5.1 | SUM を使用したコンバージョン | 41 |
| 5.2 | SAP ECS のコンバージョン後アクティビティ | 42 |
| 6 | フォローオンアクティビティ | 45 |
| 6.1 | サイレントデータ移行 | 45 |
| 6.2 | カスタムコードの適応 | 46 |
| 6.3 | アプリケーション非依存のフォローオンアクティビティ | 47 |
| 6.3.1 | SAP S/4HANA Cloud Private Edition へのデータベース拡張機能の適応 | 47 |
| 6.3.2 | 出力管理 | 48 |
| 6.3.3 | 権限コンバージョンのフォローオンアクティビティ | 51 |
| 6.3.4 | SAP Fiori UX 有効化のためのフォローオンアクティビティ (権限を含む) | 51 |
| 6.3.5 | ユーザーインターフェースの適応 | 54 |
| 6.4 | アプリケーション固有のフォローオンアクティビティリスト | 54 |
| 6.5 | コンバージョン後の旧データクリーンアップ | 55 |
| 7 | 付録 | 56 |
| 7.1 | SAP Readiness Check と SI-Check の比較 | 56 |

---

## 文書履歴

| バージョン | 日付 | 説明 |
| :--- | :--- | :--- |
| 1.0 | 2025年10月8日 | SAP S/4HANA Cloud Private Edition 2025 のバージョン。 |

---

## 1. SAP S/4HANA Cloud Private Edition へのコンバージョンガイド

SAP S/4HANA Cloud Private Edition は、現存する最も高度なインメモリプラットフォームである SAP HANA を基盤として完全に構築された、次世代ビジネススイートです。この製品は、SAP Fiori ユーザーエクスペリエンス (UX) を採用し、新しいロールベースのユーザーエクスペリエンスコンセプトを備えた最新の設計原則を使用しています。SAP S/4HANA Cloud Private Edition への移行により、以下のような継続的なアプリケーションイノベーションの恩恵を受けることができます。

*   **SAP HANA インメモリプラットフォームに特化したアプリケーションの最適化**
    SAP S/4HANA Cloud Private Edition により、SAP はアプリケーションを最適化し、SAP HANA データベースの機能を最大限に活用します。たとえば、SAP はアグリゲートを削除し、データフットプリントを削減しました。
*   **レスポンシブなユーザーエクスペリエンスデザイン**
    SAP S/4HANA Cloud Private Edition により、SAP は最新のロールベースのユーザーエクスペリエンス (UX) でアプリケーションを設計します。
*   **コア機能の統一**
    SAP S/4HANA Cloud Private Edition により、SAP は 1 つの目的のために 1 つの機能を提供することで冗長性を排除します。

SAP S/4HANA Cloud Private Edition は、モノのインターネット (IoT)、ビッグデータ、ビジネスネットワーク、モバイルファーストなどのトピックと原則を含む、デジタルエコノミーにおいて企業がシンプルに事業を運営できるよう支援します。

このガイドでは、既存の SAP Business Suite から次世代ビジネススイートである SAP S/4HANA Cloud Private Edition へ移行するためのコンバージョンプロセスを説明します。

---

## 2. 導入

既存の SAP Business Suite システムを SAP S/4HANA Cloud Private Edition 2025 にコンバージョンする方法の概要を把握するために、このガイドを注意深くお読みください。

このガイドは、以下の文書およびツールと併用する必要があります。

*   **Simplification Item Catalog**
    このツールを使用すると、Simplification Item をオンラインで検索および参照できます。
*   **System Conversion to SAP S/4HANA using SUM 2.0 SP <最新バージョン>**
*   **Maintenance Planner User Guide**
*   **SAP Readiness Check**
    このツールは、SAP ERP 6.0 システムを分析し、関連する Simplification Item の識別、ハイレベルなカスタムコード分析、アドオンの互換性、サイジングなど、SAP S/4HANA Cloud Private Edition へのコンバージョンに関する重要な側面を強調表示します。
    **→ 推奨**
    必須ではありませんが、このツールは強く推奨されます。
*   **ASU Toolbox Application Conversion Assistant**
    ASU Toolbox はアプリケーションのビューに焦点を当てており、このガイドで言及されているより技術的なコンバージョンツールを補完するものです。そのコンテンツは定期的に更新され、コンバージョンを可能な限り効率的に達成できるようにすることを目的としています。ツールに関する情報については、SAP Note 3008338 を参照してください。
    **→ 推奨**
    必須ではありませんが、このツールは強く推奨されます。
*   **Custom Code Migration Guide for SAP S/4HANA 2025**
*   **RISE with SAP システム移行ワークベンチ**
    RISE with SAP システム移行ワークベンチは、コンバージョンに追加のガードレールを提供します。SAP S/4HANA Cloud Private Edition コンバージョンに高度に調整されているため、ハンドオーバーアクティビティのダウンタイム削減からメリットを得ることができます。ツールに関する情報については、3462243 を参照してください。

これらのツールやガイド (入手方法を含む) に関する詳細情報、およびコンバージョンに関連するその他の重要な文書や SAP Note については、セクション **コンバージョンに関する文書と SAP Note [7ページ]** を参照してください。

セクション **コンバージョンプロセスの概要 [12ページ]** では、コンバージョンの異なるフェーズと関与するツールに関する情報を提供します。

セクション **コンバージョンの準備 [25ページ]** および **コンバージョンの実現 [41ページ]** では、これらのコンバージョンフェーズの詳細が提供されます。

SAP S/4HANA 2025 で利用可能なすべての機能の概要については、機能スコープ記述 at https://help.sap.com/s4hana_op_2025 | **発見** を参照してください。

### 2.1 コンバージョンに関する文書、ツール、およびSAPノート

#### 必要な文書、ツール、およびSAPノート

コンバージョンプロジェクトを準備および実行するには、次のコンバージョン資産が必要です。

| 文書 | 利用可能場所 | 説明 |
| :--- | :--- | :--- |
| **Simplification Item Catalog** | `https://help.sap.com/shana_op_2025 > Implement > Conversion & Upgrade Assets` | Simplification in SAP Business Suite product family, such as simplified functions, merged database tables, and new data models. (PDF はまだ利用可能ですが、カタログの使用を推奨します。) |
| **System Conversion to SAP S/4HANA using SUM 2.0 SP <最新バージョン>** | `https://support.sap.com/sltoolset > Software Logistics Toolset (SL Toolset) > System Maintenance > System Maintenance Scenarios > System Conversion to SAP S/4HANA using SUM 2.0 <latest SP>` | Software Update Manager を実行するためのシステムの準備方法、その使用方法、および必要とされる一般的なフォローオンステップについて説明します。 |
| **Maintenance Planner User Guide** | `http://help.sap.com/maintenance-planner` | Maintenance Planner を使用して、必要な stack.xml ファイルとソフトウェアパッケージを計算およびダウンロードする方法について説明します。 |
| **コンバージョンに関するベストプラクティスガイド** (Note: これらは必須ではありませんが、強く推奨されます。) | `https://help.sap.com/shana_op_2025 > Implement > Conversion & Upgrade Assets` | *   **Custom Code Management (CCM)**: SAP S/4HANA への単一の SAP ERP システムのコンバージョン中の CCM のベストプラクティス。 *   **Data Volume Management (DVM)**: SAP S/4HANA への単一の SAP ERP システムのコンバージョン中の DVM のベストプラクティス。 *   **Introduction of SAP Fiori during an SAP S/4HANA Conversion**: SAP S/4HANA への単一の SAP ERP システムのコンバージョン中に SAP Fiori を導入するためのベストプラクティス。 |
| **SAP Readiness Check** | `https://help.sap.com/viewer/p/SAP_READINESS_CHECK` | このツールは、SAP ERP 6.0 システムを分析し、関連する Simplification Item の識別、ハイレベルなカスタムコード分析、アドオンの互換性、サイジングなど、SAP S/4HANA へのコンバージョンに関する重要な側面を強調表示します。 **→ 推奨**: このツールは必須ではありませんが、強く推奨されます。 |
| **ASU Toolbox Application Conversion Assistant** | SAP Note **3008338** | ASU Toolbox はアプリケーションのビューに焦点を当てており、このガイドで言及されているより技術的なコンバージョンツールを補完するものです。そのコンテンツは定期的に更新され、コンバージョンを可能な限り効率的に達成できるようにすることを目的としています。 **→ 推奨**: このツールは必須ではありませんが、強く推奨されます。 |
| **Custom Code Migration Guide for SAP S/4HANA 2025** | `https://help.sap.com/shana_op_2025 > Implement > Conversion & Upgrade Assets` | コンバージョンシナリオにおけるカスタムコードの適応方法に関する手順を提供します。 |
| **SAP S/4HANA Cloud Private Edition 2025: Release Information Note** | SAP Note **3658070** | - |
| **SAP S/4HANA Cloud Private Edition 2025: Restriction Note** | SAP Note **3659273** | - |
| **SAP FIORI for SAP S/4HANA 2025: Release Information Note** | **3493254** | - |
| **SAP S/4HANA Foundation 2025: Release Information Note** | **3568504** | - |
| **SAP S/4HANA Add-on Note** | SAP Note **2214409** | - |
| **Delivery of the SAP S/4HANA Simplification Item-Check** | SAP Notes **2399707** and **2502552** | このノートで、SAP S/4HANA Pre-Transition Check Report が提供されます。 |
| **SAP S/4HANA 2025 - application specific notes in system conversion / upgrade preparation phase** | SAP Note **3634200** | コンバージョン準備フェーズ中に発生する可能性のあるエラーに関する情報。 |
| **Additional information on converting to SAP S/4HANA using SUM 2.0 <latest version>** | SAP Note for the latest version of SUM 2.0 at `https://support.sap.com/sltoolset > Software Logistics Toolset (SL Toolset) > System Maintenance > System Maintenance Scenarios > System Conversion to SAP S/4HANA Guides for System Conversion with SUM 2.0 <latest SP>` | SAP S/4HANA へのシステムコンバージョンの前提条件と技術的な手順、および SUM フェーズ中に発生する可能性のあるエラーに関する情報。 |
| **Additional information on migrating the database to a hyperscaler using SUM 2.0 <latest version>** | SAP Note for the latest version of SUM 2.0 at `https://support.sap.com/sltoolset > Software Logistics Toolset (SL Toolset) > System Maintenance > System Maintenance Scenarios > Database Migration Option (DMO) using SUM` | データベースをハイパースケーラーに移行するための前提条件と技術的な手順、および SUM フェーズ中に発生する可能性のあるエラーに関する情報。 |
| **SAP S/4HANA 2025 - application specific notes in system conversion / upgrade follow-on phase** | SAP Note **3634222** | コンバージョンフォローオンフェーズ中に発生する可能性のあるエラーに関する情報。 |
| **SAP S/4HANA System Conversion/Upgrade: Measures to reduce technical downtime** | SAP Note **2351294** | - |
| **ABAP Platform 2025 - General Information** | SAP Note **3612209** | - |
| **Java components for S/4HANA 2025 Restrictions** | SAP Note **3612338** | - |

#### 追加情報と SAP Note

次の表に重要な追加文書と SAP Note を示します。

| 文書 | 利用可能場所 | 説明 |
| :--- | :--- | :--- |
| **SAP S/4HANA: Always-Off Business Functions** | SAP Note **2240359** | - |
| **SAP S/4HANA: Always-On Business Functions** | SAP Note **2240360** | - |
| **Uninstalling ABAP Add-ons** | SAP Note **2011192** | - |
| **Automated guided steps for enabling Note Assistant for TCI and Digitally Signed SAP Notes** | SAP Note **2836302** | - |
| **Data Migration of Financials in SAP S/4HANA: Do not migrate twice!** | SAP Note **2294486** | SAP Simple Finance、または SAP S/4HANA Finance オンプレミスエディションインストールを SAP S/4HANA にコンバージョンする場合に関連します。 |
| **Conversion of Financial Accounting to SAP S/4HANA** | SAP Note **2332030** | - |
| **S4TWL: Business partner data exchange between SAP CRM and SAP S/4HANA - required pre-conversion and post-conversion actions** | SAP Note **2285062** | - |
| **Superfluous field "BUFFERED" causes exception in Consolidation and Mass Processing and potential S/4 upgrade error** | SAP Note **2781530** | - |

### 2.2 コンバージョンシナリオ

SAP ERP 6.0 システムから SAP S/4HANA Cloud Private Edition へ移行するためのアプローチにはいくつかの種類があります。

このガイドでは、最も一般的なアプローチである**ワンステップコンバージョン**を扱います。これは、既存の SAP ERP 6.0 システムを SAP S/4HANA に移行すると同時に、システムを自社のデータセンターから SAP または IaaS プロバイダーのデータセンターへ移行するものです。システムコンバージョンは、SAP Software Update Manager (SUM) を使用してワンステップで実行され、次の変更を採用するために単一のダウンタイムが発生します。

*   移行元のシステムを自社のデータセンターから SAP またはインフラストラクチャ・アズ・ア・サービス (IaaS) プロバイダーのデータセンターへ移行する。
*   SAP ERP のデータベースを SAP HANA データベースへ移行する。
*   SAP ERP のデータモデルを SAP S/4HANA のデータモデルへコンバージョンする。
*   SAP ERP のアプリケーションコードが SAP S/4HANA Cloud Private Edition 用のものに置き換えられるソフトウェアアップグレード。

**Note**
SAP は、システムコンバージョンとそれに伴うシステム移行の技術的なタスク (SAP Enterprise Cloud Services (SAP ECS) オペレーションチームへの連携と引き渡しを含む) を達成するために、資格のある移行パートナーまたは SAP が提供するサービスの専門知識を利用することを強く推奨します。

**(図: コンバージョンシナリオの概要図)**

#### 代替コンバージョンシナリオ

上記で説明したワンステップコンバージョンに加えて、現在の SAP 製品またはソフトウェアリリースに基づいた他の移行シナリオもあります。これらのオプションは柔軟性を提供し、技術ランドスケープとビジネスニーズに最も適したパスを選択できるようにします。

1.  フェーズ化されたアプローチに従い、まずシステムを SAP S/4HANA にコンバージョンし、次に**リフト＆シフト**手順を使用してデータセンターから SAP データセンターまたはインフラストラクチャ・アズ・ア・サービス (IaaS) プロバイダーのデータセンターへ移行します。この場合、SAP システムはそのまま移行され、ソフトウェアやリリースバージョンに変更はありません。このアプローチにより、移行を段階的に管理でき、より管理しやすい移行プロセスが可能になります。
    このオプションの詳細については、**SAP S/4HANA へのコンバージョンガイド**を参照してください。さらに、**RISE with SAP Private Cloud Edition** の製品ページにある「Implement Installation and Upgrade」でリフト＆シフト手順の手順を参照してください。
2.  既にプライベートクラウド環境で SAP ERP 6.0 (いずれかの EHP 上) を実行している場合は、SAP S/4HANA へのシステムコンバージョンを単に実行できます。
    このオプションの詳細については、**SAP S/4HANA へのコンバージョンガイド**および **SAP ECC から SAP S/4HANA へのトランスフォーメーションロードマップシステムコンバージョン**を参照してください。

### 2.3 コンバージョンプロセスの概要

SAP は、SAP S/4HANA Cloud Private Edition へのコンバージョンプロセスを提供します。次の図は、プロセスに関わるツール、フェーズ、およびアクティビティの概要を示しています。

**→ 推奨**
以下のセクションで説明されている順序でアクティビティを実行することを推奨します。

**(図: コンバージョンプロセスの概要フロー)**

#### プランニングフェーズ

SAP S/4HANA Cloud Private Edition へのコンバージョンを計画する際、セットアップに必要な次の計画アクティビティを実行するようにしてください。

1.  プロジェクト計画を実行するために以下のツールを使用します。
    *   **SAP Roadmap Viewer**
        SAP Roadmap Viewer を参照して、SAP が推奨する、SAP S/4HANA Cloud Private Edition への移行に必要とされるプロジェクト手順に習熟してください。詳細については、**SAP Activate for RISE with SAP S/4HANA Cloud Private Edition** を参照してください。
    *   **Simplification Item Catalog**
        このツールを使用すると、製品バージョン別およびアプリケーションまたは機能領域別にグループ化された Simplification Item の完全なコレクションを検索または参照できます。各 Simplification Item は、ビジネスおよび技術の両方の観点からコンバージョンに必要となる手順を詳述しており、準備手順とフォローオン手順の両方が含まれ、各項目は SAP Note として利用可能です。Simplification Item Catalog は、SAP for Me - Simplification Item Catalog で見つけることができます。

    **→ ヒント**
    SAP Readiness Check for SAP S/4HANA 経由で Simplification Item も利用することを推奨します。SAP Readiness Check は、本稼働中の SAP Enterprise Resource Planning システムの構成、データ、および使用状況を分析した結果に基づいて、SAP S/4HANA へのコンバージョンに関連する Simplification Item を特定します。

    *   **SAP Readiness Check**
        SAP S/4HANA Readiness Check をできるだけ早く実行して、対応する必要のある重要なトピックと、関連する労力および必要なスキルに関する概要と計画のベースラインを取得します。SAP Readiness Check for SAP S/4HANA の使用方法の詳細については、**SAP Readiness Check** を参照してください。

2.  システムランドスケープに従ってシステムコンバージョンを計画します。例えば、本番システム、品質保証システム、開発システムからなる SAP システムランドスケープがある場合は、コンバージョン順序に関してシステムグループ全体を考慮する必要があります。
3.  システムコンバージョンをオンプレミスからプライベートクラウド環境へ同時に移行するための、技術的実現の最適なアプローチを計画し選択します。
4.  コンバージョン全体のランタイムをさらに短縮するための追加のランタイム最適化について学習します。

    詳細については、**コンバージョンの計画 [18ページ]** を参照してください。

#### 準備フェーズ

アップグレードプロセスの実現フェーズを開始する前に、次の準備アクティビティを実行する必要があります。

1.  **メンテナンスプランナー**
    コンバージョンプロセスの最初のステップとしてメンテナンスプランナーツールを実行する必要があります。このツールは、コンポーネント、アドオン、ビジネス機能が SAP S/4HANA Cloud Private Edition との互換性を確保しているかを確認し、実際のコンバージョンプロセスに使用されるスタックファイルを作成します (Software Update Manager ツールによる実行)。詳細については、**メンテナンスプランナー [31ページ]** を参照してください。
    **Note**
    このステップは必須です。なぜなら、Software Update Manager はコンバージョンプロセスにスタックファイルを必要とするからです。
    メンテナンスプランナーは、SAP S/4HANA Cloud Private Edition ではサポートされていないメンテナンスオプティマイザに取って代わりました。
2.  **クラウドインフラストラクチャへの移行**
    RISE with SAP 契約に従って、SAP S/4HANA Cloud Private Edition のステップバイステップのオンボーディングおよびシステムプロビジョニングプロセスについて学習します。これには、主要な役割、コミュニケーション、および移行のための重要な技術的準備が含まれます。
3.  **システム要件**
    システム要件、開始リリース、コンバージョンパス、およびデータボリュームを認識する必要があります。詳細については、次のセクションを参照してください。
    *   **システム要件 [27ページ]**
    *   What's the Impact on Your System Landscape? **[28ページ]**
    *   Supported Start Releases **[30ページ]**
    *   Data Volume Reduction **[30ページ]**
4.  **Simplification Item-Check**
    これらのチェックは、システムが技術的にコンバージョン可能であり、コンバージョンプロセスが完了した直後にビジネスプロセスが実行を開始できるようになるために必要な重要なステップを特定します。詳細については、**Simplification Item-Check [32ページ]** を参照してください。
    **Note**
    このステップは必須であり、Software Update Manager によって再度トリガーされます。理想的には、プロセスの早い段階で Simplification Item-Check (SI-Check) を実行し、チェックによって提供される計画情報に注意を払うようにします。これらのチェックにはスタックファイルはもう必要ないことに注意してください。
    SAP Readiness Check Versus SI-Check **[56ページ]** も参照してください。
5.  **カスタムコードの移行**
    カスタムコード移行ツールは、SAP S/4HANA Cloud Private Edition のために開発された Simplification のリストに対してカスタムコードをチェックします。詳細については、**カスタムコード分析 [35ページ]** および **カスタムコードの適応 [46ページ]** を参照してください。
    **Note**
    このステップは必須ではありませんが、強く推奨されます。理想的には、SAP S/4HANA Cloud Private Edition コンバージョンプロジェクトを既存のカスタムコードベースのハウスキーピングアクティビティと組み合わせる必要があります。特に、実稼働で使用されているカスタム開発の統合ビューが必要であり、使用されなくなったカスタムコードを削除する必要があります。
    詳細については、SAP S/4HANA のカスタムコード移行ガイド 2025 を `https://help.sap.com/s4hana_op_2025 > Implement > Conversion & Upgrade Assets` で参照してください。

    上記の上位の準備フェーズの手順 2 から 4 を推奨順序で実行することをお勧めします。ただし、技術的にはこれらを独立して、または並行して実行することも可能です。

6.  **アプリケーション非依存の準備アクティビティ**
    一般的な準備手順に加えて、アプリケーション非依存の準備作業も行う必要があります。詳細については、**アプリケーション非依存の準備作業 [37ページ]** を参照してください。
7.  **アプリケーション固有の準備アクティビティ**
    アプリケーション非依存の準備作業に加えて、アプリケーション固有の準備ステップが必要になる場合もあります。これらのステップとそれらのドキュメントは、プリチェックおよびカスタムコードチェックによって部分的に提供されます。
    必要なすべての手順の完全な概要については、Simplification Item Catalog (上記参照) を参照してください。
    重要な準備ステップの概要については、**アプリケーション固有の準備作業リスト [39ページ]** を参照してください。
    財務会計コンバージョンに関する準備の詳細については、SAP Note 2332030 を参照してください。
    詳細については、**コンバージョンの準備 [25ページ]** を参照してください。

---

## 5. コンバージョンの実現

**(図: 実現フェーズのフロー)**

### 5.1 SUM を使用したコンバージョン

Software Update Manager (SUM) は、SAP S/4HANA Cloud Private Edition へのシステムコンバージョンに使用される技術ツールです。

**Note**
SUM の前にメンテナンスプランナーを実行する必要があります。なぜなら、SUM はメンテナンスプランナーによって生成された stack.xml をインプットとして必要とするからです。詳細については、**メンテナンスプランナー [31ページ]** を参照してください。

SUM プロセス内では、次のステップがワンステップ手順 (専用の開始リリース用) で実行されます。

1.  データベース移行 (オプション)。
    ソースシステムがまだ SAP HANA データベース上で実行されていない場合は、コンバージョン中にデータベースを SAP HANA に移行するために Software Update Manager のデータベース移行オプション (DMO) を使用します。
2.  SAP S/4HANA Cloud Private Edition ソフトウェアのインストール。
3.  データの新しいデータ構造へのコンバージョン (これはデータ移行の自動化された部分です)。

SUM ダウンタイム最適化については、セクション **Runtime Optimization [23ページ]** を参照してください。

SUM の使用に関するすべての情報については、ガイド **System Conversion to SAP S/4HANA using SUM** を `http://help.sap.com/sltoolset > Software Logistics Toolset > System Maintenance > System Maintenance Scenarios > System Conversion to SAP S/4HANA using SUM 2.0 <latest SP>` で参照してください。

### 5.2 SAP ECS のコンバージョン後アクティビティ

移行全体を通して責任を共有するため、SAP との円滑な協力を確保するために引き渡しのポイントを計画する必要があります。ECS ホストシステムのシステムへのアクセスは制限されているため、標準タスクの場合はサービスリクエスト (SR) を提出する必要があります。これにより、詳細な計画と明確なコミュニケーションがさらに重要になります。

**→ ヒント**
**RISE with SAP system transition workbench** は、そのガイド付き手順とともに、すべての技術的な引き渡しステップのガイダンスを提供します。詳細については、**RISE with SAP System Transition Workbench [16ページ]** を参照してください。

#### 概要: RISE 移行プロセス

SAP Enterprise Cloud Services との迅速かつ明確なコミュニケーションの維持が不可欠です。SAP ECS は、移行プロセスが目標と整合するように、SR またはインシデントに関係なく、お客様の指示に基づいて行動します。

**(図: RISE 移行プロセスのフロー)**

#### ドライランとカットオーバー

標準の SAP S/4HANA Cloud Private Edition 基本契約の範囲内では、追加のテスト実行が提供されており、必要に応じて有料サービスとして追加できます。SAP S/4HANA コンバージョンシナリオでは、2 つのドライランが利用可能です。1 つは非本番システム (QAS、DEV など) 向け、もう 1 つは本番システム向けです。ドライランに本番ハードウェアが使用される場合、最終実行のためにターゲットシステムを再構築する必要はありません。パートナーはデータベースを効率的にドロップし、移行を続けることができます。

顧客は複数のドライランを実行できますが、ECS の移行後/ビルドアクティビティは、役割と責任に応じて制限されます。サンドボックス実行 (SBX) の場合、契約にスタンドアロン SBX が含まれていない限り、品質または本番ティアのリソースを再利用できます。

ECS の後処理は、パートナーが移行とシステムコピー後のタスクを完了した後で実行されます。これらのタスクには、パートナーまたは顧客リソースでは完了できない内部 ECS コンポーネントタスクが含まれます。移行およびカットオーバー計画に、これらのアクションをリクエストするための時間枠とリードタイムを組み込むことが重要です。

この包括的なサポートフレームワークは、SAP S/4HANA Cloud Private Edition 環境でのドライランとカットオーバー中に、体系的かつ効率的なプロセスを保証します。

---

## 6. フォローオンアクティビティ

**(図: フォローオンアクティビティのフロー)**

SAP ECS がコンバージョン後のアクティビティを完了し、システムをあなた/あなたの移行パートナーに引き渡した後、グラフィックに表示されているアクティビティのフォローアップを確実に行う必要があります。プロセス全体の概要については、コンバージョンプロセスの概要 **[12ページ]** を参照してください。

### 6.1 サイレントデータ移行

アプリケーションデータの移行は通常、リリースアップグレードまたはダウンタイム中の更新中に発生します。対照的に、Silent Data Migration Infrastructure (SDMI) は、アップグレード (またはコンバージョン) 後にビジネス運用中にゼロダウンタイムアップグレードおよび実行を可能にします。

SDMI は、少なくとも 1 つのリリースに対してアップタイム機能をサポートします。したがって、アップグレードが特定のリリースを飛び越える場合 (例: アップグレードが SAP S/4HANA 1809 から SAP S/4HANA 2020 に直接移行する場合)、スキップされたリリース (この例では SAP S/4HANA 1909) の SDMI は、ターゲットリリースに対してアップタイム機能をサポートしていない場合、ビジネスダウンタイム中に実行されます。

SAP S/4HANA 2020 (開始リリースとして) 以降、SDMI はアップタイムで 3 つのリリースをサポートし、たとえば SAP S/4HANA 2020 から SAP S/4HANA 2023 へのアップグレード (ターゲットリリースに向かって 2 つのリリースを飛び越える) でゼロダウンタイムオプション (ZDO) を持つジャンプアップグレードを可能にします。

デフォルトでは、SDMI はアップタイム中に実行されます。ジョブレポジトリからの SDMI ジョブは、システムがメンテナンスモードを終了すると、各クライアントで SDMI を個別に開始し呼び出します。関連するすべての SDMI を表示するには、トランザクション SDM\_MON を呼び出します。

アップグレード前に SDM\_USER トランザクションでユーザーを維持できます。これにより、企業標準に準拠できます。ただし、アップグレードプロセス中に Software Update Manager (SUM) によって技術ユーザーとして作成することもできます。ポストプロセッシングフェーズ中、SUM は技術ユーザーが存在するかどうかを確認します。存在しない場合、更新ログにメッセージが作成されます。ユーザーが作成されない場合、SDMI は開始できず、データは移行されません。

**Note**
SUM の実行後に技術ユーザーを作成することも可能です。詳細については、`https://help.sap.com/s4hana_op_2025 > Use Product Assistance > English > Related Information > SAP S/4HANA and SAP S/4HANA Cloud Private Edition > Enterprise Technology > ABAP Platform > Adminstrating the ABAP Platform > Administration Concepts and Tools > Solution Life Cycle Management > Silent Data Migration Infrastructure` を参照してください。

SUM は、ダウンタイム中に SDMI 処理を強制するオプションを提供します。その場合、システムがビジネス運用を再開するまでに SDMI は完了します。

**▲ 注意**
このオプションには、アップグレード手順完了後にビジネスデータが SDMI プロセスによって変更されなくなるという利点がありますが、このオプションには認識しておくべき欠点も含まれます。

*   データ移行の実行にかかる時間のために、全体のシステムビジネスダウンタイムが大幅に延長されるため、SUM は SDMI ジョブを同期的に実行し、完了するまで待機します。
*   利用可能なリソース、移行テーブルのサイズ、ダイアログワークプロセスの構成、および並列化フレームワークによっては、ダウンタイムが許容できなくなるほど長くなる可能性があります。

**Note**
すべてのクライアントで、すべての SDMI が正常に処理されていることを確認してください。そうしないと、アップグレードが未完了のままになり、一部の新しいアプリケーション機能がターゲットリリースで利用できなくなるリスクがあります。さらに、次のアップグレードを行う前に、すべての SDMI が実行される必要があります。

詳細については、以下を参照してください。

*   SAP Note **2850918**: Silent Data Migration (SDMI) in SAP S/4HANA Release のための権限要件
*   SAP Note **2664638**: クライアントでの SDMI ユーザーの作成と割り当て
*   SAP Note **2907976**: Silent Data Migration (SDMI) - FAQ
*   SAP Note **2916801**: Silent Data Migration (SDMI) Configuration Options
*   SAP Note **3382097**: SDMI Classes in the Silent Data Migration Framework in SAP S/4HANA 2023 (Details, Corrections, Special Handling)
*   SAP Note **3445802**: Silent Data Migration (SDMI) New Rows after Migration - FAQ
*   `https://blogs.sap.com/2019/10/03/s4hana-silent-data-migration-infrastructure-quick-guide/`

### 6.2 カスタムコードの適応

Software Update Manager (SUM) が技術的なコンバージョンを行った後、カスタムコードの適応を開始できます。

1.  標準トランザクション SPDD、SPAU、および SPAU\_ENH を使用して、変更および拡張機能を適応させる必要があります。
    これは、SPDD および SPAU ツールが更新されたという点を除き、以前の SAP Business Suite 製品ポートフォリオのアップグレードと同じプロセスです。
2.  SAP S/4HANA Cloud Private Edition の Simplification により、SAP S/4HANA Cloud Private Edition の簡素化による問題が発生した場合、修正する必要があります。
    問題を特定するには、変換されたシステム内で ABAP Test Cockpit (ATC) を使用し、チェックバリアント S4HANA\_READINESS でローカルにチェック実行を行います。

カスタムコードの適応には、Eclipse 用の ABAP 開発ツールを使用することを推奨します。なぜなら、SE80 は SAP S/4HANA Cloud Private Edition で必要とされるすべての開発オブジェクト (CDS View など) をもはやサポートしていないからです。

これらのツールに関する詳細情報については、SAP Help Portal の `https://help.sap.com/s4hana_pce_2025 > Product Assistance > Technology > ABAP Platform > Development Information > Application Development on AS ABAP > ABAP Development Tools for Eclipse` を参照してください。

ローカル ATC 実行およびカスタムコード移行全般に関する詳細については、Custom Code Migration Guide for SAP S/4HANA and SAP S/4HANA Private Cloud Edition の `https://help.sap.com/shana_pce_2025 > Implement > Conversion & Upgrade Assets` を参照してください。

### 6.3 アプリケーション非依存のフォローオンアクティビティ

Software Update Manager (SUM) の実行後、次のセクションで説明するフォローオンアクティビティを実行する必要があります。

#### 6.3.1 SAP S/4HANA Cloud Private Edition へのデータベース拡張機能の適応

**コンテキスト**
SAP Suite on HANA から SAP S/4HANA にシステムをコンバージョンすると、SAP HANA データベースへの変更は変更されません。ただし、変更を UI で可視化するためには、UI レイヤーで手動ステップが必要になる場合があります。

**手順**
1.  変更が必要な場合、SAP Business Suite レイヤーの関連する Core Data Service (CDS) ビューを適応させます。ABAP 開発ツールを使用して CDS ビューを拡張できます。詳細については、`https://help.sap.com/s4hana_op_2025 > Use > Product Assistance > English > Related Information > SAP S/4HANA and SAP S/4HANA Cloud Private Edition > Enterprise Technology > ABAP Platform > Developing on the ABAP Platform > Development Information > ABAP CDS Development User Guide > Tasks > Extending Data Models` を参照してください。
2.  変更が必要な場合、SAP Gateway レイヤーの CDS ビュー内の OData サービスを適応させます。
    *   CDS ビュー定義でアノテーションとして含まれている OData サービスについては、関連するアーティファクトが自動的に生成されます。SAP Gateway レイヤーでの変更は不要です。詳細については、`https://help.sap.com/s4hana_op_2025` の以下を参照してください: `Use > Product Assistance > English > Related Information > SAP S/4HANA and SAP S/4HANA Cloud Private Edition > Enterprise Technology > ABAP Platform > Developing on the ABAP Platform > Development Information > Application Development on AS ABAP > SAP (On-Premise) - ABAP Programming Model for SAP Fiori > Get Started > Developing a Simple List Reporting App > Generating OData Service With Auto-Exposure`
    *   CDS ビュー定義に含まれていない OData サービスは、Service Builder で再定義する必要があります。詳細については、`https://help.sap.com/s4hana_op_2025` の以下を参照してください: `Use > Product Assistance > English > Related Information > SAP S/4HANA and SAP S/4HANA Cloud Private Edition > Enterprise Technology > ABAP Platform > Developing on the ABAP Platform > Development Information > Gateway Foundation Developer Guide > SAP Gateway Service Builder > Data Modeling Basics > Data Modeling Options > Redefining Services`
3.  アプリをご利用の場合、ランタイム適応を使用して UI レイヤーでビューフィールドを追加、移動、または削除できます。詳細については、**ユーザーインターフェースの適応 [54ページ]** を参照してください。代替手段として、SAP UI5 拡張ポイントを使用してビューを拡張できます。詳細については、`https://help.sap.com/s4hana_op_2025` の以下を参照してください: `Use > Product Assistance > English > Related Information > SAP S/4HANA and SAP S/4HANA Cloud Private Edition > Enterprise Technology > ABAP Platform > UI Technologies > SAPUI5: UI Development Toolkit for HTML5 > Extending Apps > Using SAPUI5 Flexibility`

#### 6.3.2 出力管理

SAP S/4HANA は、新しいスタイルの出力管理を導入します。その他の既存のフレームワークも、アプリケーションに応じて使用できることに注意してください。

出力制御のカスタマイズ設定は、Customizing の **Cross-Application Components > Output Control** の下で行います。

**技術的なセットアップの概要は次のとおりです。**

**出力制御の前提条件**

*   bgRFC 構成が設定されていること
*   ストレージシステムとカテゴリが維持されていること
*   BRFplus がアクティブで利用可能であること
*   Adobe Document Services が利用可能であること (Adobe Forms を使用する場合)

**bgRFC (バックグラウンドリモートファンクションコール)**
出力制御は、出力を処理するために bgRFC を使用します。したがって、bgRFC 構成を維持する必要があります。そうしないと、出力が実行されません。

関連するすべての手順はトランザクション SBGRFCCONF で実行できます。最も重要な手順の 1 つは、bgRFC が機能するためにスーパーバイザー宛先を定義することです。
詳細については、`http://help.sap.com` でキーワード bgRFC Configuration を入力し、SAP Note **2309399** および SAP Note **1616303** を参照してください。

**ストレージシステムとカテゴリ**
出力制御には、レンダリングされたフォーム出力を PDF として保存するための定義されたストレージシステム (コンテンツリポジトリ) が必要です。
ストレージシステムを設定するには、次のナビゲーションオプションを選択します。

| SAP Menu | トランザクションコード | |
| :--- | :--- | :--- |
| SPRO ➤ Cross-Application Components ➤ Document Management ➤ General Data ➤ Settings for Storage Systems ➤ Maintain Storage System | `/nOACO` | |

ストレージタイプは、SAP System Database や HTTP コンテンツサーバー (ファイルサーバー、データベース、または外部アーカイブなど) など、ニーズに合ったものを設定できます。
ストレージシステムが利用可能になったら、事前提供されたストレージカテゴリ SOMU に割り当てる必要があります。これを行うには、次のナビゲーションオプションを選択します。

| SAP Menu | トランザクションコード | |
| :--- | :--- | :--- |
| SPRO ➤ Cross-Application Components ➤ Document Management ➤ General Data ➤ Settings for Storage Systems ➤ Maintain Storage Category | `/NOACT` | |

カテゴリ SOMU を選択します。Document Area 列については SOMU を選択します。Content Repository 列については、前の手順で作成したコンテンツリポジトリを選択します。

**Business Rule Framework plus (BRFplus)**
出力制御は、出力パラメータ決定のために BRFplus を使用します。技術的には、BRFplus は WebDynpro アプリケーションに基づいています。したがって、次の ICF サービスを設定する必要があります。

| サービスパス | 説明 |
| :--- | :--- |
| `/sap/bc/webdynpro/sap/fdt_wd_workbench` | FDT Workbench |
| `/sap/bc/webdynpro/sap/fdt_wd_object_manager` | FDT Object Manager |
| `/sap/bc/webdynpro/sap/fdt_wd_catalog_browser` | FDT Catalog Browser |

詳細については、トランザクション SICF でキーワード Active Services を `http://help.sap.com` で入力してください。
サービスを設定したら、SAP Note **2248229** から必要な BRFplus アプリケーションをダウンロードしてインストールします。

**手順:**
1. トランザクション BRF+ にアクセスします。
    必要に応じて、画面をパーソナライズし、ユーザーモードを Simple から Expert に変更します。
2. Business Rule Framework plus 画面で、**Tools ➤ XML Import** を選択します。
3. Business Rule Framework plus – XML Import 画面で、File and Transport Request の下で、インポートしたいローカルの \*.xml ファイルを参照します。ファイルを順番にインポートできます。
4. Customizing Request フィールドに、適切な Customizing Request ID を入力します。
5. **Upload XML File** を選択します。
6. **Back to Workbench** を選択します。

**Adobe Document Services (ADS)**
SAP S/4HANA のアプリケーションには、フラグメント付きの PDF ベースの印刷フォームとして実装されたデフォルトのフォームテンプレートが同梱されています。
これらはレンダリングのために ADS を必要とします。ADS はクラウドソリューションまたはオンプレミスソリューションとして利用可能です。
クラウドソリューションは、SAP Cloud Platform で提供されるサービスです。新しいソリューション Form Service by Adobe の詳細情報とドキュメントへのリンクについては、SAP Note **2219598** を参照してください。
オンプレミスソリューションの場合、ADS を実行するために AS Java インストール (ADOBE 使用タイプ付き) が必要です。
ADS 自体はバージョン 10.4 (1040.xxx) 以上である必要があります。このバージョンは、SAP NetWeaver 7.3 EHP1 SP7 (以降)、NW 7.40 SP2 (以降)、および NW 7.50 (すべての SP) で提供されます。
出力管理は SAPscript および Smart Forms もサポートしているため、ADS を必ずしも使用する必要はありません。ただし、これらの 2 つのフォームテクノロジーについては特別なカスタマイズが必要であり、制限が適用されます。詳細については、SAP Notes **2292539** および **2294198** を参照してください。

**プリンター設定**
印刷はスプールを使用して行われます。詳細については、SAP Printing Guide を `https://help.sap.com/s4hana_op_2025 > Use > Product Assistance > English > Related Information > SAP S/4HANA and SAP S/4HANA Cloud Private Edition > Enterprise Technology > ABAP Platform > Administration Concepts and Tools > Solution Life Cycle Management` で参照してください。
出力制御は、トランザクション SPAD で定義されているプリンターのショートネーム (例: LP01) を使用します。

**制限事項**
*   スプールを使用した印刷は、リリース S4CORE 1.00 SPOO では利用できません。その場合は、S4CORE 1.00 SP01 にアップグレードしてください。
*   現在、あらゆる種類のフォームに対して PDF が常に作成されます。
    これにより、次の影響があります。
    *   スプールリクエストからのドキュメントのプレビューは、デバイスタイプが PDF1 または PDFUC の場合にのみ可能です。
    *   別のデバイスタイプを使用すると、SAPscript および Smart Forms のアライメントの問題が発生する可能性があります。
    *   出力は bgRFC 経由で処理されるため、フロントエンド出力はサポートされていません。

**関連情報**
SAP Note **2228611**

#### 6.3.3 権限のコンバージョンに関するフォローオンアクティビティ

廃止されたトランザクションおよびトランザクションコードの置換について、既存のバックエンド PFCG ロールメニューを確認する必要があります。これは、トランザクション SU25 レポート **Exchange of obsolete transactions in role menu** で行うことができます。詳細については、SAP Note **2465353** を参照してください。

SAP Fiori UX を有効にする予定がある場合は、**SAP Fiori UX 有効化のためのフォローオンアクティビティ (権限を含む) [51ページ]** を参照してください。

#### 6.3.4 SAP Fiori UX 有効化のためのフォローオンアクティビティ (権限を含む)

SAP Fiori UX を有効にする予定がある場合、次のアクティビティが関連します。

| アクティビティ | 説明 |
| :--- | :--- |
| **SAP Fiori Apps Library または SAP Readiness Check のヘルプを使用して SAP Fiori コンテンツを分析する** | SAP Fiori UX は、新しい SAP Fiori アプリと、権限処理のためのカタログにバンドルされた従来の UI テクノロジーおよび SAP Fiori launchpad でのユーザーホームページの構造化のためのグループを含むロールベースのコンテンツをサポートします。SAP S/4HANA は、SAP Fiori コンテンツを構造化するための例としてビジネスロールを提供します。  分析する: SAP Fiori Apps Library で利用可能な SAP Fiori コンテンツを分析します。SAP Fiori Apps Library は、システムの使用状況に基づいた特定の SAP Fiori アプリの推奨事項を取得するためのセルフサービスも提供します。**SAP Fiori Apps Library > Get SAP Fiori App Recommendations** を参照してください。  代替案として、SAP Readiness Check for SAP S/4HANA は、トランザクションの使用履歴に基づいて SAP Fiori アプリを推奨します。機能スコープ記述の **Recommended SAP Fiori Apps** セクション (`https://help.sap.com/viewer/p/SAP_READINESS_CHECK`) を参照してください。 |
| **SAP Fiori のフロントエンドカタログを定義する** | SAP は、SAP Fiori Apps Library で見つけることができるビジネスカタログのテンプレートを提供します。テンプレートカタログがお客様のニーズに適合するかどうかを確認し、その後これらのフロントエンドカタログを適応させるか、要件に合わせて新しいカタログを作成します。既存のバックエンドトランザクションに従って、関連するバックエンドトランザクションでリッチ化します。  詳細: SAP Fiori Launchpad コンテンツと権限コンセプト (`https://help.sap.com/s4hana_op_2025 > Use > Product Assistance > English > Related Information > SAP S/4HANA and SAP S/4HANA Cloud Private Edition > Enterprise Technology > SAP Fiori > SAP Fiori Overview > Implement SAP Fiori Apps > User Management and Authorization`) も参照してください。  前提条件として、バックエンドアプリケーションの複製を実行している必要があります。セクション **Replicate App Descriptors** (`https://help.sap.com/s4hana_op_2025 > Use > Product Assistance > English > Related Information > SAP S/4HANA and SAP S/4HANA Cloud Private Edition > Enterprise Technology > SAP Fiori > SAP Fiori Overview > Implement SAP Fiori Apps > UI-Specific Implementation Tasks > Basic Information`) を参照してください。 |
| **フロントエンドのビジネスロールを定義する** | SAP は、カタログとグループへの参照を含むビジネスロールのテンプレートを提供します。必要に応じてこれらのビジネスロールをコピーして適応させることができます。アプリがカタログに含まれている場合、ユーザーが SAP Fiori launchpad からアクセスできるように、関連するカタログをフロントエンドビジネスロールに割り当てる必要があります。さらに、カタログに含まれるアプリによって使用されるアクティブ化された OData サービスについて、開始権限を追加する必要があります。 |
| **SAP Fiori ビジネスカタログをバックエンド PFCG ロールに統合する** | SAP Fiori フロントエンドと SAP S/4HANA バックエンドシステムを統合するには、フロントエンドロールに割り当てられているフロントエンドカタログを既存のバックエンド PFCG ロールに統合する必要があります。これにより、カタログ内のアプリの OData サービス開始権限がバックエンド PFCG ロールのロールメニューに複製されます。  詳細: *   SAP Fiori Launchpad Content and Authorization Concept (`https://help.sap.com/s4hana_op_2025 > Use > Product Assistance > English > Related Information > SAP S/4HANA and SAP S/4HANA Cloud Private Edition > Enterprise Technology > SAP Fiori > SAP Fiori Overview > Implement SAP Fiori Apps > User Management and Authorization`) *   `https://help.sap.com/s4hana_op_2025 > Use > Product Assistance > English > Related Information > SAP S/4HANA and SAP S/4HANA Cloud Private Edition > Enterprise Technology > ABAP Platform > UI Technologies > SAP Fiori Launchpad Administration Guide > Setting Up Authorization Roles > Configuring Roles for Catalogs, Spaces and Groups > Configure Roles for Catalogs` |
| **SAP Fiori Launchpad からの SAP Easy Access Menu およびユーザーメニューへのアクセスを設定する** | SAP Fiori launchpad の使用開始の出発点は、接続されたバックエンドシステムからの SAP Easy Access Menu およびユーザーメニューへのアクセスです。これらのメニューから、ユーザーは SAP Fiori launchpad ホームページを個別に設定できます。この構成により、既存のバックエンド SAP Easy Access Menu およびユーザーメニューへのアクセスが可能になります。  これは、フロントエンドシステムで作成された専用の SAP Fiori Launchpad コンテンツを持つユーザーのための追加のアクセスオプションでもあります。  詳細: `https://help.sap.com/s4hana_op_2025 > Use > Product Assistance > English > Related Information > SAP S/4HANA and SAP S/4HANA Cloud Private Edition > Enterprise Technology > ABAP Platform > UI Technologies > SAP Fiori Launchpad Administration Guide > Setting Up Launchpad Content > Integrating Remote Content` を参照してください。 |

#### 6.3.5 ユーザーインターフェースの適応

キーユーザーは、SmartForm コントロールを使用するアプリについて、ランタイムで変更なしの方法でユーザーインターフェース (UI) を適応させることができます。たとえば、フィールドやグループの追加、削除、または移動が可能です。Stable ID を持つ SmartForm コントロールを使用するアプリについて、ランタイム適応がサポートされています。このアプリで利用可能になったフィールドのみを追加できることに注意してください。追加のフィールドが必要な場合は、`https://help.sap.com/s4hana_pce_2025 > Product Assistance > Technology > SAP Fiori > SAP Fiori Overview > Extend and Develop SAP Fiori Apps > Extend SAP Fiori Apps` に記載されているように、作成する必要があります。

### 6.4 アプリケーション固有のフォローオンアクティビティリスト

次のリストには、重要なアプリケーション固有のフォローオン手順と、それらのドキュメントの場所が含まれています。

**Note**
このリストにはコンバージョンプロセス後に実行する必要のある重要な手順の概要が含まれていますが、完全ではありません。コンバージョン関連項目の完全なリストは、Simplification Item Catalog の概要 **[12ページ]** で説明されているように確認できます。

| アプリケーション領域ごとのフォローオンタスク | 参照 |
| :--- | :--- |
| **Finance** | 財務関連のコンバージョンタスクのドキュメントについては、SAP Note を参照してください。SAP Note **2332030** |
| **SAP Credit Management** | すべての SAP Credit Management 関連のコンバージョンタスクのドキュメントについては、SAP Note を参照してください。SAP Note **2270544** |
| **Human Resources** | HR Master Data の統合 | SAP Note **2340095** |
| **Sales: Order and Contract Management** | SD Pricing: data model changes | SAP Note **2267308** |
| | SD Rebate Processing replacement by Settlement Management | SAP Note **2226380** |
| **Retail** | Trade Promotion Management のための SD Rebate Processing の最適化 | SAP Note **2200691** |
| | Generic articles および variant data の Retail クリーンアップ | SAP Note **2350650** |
| | Documentation of site master conversion, see the SAP Note. | SAP Note **2310884** |
| **Environment, Health, and Safety** | すべての EHS 関連のコンバージョンタスクのドキュメントについては、SAP Note を参照してください。 | SAP Note **2336396** |
| **Enterprise Portfolio and Project Management** | Conversion tasks related to Commercial Project Management | SAP Note **2766260** |
| **Product Safety and Stewardship** | すべての PSS 関連のコンバージョンタスクのドキュメントについては、SAP Note を参照してください。 | SAP Note **2267461** |
| **Integration** | Business network integration: Activities after converting SAP Business Network Integration (that is, Ariba Network Integration) | SAP Note **2341836** |
| | Integration with SAP SuccessFactors Employee Central | SAP Note **2340095** |
| **Media: Media Product Master** | Media Product Master に関連するすべてのコンバージョンタスクのドキュメント。 | SAP Note **2499057** |

#### その他のフォローオンタスク

| フォローオンタスク | 参照 |
| :--- | :--- |
| Advanced Variant Configuration の有効化に関する情報については、Installation Guide for SAP S/4HANA の Follow-Up Activities for Advanced Variant Configuration セクション、`https://help.sap.com/s4hana_op_2025 > Implement > Installation Guide` のセクションを参照してください。このセクションに記載されているすべての手順を実行する必要があります。 | |

### 6.5 コンバージョン後の旧データクリーンアップ

Obsolete Data Handling Monitor を使用すると、SAP ERP システムの SAP S/4HANA へのコンバージョン後に残る可能性のある旧データを削除できます。

旧データは、多くのアプリケーション領域における SAP S/4HANA データモデルの簡素化から発生します。これらの領域には、Material Management、Financials、Sales and Distribution、Environment and Health Science などが含まれます。ソースデータは、コンバージョン中にビジネスダウンタイムが増加するため、コンバージョン中に自動的に削除されず、コンバージョン中または後に旧データストアが必要になる場合があるため、削除されません。したがって、コンバージョン結果を正常にテストおよび検証した後、Obsolete Data Handling Monitor で旧データをクリーンアップできます。

トランザクションコード **SODH** を使用して Obsolete Data Handling Monitor にアクセスできます。

---

## 7. 付録

### 7.1 SAP Readiness Check と SI-Check の比較

SAP Readiness Check ツールと Simplification Item-Check (SI-Check) ツールは、コンバージョンプロセスをサポートするために使用されます。両ツールの違いについては、コンバージョンプロセスの概要 **[12ページ]** を参照してください。次の表に両ツールの違いを説明します。

| ツール比較 | SAP Readiness Check | Simplification Item-Check (/SDF/RC\_START\_CHECK) |
| :--- | :--- | :--- |
| **Type** | 顧客セルフサービス。SAP Digital Business Services (標準サポートに含まれる) | スタンドアロンレポート |
| **SAP Solution Manager** | 不要 | 不要 |
| **User Interface** | クラウドベースの Web インターフェース | SAP GUI |
| **Included Checks** | * Simplification item relevance * カスタムコード * 推奨 SAP Fiori apps * アドオンの互換性 * SAP Custom Development プロジェクト * SAP S/4HANA サイジング * ビジネス機能 * コンバージョンまたはアップグレード前のシステム一貫性のチェック * 統合分析 | * Simplification item relevance * コンバージョンまたはアップグレード前のシステム一貫性のチェック |
| **Called by Software Update Manager (SUM)** | No | Yes |
| **Mandatory** | No | Yes |
| **Use Cases** | * Conversion to SAP S/4HANA * Upgrade to a higher SAP S/4HANA release | * Conversion to SAP S/4HANA * Upgrade to a higher SAP S/4HANA release |

SAP Readiness Check と Simplification Item-Check の両方が Simplification Item の関連性と一貫性に関する情報を表示できますが、これらは異なる目的を果たし、両方が必要です。

*   **SAP Readiness Check** は主に計画ツールであり、システムコンバージョンプロジェクトの早い段階で実行され、必要なアクティビティ (Simplification Item 関連のタスクを含む) の概要を取得します。また、プロジェクト中にこれらのアクティビティを追跡するためにも役立ちます (たとえば、Simplification Item の一貫性エラーを示すバーンダウンチャートを使用)。
*   **Simplification Item-Check** は、SUM ツールが SI-Check の最終実行を行う前の、ダウンタイムまでの Simplification Item の一貫性エラーのクリーンアップという運用レベルで使用されます。したがって、SI-Check はチェックの実行において、より詳細な制御を提供します。これには、SAP Readiness Check が行うようにすべてのチェックを実行するのではなく、修正した特定の Иラーが消えたかどうかを再確認したい場合に、個々の Simplification Item のチェックランタイムを大幅に短縮できるオプションが含まれます。

さらに、SI-Check は特定のエラータイプを免除するオプションを提供します (詳細については、下記のブログ投稿を参照)。

詳細については、以下を参照してください。

*   SAP Note **2913617** (SAP Readiness Check について)。
*   本ガイドの **Simplification Item-Check [32ページ]**
*   ブログ投稿 `https://blogs.sap.com/2018/03/26/sap-s4hana-simplification-item-check-how-to-do-it-right./`

---

## 重要な免責事項と法的情報

### ハイパーリンク

一部のリンクはアイコンやマウスオーバーテキストによって分類されています。これらのリンクは追加情報を提供します。

**アイコンについて:**

*   アイコン **(外部リンクアイコン)** が付いたリンク: SAP がホストしていない Web サイトにアクセスすることになります。このようなリンクを使用することにより、(SAP との契約で特に明記されていない限り) 次の点に同意したものとみなされます。
    *   リンク先のサイトのコンテンツは SAP のドキュメントではありません。この情報に基づいて SAP に対して製品の主張を行うことはできません。
    *   SAP はリンク先のサイトのコンテンツに同意または不同意を表明するものではなく、そのサイトの可用性や正確性を保証するものでもありません。SAP は、SAP の重大な過失または意図的な不正行為によって損害が発生した場合を除き、かかるコンテンツの使用によって生じた損害について責任を負いません。
*   アイコン **(SAP内リンクアイコン)** が付いたリンク: 特定の SAP 製品またはサービスに関するドキュメントを離れ、SAP がホストする Web サイトにアクセスすることになります。このようなリンクを使用することにより、(SAP との契約で特に明記されていない限り) この情報に基づいて SAP に対して製品の主張を行うことはできないことに同意したものとみなされます。

### 外部プラットフォームでホストされているビデオ

一部のビデオはサードパーティのビデオホスティングプラットフォームを指している場合があります。SAP は、これらのプラットフォームに保存されているビデオの将来の利用可能性を保証できません。さらに、これらのプラットフォームでホストされている広告やその他のコンテンツ (たとえば、おすすめのビデオや同じサイトでホストされている他のビデオへのナビゲーションなど) は、SAP の管理下になく、SAP の責任範囲外です。

### ベータ版およびその他の実験的機能

実験的機能は、SAP が将来のリリースについて保証する公式に提供されるスコープの一部ではありません。これは、実験的機能が SAP によっていつでも、いかなる理由でも予告なしに変更される可能性があることを意味します。実験的機能は本番使用を目的としていません。十分なバックアップが取られていないデータ、またはライブ運用環境で実験的機能を示す、テスト、検証、評価、またはその他の使用を行うことはできません。
実験的機能の目的は、早期にフィードバックを得て、顧客やパートナーが将来の製品に影響を与えられるようにすることです。フィードバックを提供することにより (たとえば、SAP Community で)、寄与または派生作業の知的財産権は SAP の独占的な所有権のままであることに同意します。

### サンプルコード

ソフトウェアコーディングおよび/またはコードスニペットは例です。これらは本番使用を目的としていません。サンプルコードは、構文および表現のルールをよりよく説明し視覚化するためだけに意図されています。SAP はサンプルコードの正確性と完全性を保証しません。SAP は、SAP の重大な過失または意図的な不正行為によって損害が発生した場合を除き、サンプルコードの使用によって生じたエラーまたは損害について責任を負いません。

### バイアスフリーの言語

SAP は、多様性とインクルージョンの文化をサポートしています。可能な限り、すべての文化、民族、性別、能力の人々を参照するために、ドキュメントでは偏りのない言語を使用します。

---

**© 2025 SAP SE または SAP 関連会社。無断複写・転載を禁じます。**

本書の一部を、SAP SE または SAP 関連会社の書面による事前の許可なく、いかなる形式または目的のためにも複製または送信することはできません。ここに記載されている情報は、予告なく変更される場合があります。

SAP SE およびその販売業者が市場に出している一部のソフトウェア製品には、他のソフトウェアベンダーの独自のソフトウェアコンポーネントが含まれています。
国ごとの製品仕様は異なる場合があります。

これらの資料は、情報提供のみを目的として、SAP SE または SAP 関連会社によって提供されており、いかなる種類の商品性または特定の目的に対する保証もありません。SAP またはその関連会社は、資料に関するエラーまたは省略については責任を負いません。SAP または SAP 関連会社の製品およびサービスに関する唯一の保証は、それらの製品およびサービスに付随する明示的な保証書に記載されているものです。ここに記載されている内容は、追加の保証を構成するものとして解釈されるべきではありません。

ここに記載されている SAP およびその他の SAP 製品およびサービス、ならびにそれぞれのロゴは、ドイツおよびその他の国における SAP SE (または SAP 関連会社) の商標または登録商標です。言及されているすべてのその他の製品名およびサービス名は、それぞれの会社の商標です。

追加の商標情報と通知については、https://www.sap.com/about/legal/trademark.html を参照してください。

**THE BEST RUN SAP**