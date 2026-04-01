---
layout: post
title: "今日のマイクロソフト — ニュースまとめ（2026年4月2日）/ Today's Microsoft — News Roundup (April 2, 2026)"
date: 2026-04-02 07:07:00 +0900
tags: [Microsoft, GitHub, Copilot, AI, Security, Azure, Supply Chain]
tone: "Journalistic"
persona: "News Curator"
source_urls:
  - https://blogs.microsoft.com/feed/
  - https://blogs.microsoft.com/on-the-issues/feed/
  - https://github.blog/feed/
  - https://github.blog/changelog/feed/
  - https://devblogs.microsoft.com/feed/
  - https://azure.microsoft.com/en-us/blog/feed/
  - https://news.microsoft.com/ja-jp/
  - https://blogs.microsoft.com/blog/2026/03/31/open-to-work-how-to-get-ahead-in-the-age-of-ai/
  - https://blogs.microsoft.com/on-the-issues/2026/03/31/working-constructively-with-the-uk-cma-to-support-customer-choice-and-cloud-competition/
  - https://github.blog/security/supply-chain-security/securing-the-open-source-supply-chain-across-github/
  - https://github.blog/ai-and-ml/github-copilot/run-multiple-agents-at-once-with-fleet-in-copilot-cli/
  - https://github.blog/ai-and-ml/github-copilot/agent-driven-development-in-copilot-applied-science/
  - https://github.blog/changelog/2026-04-01-research-plan-and-code-with-copilot-cloud-agent
  - https://github.blog/changelog/2026-04-01-codespaces-is-now-generally-available-for-github-enterprise-with-data-residency
  - https://github.blog/changelog/2026-04-01-gpt-5-4-mini-is-now-available-in-copilot-student-auto-model-selection
  - https://github.blog/changelog/2026-04-01-github-mobile-stay-in-flow-with-a-refreshed-copilot-tab-and-native-session-logs
  - https://github.blog/changelog/2026-04-01-github-mobile-faster-more-flexible-agent-assignment-from-issues
  - https://github.blog/changelog/2026-03-31-upcoming-deprecation-of-claude-sonnet-4-in-github-copilot
  - https://github.blog/changelog/2026-03-31-dependabot-now-supports-xcode-projects-using-swiftpm-with-xcodeproj-manifests
  - https://github.blog/changelog/2026-03-31-github-secret-scanning-nine-new-types-and-more
  - https://github.blog/changelog/2026-03-31-codeql-2-25-0-adds-swift-6-2-4-support
  - https://github.blog/changelog/2026-03-31-codeql-pull-requests-insights-on-security-overview-now-cover-all-protected-branches
  - https://news.microsoft.com/source/asia/features/microsoft-ai-tour-tokyo-2026-main-blog/?lang=ja
issue_number: 37
excerpt: "2026年3月31日〜4月1日のMicrosoft・GitHub最新ニュースを一挙紹介。Copilot cloud agent拡張、/fleet並列エージェント、OSSサプライチェーン防御策、GitHub Mobileアップデート、Claude Sonnet 4廃止予告、セキュリティ強化など全15件超。"
---

## 📰 This Week's Headlines / 今日の注目ヘッドライン

1. **GitHub が Copilot cloud agent を大幅拡張** — PRワークフローに限らず、計画立案・リサーチにも活用可能に（4月1日）
2. **オープンソース・サプライチェーン防御の新施策** — GitHub が Actions・npm 向けのセキュリティ強化ロードマップを公開（4月1日）
3. **Copilot CLI に `/fleet` コマンド登場** — 複数エージェントの並列実行を実現（4月1日）

1. **GitHub expands Copilot cloud agent** — Now supports planning and deep research beyond PR workflows (April 1)
2. **Open source supply chain defense** — GitHub outlines new security roadmap for Actions and npm (April 1)
3. **`/fleet` command launches in Copilot CLI** — Enables parallel multi-agent execution (April 1)

---

## 🏢 Microsoft Updates / マイクロソフト関連

### [Open to Work: How to Get Ahead in the Age of AI](https://blogs.microsoft.com/blog/2026/03/31/open-to-work-how-to-get-ahead-in-the-age-of-ai/) — 2026年3月31日

LinkedIn CEO の Ryan Roslansky が、Aneesh Raman との共著書「Open to Work」の発売を発表した。AI 時代のキャリア戦略を LinkedInグローバル労働市場データに基づいて解説する実践ガイドで、Microsoft 社長 Brad Smith との対談ポッドキャストも公開されている。

LinkedIn CEO Ryan Roslansky announced the publication of "Open to Work: How to Get Ahead in the Age of AI," co-authored with Aneesh Raman. The practical guide draws on LinkedIn's global labor market data to help professionals navigate AI-driven career shifts. A companion podcast conversation with Microsoft President Brad Smith is also available.

### [Working constructively with the UK CMA to support customer choice and cloud competition](https://blogs.microsoft.com/on-the-issues/2026/03/31/working-constructively-with-the-uk-cma-to-support-customer-choice-and-cloud-competition/) — 2026年3月31日

Microsoft は英国競争・市場庁（CMA）のクラウド市場調査に対応し、Azure のデータ移行（egress）、スイッチング、相互運用性に関する変更を発表した。英国の顧客がクラウドプロバイダーを柔軟に選択できるよう、迅速に実施するとしている。

Microsoft announced changes to its Azure cloud services in the United Kingdom, addressing data egress, switching, and interoperability issues raised by the Competition and Markets Authority (CMA). The company committed to implementing the changes promptly and sharing the approach with regulators worldwide.

---

## 🐙 GitHub Blog / GitHub ブログ

### [Securing the open source supply chain across GitHub](https://github.blog/security/supply-chain-security/securing-the-open-source-supply-chain-across-github/) — 2026年4月1日

GitHub はオープンソースのサプライチェーン攻撃への対策を包括的にまとめた記事を公開した。攻撃者が GitHub Actions のワークフロー経由でシークレットを窃取するパターンが増加しており、CodeQL による Actions ワークフローレビューの有効化が最も重要な対策として挙げられている。npm では毎日3万以上のパッケージが公開され、各バージョンがマルウェアスキャンされている。Trusted publishing の導入もnpm, PyPI, NuGet, RubyGems, Cratesなど主要リポジトリに拡大済み。

GitHub published a comprehensive overview of open source supply chain attack prevention. The new attack pattern focuses on exfiltrating secrets via GitHub Actions workflows. GitHub recommends enabling CodeQL for Actions workflow review as the top priority. npm scans all 30,000+ daily package publishes for malware, and trusted publishing now spans npm, PyPI, NuGet, RubyGems, and Crates. An updated Actions security roadmap is forthcoming.

### [Run multiple agents at once with /fleet in Copilot CLI](https://github.blog/ai-and-ml/github-copilot/run-multiple-agents-at-once-with-fleet-in-copilot-cli/) — 2026年4月1日

Copilot CLI に新スラッシュコマンド `/fleet` が登場。タスクを独立したワークアイテムに分解し、複数のサブエージェントを並列で起動してコードベースの異なる部分を同時に作業できる。各サブエージェントは独自のコンテキストウィンドウを持ちつつファイルシステムを共有する。カスタムエージェントの指定や依存関係の宣言にも対応している。

The new `/fleet` slash command in Copilot CLI enables parallel multi-agent execution. An orchestrator decomposes tasks into independent work items and dispatches multiple sub-agents simultaneously. Each sub-agent has its own context window but shares the filesystem. Users can define dependencies between tasks, set file boundaries, and reference custom agents for specialized work.

### [Agent-driven development in Copilot Applied Science](https://github.blog/ai-and-ml/github-copilot/agent-driven-development-in-copilot-applied-science/) — 2026年3月31日

GitHub の Copilot Applied Science チームの AI 研究者が、コーディングエージェントを使ってエージェントを構築し、自身の業務（ベンチマーク分析）を自動化した事例を紹介。Copilot CLI + Claude Opus 4.6 + VSCode の構成で、数十万行に及ぶベンチマーク軌跡データの分析を自動化した。Copilot SDK の活用やプロンプト設計のベストプラクティスも共有されている。

A researcher on GitHub's Copilot Applied Science team shared how they used coding agents to build agents that automated benchmark trajectory analysis—reducing hundreds of thousands of lines of code to review. The setup used Copilot CLI with Claude Opus 4.6 and VSCode. Key takeaways include leveraging the Copilot SDK, writing conversational prompts, and using planning modes before agent modes.

---

## 📋 GitHub Changelog / GitHub 変更履歴（4月1日）

### [Research, plan, and code with Copilot cloud agent](https://github.blog/changelog/2026-04-01-research-plan-and-code-with-copilot-cloud-agent) — 2026年4月1日

Copilot cloud agent（旧 Copilot coding agent）が PR ワークフロー以外にも拡張された。PR を作成せずにブランチ上でコード生成が可能になり、実装計画の生成やコードベースの深いリサーチにも対応。全有料 Copilot プランで利用可能。

Copilot cloud agent (formerly Copilot coding agent) now supports workflows beyond pull requests. Users can generate code on a branch without creating a PR, produce implementation plans for review before coding, and conduct deep research sessions grounded in repository context. Available on all paid Copilot plans.

### [Codespaces is now GA for GitHub Enterprise with data residency](https://github.blog/changelog/2026-04-01-codespaces-is-now-generally-available-for-github-enterprise-with-data-residency) — 2026年4月1日

GitHub Codespaces が GitHub Enterprise Cloud のデータレジデンシー対応として一般提供開始。オーストラリア、EU、日本、米国の全リージョンで利用可能。一般プラットフォーム版と同等の機能を提供する。

GitHub Codespaces is now generally available for GitHub Enterprise Cloud with data residency, covering Australia, EU, Japan, and US regions with full feature parity.

### [GPT-5.4 mini is now available in Copilot Student auto model selection](https://github.blog/changelog/2026-04-01-gpt-5-4-mini-is-now-available-in-copilot-student-auto-model-selection) — 2026年4月1日

GPT-5.4 mini が Copilot Student プランの自動モデル選択で一般利用可能になった。VS Code および github.com の Copilot Chat で利用できる。

GPT-5.4 mini is now generally available to Copilot Student plan users via auto model selection in VS Code and on github.com.

### [GitHub Mobile: Refreshed Copilot tab and native session logs](https://github.blog/changelog/2026-04-01-github-mobile-stay-in-flow-with-a-refreshed-copilot-tab-and-native-session-logs) — 2026年4月1日

GitHub Mobile がエージェントワークフロー管理を強化。Android ではナビゲーションバーに Copilot タブが追加され、セッションログのネイティブ表示、セッション停止、PR 作成・レビューがアプリ内で完結する。iOS / Android 両対応。

GitHub Mobile now features a refreshed Copilot tab (moved to the navigation bar on Android), native session log viewing, in-app PR creation from completed sessions, and the ability to stop running sessions. Available on both iOS and Android.

### [GitHub Mobile: Faster, more flexible agent assignment from issues](https://github.blog/changelog/2026-04-01-github-mobile-faster-more-flexible-agent-assignment-from-issues) — 2026年4月1日

GitHub Mobile の Issue オーバーフローメニューに「Assign an Agent」オプションが追加された。カスタム指示や別リポジトリの指定が可能で、Issue 作成時にも同様の操作ができる。

GitHub Mobile adds a new "Assign an Agent" option in the issue overflow menu, with support for custom instructions and cross-repository assignment. The same options are available during new issue creation.

---

## 📋 GitHub Changelog / GitHub 変更履歴（3月31日）

### [Upcoming deprecation of Claude Sonnet 4 in GitHub Copilot](https://github.blog/changelog/2026-03-31-upcoming-deprecation-of-claude-sonnet-4-in-github-copilot) — 2026年3月31日

Claude Sonnet 4 が 2026年5月1日に GitHub Copilot の全エクスペリエンスから廃止される。推奨代替モデルは Claude Sonnet 4.6。Enterprise 管理者はモデルポリシーの確認が必要。

Claude Sonnet 4 will be deprecated from all GitHub Copilot experiences on May 1, 2026. The suggested alternative is Claude Sonnet 4.6. Enterprise administrators should verify model policy settings and enable access to alternative models.

### [Dependabot now supports Xcode projects using SwiftPM with .xcodeproj manifests](https://github.blog/changelog/2026-03-31-dependabot-now-supports-xcode-projects-using-swiftpm-with-xcodeproj-manifests) — 2026年3月31日

Dependabot が `.xcodeproj` バンドル内の Swift パッケージ依存関係を検出・更新可能に。`Package.swift` ファイルがなくても動作し、Apple 開発者コミュニティへの自動依存関係更新が拡大した。

Dependabot can now detect and update Swift package dependencies in Xcode projects that manage packages through `.xcodeproj` bundles, even without a `Package.swift` file. This was one of the most requested enhancements for Swift ecosystem support.

### [GitHub secret scanning — nine new types and more](https://github.blog/changelog/2026-03-31-github-secret-scanning-nine-new-types-and-more) — 2026年3月31日

GitHub のシークレットスキャンに9種類の新しいシークレットタイプ（Langchain、Salesforce、Figma 等7プロバイダー）が追加された。Figma、Google、OpenVSX、PostHog のシークレットがプッシュ保護のデフォルト対象に。npm アクセストークンの有効性チェックにも新規対応。

GitHub secret scanning added nine new secret types from seven providers (Langchain, Salesforce, Figma, and more). Figma, Google, OpenVSX, and PostHog secrets are now push-protected by default. Validity checks are now available for npm access tokens.

### [CodeQL 2.25.0 adds Swift 6.2.4 support](https://github.blog/changelog/2026-03-31-codeql-2-25-0-adds-swift-6-2-4-support) — 2026年3月31日

CodeQL 2.25.0 がリリースされ、Swift 6.2.4 の解析に対応。Java の制御フローグラフが全面的に書き直されて精度が向上。C# 14 のパーシャルコンストラクタや、JavaScript のブラウザ固有ソースにも対応。

CodeQL 2.25.0 adds Swift 6.2.4 analysis, a rewritten Java control flow graph for improved accuracy, C# 14 partial constructor support, and browser-specific source kinds for JavaScript/TypeScript.

### [CodeQL PR insights on security overview now cover all protected branches](https://github.blog/changelog/2026-03-31-codeql-pull-requests-insights-on-security-overview-now-cover-all-protected-branches) — 2026年3月31日

セキュリティ概要の CodeQL PR インサイトが、デフォルトブランチだけでなく全保護ブランチのデータを集計するようになった。Copilot Autofix の効果をより正確に把握可能。

CodeQL pull request insights on the security overview now aggregate Copilot Autofix and alert statistics from all protected branches, not just the default branch.

---

## 🇯🇵 Microsoft News Japan / マイクロソフト日本ニュース

### [AI が変革するビジネスの現在地から未来へ — Microsoft AI Tour Tokyo 開催](https://news.microsoft.com/source/asia/features/microsoft-ai-tour-tokyo-2026-main-blog/?lang=ja) — 2026年3月

東京ビッグサイトで Microsoft AI Tour が開催され、数千人の経営者・開発者が参加した。日経225企業における Microsoft 365 Copilot の導入率が94%超に到達したことが発表された。Fortune 500 企業の90%が Copilot を利用し、有償シート数は前年同期比160%超の成長を記録。また、Microsoft 365 E7（Frontier Suite）、Agent 365（5月1日GA）、Copilot Cowork など新サービスが紹介された。セブン-イレブン・ジャパン、りそなホールディングス、富士通、花王、ソニー等の国内事例も共有された。

Microsoft AI Tour was held at Tokyo Big Sight, attracting thousands of executives and developers. The company announced that Microsoft 365 Copilot adoption among Nikkei 225 companies has surpassed 94%. Globally, 90% of Fortune 500 companies use Copilot, with paid seats growing over 160% year-over-year. New offerings including Microsoft 365 E7 (Frontier Suite), Agent 365 (GA May 1), and Copilot Cowork were showcased, alongside case studies from Seven-Eleven Japan, Resona Holdings, Fujitsu, Kao, Sony, and other Japanese enterprises.

---

## 📊 By the Numbers / 数字で見る

- **15件** — 3月31日〜4月1日に公開された Microsoft・GitHub 関連の記事・アップデート数 / articles and updates published March 31–April 1
- **9種類** — GitHub secret scanning に追加された新シークレットタイプ / new secret types added to GitHub secret scanning
- **94%超** — 日経225企業の Microsoft 365 Copilot 導入率 / Nikkei 225 companies using Microsoft 365 Copilot
- **160%超** — Copilot 有償シート数の前年同期比成長率 / year-over-year growth in paid Copilot seats
- **30,000+** — npm で毎日公開されるパッケージ数（すべてマルウェアスキャン対象）/ daily npm package publishes, all scanned for malware
- **5件** — 4月1日の GitHub Changelog 更新件数 / GitHub Changelog updates on April 1
- **4リージョン** — Codespaces データレジデンシー対応地域（豪州、EU、日本、米国）/ Codespaces data residency regions

---

## 🔗 Full Article Links / 全記事リンク一覧

1. [Open to Work: How to Get Ahead in the Age of AI](https://blogs.microsoft.com/blog/2026/03/31/open-to-work-how-to-get-ahead-in-the-age-of-ai/) — Microsoft Blog, Mar 31
2. [Working constructively with the UK CMA](https://blogs.microsoft.com/on-the-issues/2026/03/31/working-constructively-with-the-uk-cma-to-support-customer-choice-and-cloud-competition/) — On the Issues, Mar 31
3. [Securing the open source supply chain across GitHub](https://github.blog/security/supply-chain-security/securing-the-open-source-supply-chain-across-github/) — GitHub Blog, Apr 1
4. [Run multiple agents at once with /fleet in Copilot CLI](https://github.blog/ai-and-ml/github-copilot/run-multiple-agents-at-once-with-fleet-in-copilot-cli/) — GitHub Blog, Apr 1
5. [Agent-driven development in Copilot Applied Science](https://github.blog/ai-and-ml/github-copilot/agent-driven-development-in-copilot-applied-science/) — GitHub Blog, Mar 31
6. [Research, plan, and code with Copilot cloud agent](https://github.blog/changelog/2026-04-01-research-plan-and-code-with-copilot-cloud-agent) — GitHub Changelog, Apr 1
7. [Codespaces is now GA for GitHub Enterprise with data residency](https://github.blog/changelog/2026-04-01-codespaces-is-now-generally-available-for-github-enterprise-with-data-residency) — GitHub Changelog, Apr 1
8. [GPT-5.4 mini in Copilot Student auto model selection](https://github.blog/changelog/2026-04-01-gpt-5-4-mini-is-now-available-in-copilot-student-auto-model-selection) — GitHub Changelog, Apr 1
9. [GitHub Mobile: Refreshed Copilot tab and native session logs](https://github.blog/changelog/2026-04-01-github-mobile-stay-in-flow-with-a-refreshed-copilot-tab-and-native-session-logs) — GitHub Changelog, Apr 1
10. [GitHub Mobile: Faster, more flexible agent assignment from issues](https://github.blog/changelog/2026-04-01-github-mobile-faster-more-flexible-agent-assignment-from-issues) — GitHub Changelog, Apr 1
11. [Upcoming deprecation of Claude Sonnet 4](https://github.blog/changelog/2026-03-31-upcoming-deprecation-of-claude-sonnet-4-in-github-copilot) — GitHub Changelog, Mar 31
12. [Dependabot supports Xcode SwiftPM projects](https://github.blog/changelog/2026-03-31-dependabot-now-supports-xcode-projects-using-swiftpm-with-xcodeproj-manifests) — GitHub Changelog, Mar 31
13. [GitHub secret scanning — nine new types](https://github.blog/changelog/2026-03-31-github-secret-scanning-nine-new-types-and-more) — GitHub Changelog, Mar 31
14. [CodeQL 2.25.0 adds Swift 6.2.4 support](https://github.blog/changelog/2026-03-31-codeql-2-25-0-adds-swift-6-2-4-support) — GitHub Changelog, Mar 31
15. [CodeQL PR insights cover all protected branches](https://github.blog/changelog/2026-03-31-codeql-pull-requests-insights-on-security-overview-now-cover-all-protected-branches) — GitHub Changelog, Mar 31
16. [Microsoft AI Tour Tokyo 2026](https://news.microsoft.com/source/asia/features/microsoft-ai-tour-tokyo-2026-main-blog/?lang=ja) — Microsoft News Japan, Mar 2026
