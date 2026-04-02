---
layout: post
title: "今週のマイクロソフト ホットトピック 🔥 / Microsoft Hot Topics This Week"
date: 2026-04-02 16:14:00 +0900
tags: [Copilot, Security, AI, GitHub, Supply Chain]
tone: "Casual / Newsletter"
persona: "Microsoft Specialist"
source_urls:
  - https://blogs.microsoft.com/blog/2026/03/31/open-to-work-how-to-get-ahead-in-the-age-of-ai/
  - https://github.blog/changelog/2026-04-01-research-plan-and-code-with-copilot-cloud-agent
  - https://github.blog/ai-and-ml/github-copilot/run-multiple-agents-at-once-with-fleet-in-copilot-cli/
  - https://github.blog/ai-and-ml/github-copilot/agent-driven-development-in-copilot-applied-science/
  - https://github.blog/security/supply-chain-security/securing-the-open-source-supply-chain-across-github/
  - https://www.microsoft.com/en-us/security/blog/2026/04/01/mitigating-the-axios-npm-supply-chain-compromise/
  - https://www.microsoft.com/en-us/security/blog/2026/03/31/applying-security-fundamentals-to-ai-practical-advice-for-cisos/
  - https://www.microsoft.com/en-us/security/blog/2026/03/30/addressing-the-owasp-top-10-risks-in-agentic-ai-with-microsoft-copilot-studio/
  - https://www.microsoft.com/en-us/security/blog/2026/03/31/whatsapp-malware-campaign-delivers-vbs-payloads-msi-backdoors/
  - https://github.blog/changelog/2026-04-01-gpt-5-4-mini-is-now-available-in-copilot-student-auto-model-selection
  - https://github.blog/changelog/2026-04-01-github-mobile-stay-in-flow-with-a-refreshed-copilot-tab-and-native-session-logs
  - https://github.blog/changelog/2026-03-31-upcoming-deprecation-of-claude-sonnet-4-in-github-copilot
  - https://github.blog/changelog/2026-04-01-codespaces-is-now-generally-available-for-github-enterprise-with-data-residency
  - https://blogs.microsoft.com/feed/
  - https://azure.microsoft.com/en-us/blog/feed/
  - https://devblogs.microsoft.com/feed/
  - https://github.blog/feed/
  - https://github.blog/changelog/feed/
  - https://www.microsoft.com/en-us/security/blog/feed/
  - https://news.microsoft.com/ja-jp/feed/
issue_number: 42
excerpt: "Copilot Cloud Agentの大幅アップデート、/fleetによるマルチエージェント並列実行、Axios npmサプライチェーン攻撃への対応など、今週のマイクロソフトのホットトピックを総まとめ。"
---

やぁ、みなさん！👋 今週もマイクロソフト界隈はアツいニュースが盛りだくさんでした。Copilotの進化からセキュリティの緊急事態まで、見逃せないトピックをまるっとお届けします！

Hey everyone! 👋 It's been another jam-packed week in the Microsoft universe — from massive Copilot upgrades to a critical security incident. Let's dive into the highlights!

---

## 📋 Overview / 概要

今週（2026年3月26日〜4月2日）は、GitHub Copilotのエージェント機能が大きく進化し、同時にAxiosのnpmサプライチェーン攻撃という重大なセキュリティインシデントが発生しました。Microsoftのセキュリティチームの迅速な対応が光った一週間です。

This week (March 26 – April 2, 2026), GitHub Copilot's agent capabilities took a huge leap forward, while a critical npm supply chain attack on Axios demanded immediate attention. Microsoft's security team delivered a swift, detailed response.

---

## 🔑 Key Highlights / 注目ポイント

### 1. 🚀 Copilot Cloud Agent — PR以外もOKになった！

**これ、めちゃくちゃ大きい変更です。** これまでCopilot Cloud Agent（旧 Copilot coding agent）はプルリクエストを作ることしかできませんでした。今回のアップデートで、以下が可能に：

- **PRなしでブランチ上で作業** — コードを書いてからPRを作るタイミングを自分で決められる
- **実装プランの生成** — コードを書く前にCopilotに計画を立てさせて、レビュー＆承認してから実装へ
- **コードベースの深い調査** — リポジトリ全体を対象にした質問に、しっかり根拠のある回答を返してくれる

Copilotが「コーディングマシン」から「開発パートナー」へと進化した瞬間ですね。

**This is a game-changing update.** Copilot cloud agent is no longer limited to pull-request workflows:

- **Work on a branch without opening a PR** — review the diff first, then decide when you're ready
- **Generate implementation plans** — ask Copilot to plan before coding, review and approve the approach
- **Deep research in your codebase** — get comprehensive, repository-grounded answers to broad questions

Copilot just evolved from a "coding machine" to a true "development partner."

> [Research, plan, and code with Copilot cloud agent](https://github.blog/changelog/2026-04-01-research-plan-and-code-with-copilot-cloud-agent)

---

### 2. ⚡ /fleet — 複数エージェントを同時に走らせろ！

Copilot CLIに `/fleet` コマンドが登場。一つのタスクを複数の独立したサブエージェントに分解して、**並列実行**できるようになりました。

仕組みはこんな感じ：
1. タスクを独立した作業単位に分解
2. 並列実行可能なものを識別
3. サブエージェントを同時にディスパッチ
4. 完了を監視して次のウェーブを投入
5. 最終成果物を統合

例えば「認証モジュールのリファクタ、テスト更新、ドキュメント修正」を一つのプロンプトで投げると、それぞれ別のエージェントが同時に作業してくれる。`.github/agents/` でカスタムエージェントを定義して、タスクごとに異なるモデルやツールを割り当てることも可能です。

The new `/fleet` slash command in Copilot CLI lets you dispatch **multiple subagents in parallel**. The orchestrator decomposes your task, identifies independent tracks, dispatches agents simultaneously, and synthesizes the final output. You can even reference custom agents defined in `.github/agents/` to use different models for different jobs. This is like having a whole dev team at your fingertips! 🤯

> [Run multiple agents at once with /fleet in Copilot CLI](https://github.blog/ai-and-ml/github-copilot/run-multiple-agents-at-once-with-fleet-in-copilot-cli/)

---

### 3. 🚨 Axios npm サプライチェーン攻撃 — 要対応！

**これは緊急です。** 週間7,000万ダウンロードを超える人気JavaScriptライブラリ「Axios」のバージョン **1.14.1** と **0.30.4** が北朝鮮の国家支援アクター **Sapphire Sleet** によって侵害されました。

攻撃の手口：
- `plain-crypto-js` という偽の依存パッケージを注入
- `npm install` 時に自動的にC2サーバーへ接続
- Windows / macOS / Linux すべてにOS別のRATを配信
- Windowsではレジストリに永続化メカニズムを仕込む

**やるべきこと：**
- Axios 1.14.1 または 0.30.4 を使っている場合、**今すぐ** 1.14.0 または 0.30.3 にダウングレード
- シークレットとクレデンシャルをローテーション
- Axiosの自動アップデートを無効化

Microsoft Defenderはすでに検知・保護を提供しており、GitHubのAdvisory Databaseにも掲載済みです。

**URGENT:** Axios versions **1.14.1** and **0.30.4** were compromised by **Sapphire Sleet**, a North Korean state actor. The malicious versions inject `plain-crypto-js` as a dependency that connects to a C2 server during `npm install`, deploying platform-specific RATs on Windows, macOS, and Linux. **Downgrade immediately** to 1.14.0 or 0.30.3 and rotate all credentials.

> [Mitigating the Axios npm supply chain compromise](https://www.microsoft.com/en-us/security/blog/2026/04/01/mitigating-the-axios-npm-supply-chain-compromise/)

---

## 🔍 Deep Dive / 深掘り

### エージェント駆動開発の実践 — Copilot Applied Scienceチームの事例

GitHubのCopilot Applied Scienceチームが、**コーディングエージェントを使ってエージェントを構築した**実体験を共有しています。これがなかなか面白い。

3日間で5人のメンバーが参加し、11個の新エージェント、4つの新スキル、ワークフロー機能を開発。コード変更量は **+28,858 / -2,884行**、345ファイルにわたります。

成功の鍵となった3つの原則：
- **プロンプト戦略**: エージェントをエンジニアのように扱い、計画モードを活用してから実装モードへ
- **アーキテクチャ戦略**: リファクタリング、ドキュメント更新、クリーンアップを頻繁に
- **イテレーション戦略**: 「信頼するが検証する」→「プロセスを責めろ、エージェントを責めるな」

GitHub's Copilot Applied Science team shared a fascinating case study of using coding agents to build agents. In just 3 days, 5 team members created 11 new agents, 4 new skills, and workflow features — totaling **+28,858/-2,884 lines** across 345 files. The key takeaway? Treat the agent like an engineer: be conversational, leverage planning mode, and keep your codebase well-maintained for agent-first development.

> [Agent-driven development in Copilot Applied Science](https://github.blog/ai-and-ml/github-copilot/agent-driven-development-in-copilot-applied-science/)

---

### オープンソースのサプライチェーンセキュリティ強化

GitHubが、最近のサプライチェーン攻撃パターンに対するセキュリティ強化策をまとめています。攻撃者はGitHub Actionsのワークフローを起点にシークレットを窃取し、悪意あるパッケージを公開するパターンが増えています。

**今すぐできる対策：**
- CodeQLでGitHub Actionsワークフローをスキャン（パブリックリポジトリは無料）
- `pull_request_target` でのワークフロートリガーを避ける
- サードパーティActionsをフルレングスのコミットSHAでピン留め
- Dependabotで悪意ある依存関係を検知

GitHub announced enhanced security measures against supply chain attacks. Key actions: enable CodeQL for Actions workflows (free on public repos), pin third-party Actions to full commit SHAs, and use Dependabot for malicious dependency detection. npm now processes trusted publishing across npm, PyPI, NuGet, RubyGems, and Crates.

> [Securing the open source supply chain across GitHub](https://github.blog/security/supply-chain-security/securing-the-open-source-supply-chain-across-github/)

---

### OWASP Top 10 for Agentic AI × Microsoft Copilot Studio

エージェンティックAIが本番環境に投入される中、OWASPが「Agentic Applications向けTop 10」を発表。Microsoftのセキュリティブログでは、これらのリスクに対するMicrosoft Copilot Studioでの実践的な緩和策を解説しています。

10のリスクには、エージェントの目標ハイジャック、ツールの悪用、アイデンティティの乱用、サプライチェーン脆弱性などが含まれます。MicrosoftのAI Red Teamメンバーもレビューボードに参加しています。

As agentic AI moves to production, OWASP published its Top 10 for Agentic Applications (2026), and Microsoft's security blog detailed practical mitigations using Copilot Studio and Agent 365. The 10 risks cover agent goal hijacking, tool misuse, identity abuse, supply chain vulnerabilities, and more. Members of Microsoft's AI Red Team served on the OWASP review board.

> [Addressing the OWASP Top 10 Risks in Agentic AI with Microsoft Copilot Studio](https://www.microsoft.com/en-us/security/blog/2026/03/30/addressing-the-owasp-top-10-risks-in-agentic-ai-with-microsoft-copilot-studio/)

---

### AI時代のセキュリティ — CISOへの実践アドバイス

Microsoftセキュリティブログから、CISOに向けた実践的なアドバイスが公開されました。キーメッセージは2つ：

1. **AIは魔法じゃない** — 非常に優秀だけど新人のように扱うのがベスト。明確で具体的な指示を出し、重要な操作の前にはチェックポイントを設ける。
2. **AIはソフトウェアである** — 従来のセキュリティプラクティス（最小権限、アクセス制御、Prompt Shield）がそのまま適用できる。

Microsoft published practical AI security advice for CISOs: (1) AI isn't magic — treat it like a smart but new team member, and (2) AI is software — apply the same security fundamentals you already know: least privilege, identity controls, and tools like Prompt Shield against indirect prompt injection.

> [Applying security fundamentals to AI: Practical advice for CISOs](https://www.microsoft.com/en-us/security/blog/2026/03/31/applying-security-fundamentals-to-ai-practical-advice-for-cisos/)

---

## 📰 その他のニュース / Quick Hits

- **📖 "Open to Work" 発売**: LinkedIn CEO Ryan Roslanskyの新著「Open to Work: How to Get Ahead in the Age of AI」が発売。AIと仕事の未来についての実践ガイド。 — [Blog Post](https://blogs.microsoft.com/blog/2026/03/31/open-to-work-how-to-get-ahead-in-the-age-of-ai/)

- **📱 GitHub Mobile アップデート**: Copilotタブのリフレッシュ、ネイティブセッションログ、Issueからのエージェント割り当てが改善。 — [Changelog](https://github.blog/changelog/2026-04-01-github-mobile-stay-in-flow-with-a-refreshed-copilot-tab-and-native-session-logs)

- **🤖 GPT-5.4 mini が学生向けに**: Copilot Studentのオートモデルセレクションに GPT-5.4 mini が追加。 — [Changelog](https://github.blog/changelog/2026-04-01-gpt-5-4-mini-is-now-available-in-copilot-student-auto-model-selection)

- **⚠️ Claude Sonnet 4 非推奨予告**: GitHub CopilotでのClaude Sonnet 4のサポートが非推奨に。ユーザーは新しいモデルへの移行を。 — [Changelog](https://github.blog/changelog/2026-03-31-upcoming-deprecation-of-claude-sonnet-4-in-github-copilot)

- **☁️ Codespaces がEnterprise Data Residencyで GA**: GitHub Enterprise向けCodespacesがデータレジデンシー対応で一般提供開始。 — [Changelog](https://github.blog/changelog/2026-04-01-codespaces-is-now-generally-available-for-github-enterprise-with-data-residency)

- **🦠 WhatsApp マルウェアキャンペーン**: VBScriptとMSIバックドアを配信するWhatsAppマルウェアキャンペーンが発見。Microsoft Defenderで検知可能。 — [Security Blog](https://www.microsoft.com/en-us/security/blog/2026/03/31/whatsapp-malware-campaign-delivers-vbs-payloads-msi-backdoors/)

---

## 💡 What This Means / 今週のまとめ

今週のニュースを俯瞰すると、Microsoftの戦略の2つの柱がくっきり見えてきます：

**1. AIエージェントの民主化** 🤖

Copilot Cloud Agentの拡張、/fleetコマンド、エージェント駆動開発の実践事例… これらは全て「AIエージェントを誰もが使いやすくする」というMicrosoftの方向性を示しています。もはやCopilotは単なるコード補完ツールではなく、計画・調査・実装・レビューまでカバーする開発パートナーです。

**2. AI時代のセキュリティリーダーシップ** 🛡️

AxiosのサプライチェーンアタックへのMicrosoft Threat Intelligenceの詳細な分析、OWASP Top 10 for Agentic AIへの貢献、CISOs向けのAIセキュリティガイダンス… Microsoftは「AIを推進する側」であると同時に「AIのリスクを管理する側」としてもリーダーシップを取ろうとしています。これは「Trust（信頼）」をAI時代の差別化要因にするというSatya Nadellaのビジョンそのものです。

**Looking at this week's news through the lens of Microsoft's strategy:**

1. **Democratizing AI agents** — Copilot Cloud Agent's expansion, `/fleet`, and agent-driven development practices all point to making AI agents accessible to every developer. Copilot is no longer just autocomplete; it's a full development partner that plans, researches, implements, and reviews.

2. **Security leadership in the AI era** — From the detailed Axios supply chain analysis to OWASP contributions and CISO guidance, Microsoft is positioning itself as both the enabler of AI and the guardian against AI-related risks. This is Satya Nadella's "Trust as a differentiator" vision in action.

来週も注目のニュースがあれば、またお届けします！Stay tuned! 🎯

---

## 🔗 Sources / ソース

- [Research, plan, and code with Copilot cloud agent](https://github.blog/changelog/2026-04-01-research-plan-and-code-with-copilot-cloud-agent)
- [Run multiple agents at once with /fleet in Copilot CLI](https://github.blog/ai-and-ml/github-copilot/run-multiple-agents-at-once-with-fleet-in-copilot-cli/)
- [Agent-driven development in Copilot Applied Science](https://github.blog/ai-and-ml/github-copilot/agent-driven-development-in-copilot-applied-science/)
- [Securing the open source supply chain across GitHub](https://github.blog/security/supply-chain-security/securing-the-open-source-supply-chain-across-github/)
- [Mitigating the Axios npm supply chain compromise](https://www.microsoft.com/en-us/security/blog/2026/04/01/mitigating-the-axios-npm-supply-chain-compromise/)
- [Applying security fundamentals to AI: Practical advice for CISOs](https://www.microsoft.com/en-us/security/blog/2026/03/31/applying-security-fundamentals-to-ai-practical-advice-for-cisos/)
- [Addressing the OWASP Top 10 Risks in Agentic AI](https://www.microsoft.com/en-us/security/blog/2026/03/30/addressing-the-owasp-top-10-risks-in-agentic-ai-with-microsoft-copilot-studio/)
- [WhatsApp malware campaign delivers VBScript and MSI backdoors](https://www.microsoft.com/en-us/security/blog/2026/03/31/whatsapp-malware-campaign-delivers-vbs-payloads-msi-backdoors/)
- [Open to Work: How to Get Ahead in the Age of AI](https://blogs.microsoft.com/blog/2026/03/31/open-to-work-how-to-get-ahead-in-the-age-of-ai/)
- [GPT-5.4 mini for Copilot Student](https://github.blog/changelog/2026-04-01-gpt-5-4-mini-is-now-available-in-copilot-student-auto-model-selection)
- [GitHub Mobile: Refreshed Copilot tab](https://github.blog/changelog/2026-04-01-github-mobile-stay-in-flow-with-a-refreshed-copilot-tab-and-native-session-logs)
- [Claude Sonnet 4 deprecation notice](https://github.blog/changelog/2026-03-31-upcoming-deprecation-of-claude-sonnet-4-in-github-copilot)
- [Codespaces GA for Enterprise data residency](https://github.blog/changelog/2026-04-01-codespaces-is-now-generally-available-for-github-enterprise-with-data-residency)
