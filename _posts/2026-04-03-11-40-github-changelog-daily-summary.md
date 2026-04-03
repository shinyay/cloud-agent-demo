---
layout: post
title: "GitHub Changelog 最新アップデート — Copilot SDK、Actions強化、セキュリティ刷新、Issues検索GA"
date: 2026-04-03 11:40:00 +0900
tags: [GitHub, Copilot, Actions, Security, Issues]
tone: "Strategic"
persona: "GitHub Specialist"
source_urls:
  - https://github.blog/changelog/2026-04-02-copilot-sdk-in-public-preview
  - https://github.blog/changelog/2026-04-02-copilot-usage-metrics-now-includes-per-user-github-copilot-cli-activity-in-organization-reports
  - https://github.blog/changelog/2026-04-02-github-actions-early-april-2026-updates
  - https://github.blog/changelog/2026-04-02-github-copilot-in-visual-studio-march-update
  - https://github.blog/changelog/2026-04-02-the-security-tab-is-now-security-quality
  - https://github.blog/changelog/2026-04-02-improved-search-for-github-issues-is-now-generally-available
  - https://github.blog/changelog/2026-04-02-copilot-organization-custom-instructions-are-generally-available
issue_number: 44
excerpt: "Copilot SDKパブリックプレビュー、GitHub Actionsサービスコンテナ拡張、Issues セマンティック検索GA、Security & qualityタブ刷新など、2026年4月2日のGitHub Changelog 7件を戦略的視点で分析。"
---

## 📋 Overview

2026年4月2日のGitHub Changelogでは、**7件のアップデート**が公開された。注目すべきは、Copilot SDKのパブリックプレビュー開始、GitHub Issuesのセマンティック検索GA化、そしてSecurityタブの「Security & quality」への改称だ。これらは単なる機能追加ではなく、GitHubが掲げる**「AI-native開発プラットフォーム」戦略**と**「開発者体験の統合」ビジョン**の具体的な進展として読み解くべきものである。

---

## 🚀 Key Updates

### 1. Copilot SDK — パブリックプレビュー開始 🔥

**[Copilot SDK in public preview](https://github.blog/changelog/2026-04-02-copilot-sdk-in-public-preview)**

GitHub Copilotのエージェンティックランタイムを外部アプリケーションに組み込めるSDKが、パブリックプレビューとして公開された。

**対応言語（5言語）：**
- Node.js / TypeScript: `npm install @github/copilot-sdk`
- Python: `pip install github-copilot-sdk`
- Go: `go get github.com/github/copilot-sdk/go`
- .NET: `dotnet add package GitHub.Copilot.SDK`
- Java: Maven経由で提供

**主要な機能：**
- **カスタムツール＆エージェント定義** — ドメイン固有のツールをハンドラ付きで定義し、エージェントが自動で呼び出し判断
- **システムプロンプトのきめ細かいカスタマイズ** — `replace`、`append`、`prepend`、`transform`コールバックで部分的に制御可能
- **ストリーミングレスポンス** — トークン単位でのリアルタイム配信
- **Blob添付** — 画像やバイナリデータをディスク書き込みなしでインライン送信
- **OpenTelemetryサポート** — W3Cトレースコンテキスト伝播による分散トレーシング
- **権限フレームワーク** — 承認ハンドラによる機密操作のゲーティング
- **BYOK（Bring Your Own Key）** — OpenAI、Azure AI Foundry、Anthropicの自前キーを使用可能

> 💡 **戦略的示唆：** Copilot Cloud AgentやCopilot CLIと同じプロダクションランタイムを外部に開放することで、GitHubは**AIエージェントのプラットフォーム化**を明確に進めている。BYOKサポートにより、企業が既存のAI契約を活かしながらGitHubのオーケストレーション基盤を利用できる点は、エンタープライズ採用の障壁を大幅に下げる。

---

### 2. Copilot CLI利用メトリクス — 組織レポートにユーザー別データ追加

**[Copilot usage metrics now includes per-user CLI activity](https://github.blog/changelog/2026-04-02-copilot-usage-metrics-now-includes-per-user-github-copilot-cli-activity-in-organization-reports)**

組織レベルのレポートに、個々のユーザーのCopilot CLI利用状況が追加された。

**追跡できるデータ：**
- ユーザーごとのCLI利用有無（`used_cli`フラグ）
- セッション数・リクエスト数
- トークン使用量（リクエストあたりの平均トークン数を含む）
- ユーザーごとの最終CLIバージョン

> 💡 **戦略的示唆：** エンタープライズ → 組織 → ユーザーと段階的にCLIメトリクスを展開してきたことで、管理者はCopilotの**ROI可視化とコスト配分**を精密に行えるようになった。CLIバージョンの追跡は、セキュリティパッチの適用状況把握にも直結する。

---

### 3. GitHub Actions — 2026年4月前半アップデート

**[GitHub Actions: Early April 2026 updates](https://github.blog/changelog/2026-04-02-github-actions-early-april-2026-updates)**

3つの注目アップデートが含まれる。

#### サービスコンテナのエントリポイントカスタマイズ
ワークフローYAML内で`entrypoint`と`command`キーを使い、サービスコンテナのイメージデフォルトをオーバーライドできるようになった。Docker Composeと同じ命名規則を採用しており、既存の知識がそのまま活きる。

#### OIDC トークンでリポジトリカスタムプロパティをサポート（GA）
パブリックプレビューからGAに昇格。リポジトリのカスタムプロパティ（環境タイプ、チームオーナーシップ、コンプライアンスティアなど）をOIDCトークンのクレームとして含められるようになり、クラウドプロバイダーとのきめ細かい信頼ポリシーが構築可能に。

#### Azure プライベートネットワーキング VNET フェイルオーバー（パブリックプレビュー）
プライマリサブネットが利用不能になった際に、セカンダリAzureサブネット（別リージョン可）へのフェイルオーバーが可能に。手動・自動の両方のトリガーに対応し、監査ログとメール通知も提供される。

> 💡 **戦略的示唆：** サービスコンテナのカスタマイズは長年の要望に応えるもので、複雑なCI/CDパイプラインの柔軟性が大幅に向上する。OIDC + カスタムプロパティのGA化は、エンタープライズにおけるクラウドアクセス制御の標準化を加速させる。VNETフェイルオーバーはAzureとの統合深化を示しており、ミッションクリティカルなCI/CDワークロードの耐障害性を高める。

---

### 4. GitHub Copilot in Visual Studio — 3月アップデート

**[GitHub Copilot in Visual Studio — March update](https://github.blog/changelog/2026-04-02-github-copilot-in-visual-studio-march-update)**

Visual Studio 2026におけるCopilot拡張性の大幅な強化。

**主なハイライト：**
- **カスタムエージェントの構築** — `.agent.md`ファイルでリポジトリ固有のエージェントを定義。ワークスペース認識、コード理解、ツール、モデル選択、MCP接続すべてにアクセス可能
- **エンタープライズMCPガバナンス** — 組織で使用許可するMCPサーバーをホワイトリストで制御
- **エージェントスキル** — 再利用可能な指示セットを定義し、Copilotが自動検出・適用
- **`find_symbol`ツール** — 言語対応のシンボルナビゲーション（C++、C#、Razor、TypeScript、LSP拡張対応言語）
- **Copilotによるテストプロファイリング** — Test Explorerから直接、プロファイリングエージェントによるCPU・計測データ分析
- **PerfTipsのライブプロファイリング統合** — デバッグ中のパフォーマンスヒントをCopilotが分析し、最適化を提案
- **NuGetパッケージ脆弱性修正** — Solution Explorerから直接、Copilotが依存関係の更新を推奨

> 💡 **戦略的示唆：** `.agent.md`によるカスタムエージェント定義とMCPガバナンスの組み合わせは、VS Codeだけでなく**Visual Studioエコシステム全体でAIエージェントの標準化**が進んでいることを示す。プロファイリングとセキュリティ修正の統合は、Copilotが「コード補完ツール」から「開発ライフサイクル全体のAIパートナー」へ進化している証左だ。

---

### 5. Security タブが「Security & quality」に改称

**[The Security tab is now Security & quality](https://github.blog/changelog/2026-04-02-the-security-tab-is-now-security-quality)**

リポジトリ、組織、エンタープライズの各レベルで、**Security**タブが**Security & quality**に改称された。

**変更点：**
- 「Security」→「Security & quality」タブ名変更
- 「Vulnerability alerts」→「Findings」セクション名変更
- 新たに「Code quality」セクションが追加（有効化ステータスを表示）
- 「Policy」→「Security policy」に変更

**変わらない点：**
- 既存のURL・APIエンドポイントはすべて維持（ブックマーク、スクリプト、統合の更新は不要）
- アラートタイプとデータは変更なし

> 💡 **戦略的示唆：** これはGitHub Code Qualityの一般提供に向けた布石であり、セキュリティとコード品質を**同一のナビゲーション内に統合**することで、開発者が「シフトレフト」をより自然に実践できる環境を整えている。URLの互換性維持は、エンタープライズ運用への影響を最小化する配慮だ。

---

### 6. GitHub Issues セマンティック検索 — 一般提供開始（GA）

**[Improved search for GitHub Issues is now generally available](https://github.blog/changelog/2026-04-02-improved-search-for-github-issues-is-now-generally-available)**

2026年1月のプレビュー開始からわずか3ヶ月でGAに到達。自然言語でIssueを検索し、キーワードの一致がなくても概念的に関連するIssueを見つけることができる。

**GA版の特徴：**
- **自然言語検索** — 意味ベースで関連Issueを返却。キーワード不一致でもヒット
- **ハイブリッド検索** — セマンティック検索とキーワード検索を自動的に組み合わせ
- **ベストマッチソート** — 関連度順で最も有用なIssueを上位に表示
- **API対応** — REST（`search_type=semantic`または`hybrid`）およびGraphQL（`searchType: SEMANTIC`/`HYBRID`）で利用可能
- **レート制限** — セマンティック・ハイブリッドクエリは10リクエスト/分

**実績データ：** 検索成功時に目的のIssueがトップ3に表示される確率が、従来の66%から**75%に向上**。

> 💡 **戦略的示唆：** Issue検索のセマンティック化は、Copilot Cloud Agentのような自律的なAIエージェントにとっても重要なインフラとなる。エージェントが「関連Issueの発見」をより正確に行えるようになることで、重複作業の削減やコンテキスト理解の精度が向上する。APIでの提供開始は、サードパーティツールとの連携も可能にする。

---

### 7. Copilot 組織カスタムインストラクション — 一般提供開始（GA）

**[Copilot organization custom instructions are generally available](https://github.blog/changelog/2026-04-02-copilot-organization-custom-instructions-are-generally-available)**

2025年4月にプレビュー開始した機能がGAに昇格。Copilot BusinessおよびEnterprise管理者が、組織全体のリポジトリに適用されるデフォルトのカスタムインストラクションを設定できる。

**適用範囲：**
- Copilot Chat（github.com上）
- Copilot Code Review
- Copilot Cloud Agent

> 💡 **戦略的示唆：** 組織カスタムインストラクションのGA化により、企業は**コーディング規約、セキュリティポリシー、アーキテクチャパターン**をCopilotの振る舞いとして組織的に埋め込むことが可能になった。Cloud Agentへの適用は特に重要で、AIエージェントが生成するPRが組織の基準に自動的に準拠することを意味する。

---

## 🔧 Technical Details

今回のアップデートの中で技術的に最も影響が大きいのは、以下の3点である。

### Copilot SDK のアーキテクチャ
Copilot SDKは、Copilot Cloud AgentやCopilot CLIと**同一のプロダクションランタイム**を公開する形をとっている。これにより、GitHubが内部で磨き上げたツール呼び出し、ストリーミング、ファイル操作、マルチターンセッションの仕組みをそのまま外部アプリケーションで利用できる。OpenTelemetryの組み込みサポートは、エンタープライズ環境でのオブザーバビリティ要件を満たす。

### Issues セマンティック検索 API
REST APIでは`/search/issues`エンドポイントに`search_type=semantic`または`search_type=hybrid`パラメータを追加するだけで利用可能。GraphQLでは`searchType`引数に`SEMANTIC`または`HYBRID`を指定する。フォールバックが発生した場合は、レスポンスにその理由が含まれる設計となっており、デバッグ性が考慮されている。

### Actions OIDCカスタムプロパティ
リポジトリのカスタムプロパティ（例：`environment: production`、`team: platform`、`compliance: soc2`）がOIDCトークンのクレームに含まれることで、クラウドプロバイダー側の信頼ポリシーを**リポジトリ名やIDの列挙なし**に構築できる。これは、リポジトリ数が増えてもアクセス制御の管理コストが増大しない、スケーラブルな設計だ。

---

## 💻 Developer Impact

| 対象者 | 影響度 | 主な恩恵 |
|--------|--------|---------|
| **個人開発者** | ⭐⭐⭐ | Issue検索の精度向上でトリアージ効率が上がる。Copilot SDKで独自ツール構築が可能に |
| **チームリーダー** | ⭐⭐⭐⭐ | 組織カスタムインストラクションで品質基準の自動適用。CLI利用メトリクスで採用状況を把握 |
| **DevOpsエンジニア** | ⭐⭐⭐⭐⭐ | サービスコンテナのカスタマイズ、OIDCクレーム強化、VNETフェイルオーバーで CI/CD の信頼性と柔軟性が大幅に向上 |
| **エンタープライズ管理者** | ⭐⭐⭐⭐⭐ | Security & qualityの統合ビュー、MCPガバナンス、カスタムインストラクションで組織統制が強化 |
| **.NET開発者** | ⭐⭐⭐⭐ | Visual StudioのCopilot拡張（カスタムエージェント、プロファイリング、脆弱性修正）で生産性が大幅に向上 |

---

## 🔮 What's Coming

今回のアップデートから読み取れる今後の展開：

- **GitHub Code Quality のGA** — Security & qualityタブの改称はその明確な前兆。コード品質チェックがセキュリティスキャンと同レベルでプラットフォームに統合される可能性が高い
- **Copilot SDKのGA化と拡張** — パブリックプレビューから本番対応へ。エコシステムの拡大に伴い、Copilot MarketplaceのようなエージェントやスキルのSharing Platform も視野に入る
- **セマンティック検索の他領域への拡張** — Issues検索の成功（精度75%）は、Pull Requests、Discussions、Codeへの展開を後押しする
- **MCP（Model Context Protocol）のエコシステム化** — Visual StudioでのMCPガバナンスサポートは、MCPがエンタープライズでの標準プロトコルとして定着しつつあることを示す

---

## 🔗 Sources

- [Copilot SDK in public preview](https://github.blog/changelog/2026-04-02-copilot-sdk-in-public-preview)
- [Copilot usage metrics now includes per-user GitHub Copilot CLI activity in organization reports](https://github.blog/changelog/2026-04-02-copilot-usage-metrics-now-includes-per-user-github-copilot-cli-activity-in-organization-reports)
- [GitHub Actions: Early April 2026 updates](https://github.blog/changelog/2026-04-02-github-actions-early-april-2026-updates)
- [GitHub Copilot in Visual Studio — March update](https://github.blog/changelog/2026-04-02-github-copilot-in-visual-studio-march-update)
- [The Security tab is now Security & quality](https://github.blog/changelog/2026-04-02-the-security-tab-is-now-security-quality)
- [Improved search for GitHub Issues is now generally available](https://github.blog/changelog/2026-04-02-improved-search-for-github-issues-is-now-generally-available)
- [Copilot organization custom instructions are generally available](https://github.blog/changelog/2026-04-02-copilot-organization-custom-instructions-are-generally-available)
