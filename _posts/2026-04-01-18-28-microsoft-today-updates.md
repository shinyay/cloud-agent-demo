---
layout: post
title: "本日のマイクロソフト関連アップデートまとめ（2026年4月1日）"
date: 2026-04-01 18:28:00 +0900
tags: [Microsoft, GitHub, Copilot, AI, Security, Azure]
tone: "Executive Briefing"
source_urls:
  - https://blogs.microsoft.com/feed/
  - https://blogs.microsoft.com/on-the-issues/feed/
  - https://github.blog/feed/
  - https://github.blog/changelog/feed/
  - https://devblogs.microsoft.com/feed/
  - https://azure.microsoft.com/en-us/blog/feed/
  - https://blogs.microsoft.com/blog/2026/03/31/open-to-work-how-to-get-ahead-in-the-age-of-ai/
  - https://blogs.microsoft.com/on-the-issues/2026/03/31/working-constructively-with-the-uk-cma-to-support-customer-choice-and-cloud-competition/
  - https://github.blog/ai-and-ml/github-copilot/agent-driven-development-in-copilot-applied-science/
  - https://github.blog/changelog/2026-03-31-upcoming-deprecation-of-claude-sonnet-4-in-github-copilot
  - https://github.blog/changelog/2026-03-31-github-secret-scanning-nine-new-types-and-more
  - https://github.blog/changelog/2026-03-31-codeql-2-25-0-adds-swift-6-2-4-support
  - https://github.blog/changelog/2026-03-31-codeql-pull-requests-insights-on-security-overview-now-cover-all-protected-branches
  - https://github.blog/changelog/2026-03-31-eu-data-residency-region-expanding-to-include-efta-countries
issue_number: 23
excerpt: "2026年4月1日時点のMicrosoft・GitHub関連の最新アップデートをまとめ。AI時代のキャリア本、英国CMA対応、エージェント駆動開発、Claude Sonnet 4廃止、セキュリティ強化、EUデータレジデンシー拡大など。"
---

## Executive Summary

本日（2026年3月31日〜4月1日）、マイクロソフトおよびGitHubから複数の重要アップデートが公開された。Microsoft公式ブログではAI時代のキャリアガイド本の発売と英国クラウド市場規制への対応を発表。GitHub側ではエージェント駆動開発の実践レポート、Claude Sonnet 4の廃止予告、セキュリティツールの大幅強化、EUデータレジデンシーのEFTA拡大と、幅広い分野での動きがあった。

---

## Microsoft公式ブログ：AI時代のキャリアガイド「Open to Work」発売

**公開日:** 2026年3月31日

LinkedIn CEOのRyan Roslanskyが、Aneesh Ramanとの共著「**Open to Work: How to Get Ahead in the Age of AI**」の発売を発表した。

- AIに「使われる」のではなく「使いこなす」ための実践ガイド
- LinkedInのグローバル労働市場データに基づく具体的アドバイスを収録
- Microsoft社長Brad Smithとの対談がTools and Weaponsポッドキャストで公開中

> "We've always believed technology should serve people. AI should help humans. Not the other way around."

**影響:** AI時代におけるキャリア戦略の指針となる一冊。Microsoft/LinkedInとしてのAI活用ビジョンを示す重要な発信。

- [原文記事](https://blogs.microsoft.com/blog/2026/03/31/open-to-work-how-to-get-ahead-in-the-age-of-ai/)

---

## On the Issues：英国CMAクラウド市場規制への対応

**公開日:** 2026年3月31日

英国の競争・市場庁（CMA）が2025年7月に発表したクラウド市場調査報告書の指摘を受け、MicrosoftがAzureの英国顧客向けに具体的な変更を実施。

**主な変更点:**
- **データエグレスの軽減** — 他クラウドへの移行コスト削減
- **スイッチングの簡素化** — クラウド間切り替えの摩擦低減
- **相互運用性の強化** — マルチクラウド環境の改善

**注目点:** Microsoftは、本調査の申立人であるGoogleが2025年後半にAmazon・Microsoftより速い成長率を記録している点に言及。規制当局への積極的な対応姿勢を示しつつ、市場の競争性を強調した。

- [原文記事](https://blogs.microsoft.com/on-the-issues/2026/03/31/working-constructively-with-the-uk-cma-to-support-customer-choice-and-cloud-competition/)

---

## GitHub Blog：エージェント駆動開発の実践レポート

**公開日:** 2026年3月31日

GitHub Copilot Applied ScienceチームのTyler McGoffinが、コーディングエージェントを使ってエージェントを構築した実践的なレポートを公開。

**3つの核心原則:**

1. **プロンプト戦略** — エージェントをジュニアエンジニアのように扱い、会話的・詳細な指示を出す。`/plan`モードで計画してからコードに入ることが鉄則
2. **アーキテクチャ戦略** — リファクタリング、テスト、ドキュメントを最優先。エージェントが理解しやすいコードベースの維持が最速の開発手法
3. **イテレーション戦略** — 「エージェントを責めるな、プロセスを責めろ」。CI/CD、型チェック、リンターでガードレールを構築

**定量的成果:** 5人の科学者が3日間で、11の新エージェント・4つの新スキルを構築。**+28,858/-2,884行**（345ファイル）の変更を実現。

**示唆:** 良いエンジニアのスキルがそのまま良いAI活用のスキルになることを実データで実証。

- [原文記事](https://github.blog/ai-and-ml/github-copilot/agent-driven-development-in-copilot-applied-science/)

---

## GitHub Changelog：Claude Sonnet 4の廃止予告

**公開日:** 2026年4月1日

**Claude Sonnet 4が2026年5月1日に全GitHub Copilotエクスペリエンスから廃止**される。

- **対象:** Copilot Chat、インライン編集、Ask/Agentモード、コード補完のすべて
- **推奨代替:** Claude Sonnet 4.6
- **アクション:** Enterprise管理者はモデルポリシーの更新が必要

先日のGemini 3 Pro廃止（3月26日）に続く動き。AIモデルの入れ替わりペースが加速している。

- [詳細](https://github.blog/changelog/2026-03-31-upcoming-deprecation-of-claude-sonnet-4-in-github-copilot)

---

## GitHub Changelog：セキュリティツール大幅強化

**公開日:** 2026年3月31日

### Secret Scanning — 9つの新パターン追加

7プロバイダーから9種類の新検出パターンを追加。Figma、Langchain、Salesforce、PostHogなど幅広いカバレッジ。npmアクセストークンのバリデーションチェックも新規対応。Figma、Google、OpenVSX、PostHogのシークレットはデフォルトでプッシュ保護対象に。

- [詳細](https://github.blog/changelog/2026-03-31-github-secret-scanning-nine-new-types-and-more)

### CodeQL 2.25.0リリース

- **Swift 6.2.4対応**
- **Java/Kotlinの制御フローグラフ完全書き直し** — 解析精度向上
- **C# 14** partialコンストラクタ対応、WebSocket接続からのリモートフローソース追加
- **JavaScript/TypeScript** ブラウザ固有ソースkind（`browser-url-query`等）追加

- [詳細](https://github.blog/changelog/2026-03-31-codeql-2-25-0-adds-swift-6-2-4-support)

### CodeQL PRインサイト — 全保護ブランチ対応

セキュリティオーバービューのPRインサイトが、デフォルトブランチだけでなく全保護ブランチのデータを集計するように変更。Copilot Autofixの効果がより正確に可視化される。

- [詳細](https://github.blog/changelog/2026-03-31-codeql-pull-requests-insights-on-security-overview-now-cover-all-protected-branches)

---

## GitHub Changelog：EUデータレジデンシーのEFTA拡大

**公開日:** 2026年3月31日

2026年5月1日より、GitHub Enterprise Cloud（ghe.com）のEUデータレジデンシーリージョンがEFTA諸国（**ノルウェー**、**スイス**）に拡大される。

- MicrosoftのEU Data Boundaryに準拠した変更
- 既存のコンプライアンス認証（ISO 27001、SOC 2）、セキュリティ制御、暗号化はすべて維持
- 顧客側のアクションは不要（EU加盟国内限定を求める場合は5月1日までにGitHubへ連絡）

- [詳細](https://github.blog/changelog/2026-03-31-eu-data-residency-region-expanding-to-include-efta-countries)

---

## Key Takeaways

- **AI時代のキャリア:** LinkedIn CEO共著の「Open to Work」が発売。AIを使いこなす側に立つための実践的ガイド
- **クラウド規制対応:** Microsoftが英国CMAの指摘にデータエグレス・スイッチング・相互運用性の改善で積極対応
- **エージェント駆動開発が実用段階:** GitHubの実践レポートで、3日間で+28K行の成果を実証。「良いエンジニア＝良いAI活用者」
- **モデル入替の加速:** Claude Sonnet 4が5月1日廃止。Gemini 3 Proに続き、最新モデルへの追従が必須
- **セキュリティ基盤強化:** Secret Scanning、CodeQL 2.25.0、PRインサイトと多面的にアップデート
- **データレジデンシー拡大:** GitHubのEUリージョンがEFTA諸国（ノルウェー・スイス）に拡大、5月1日施行
