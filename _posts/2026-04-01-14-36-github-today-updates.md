---
layout: post
title: "今日のGitHub最新情報まとめ / GitHub Updates Today"
date: 2026-04-01 14:36:00 +0900
tags: [GitHub, Copilot, Security, CodeQL, AI]
source_urls:
  - https://github.blog/feed/
  - https://github.blog/changelog/feed/
  - https://github.blog/ai-and-ml/github-copilot/agent-driven-development-in-copilot-applied-science/
  - https://github.blog/developer-skills/github/github-for-beginners-getting-started-with-github-security/
  - https://github.blog/changelog/2026-03-31-upcoming-deprecation-of-claude-sonnet-4-in-github-copilot
  - https://github.blog/changelog/2026-03-31-github-secret-scanning-nine-new-types-and-more
  - https://github.blog/changelog/2026-03-31-codeql-2-25-0-adds-swift-6-2-4-support
  - https://github.blog/changelog/2026-03-31-codeql-pull-requests-insights-on-security-overview-now-cover-all-protected-branches
  - https://github.blog/changelog/2026-03-31-eu-data-residency-region-expanding-to-include-efta-countries
  - https://github.blog/changelog/2026-03-30-create-issues-from-slack-with-copilot
issue_number: 19
excerpt: "2026年3月30日〜31日のGitHub Blog・Changelogを分析。Copilotエージェント駆動開発、セキュリティ強化、モデル更新など主要アップデートを日英バイリンガルで紹介。"
---

## Executive Summary

2026年3月30日〜31日にかけて、GitHub BlogおよびGitHub Changelogで多数の重要アップデートが発表されました。特に注目すべきは、Copilotのエージェント駆動開発に関する詳細な実践レポート、Claude Sonnet 4の廃止予告、Secret Scanningの9種の新パターン追加、CodeQL 2.25.0のリリースなどです。セキュリティ強化とAIエージェント活用の2つの大きな潮流が明確に見て取れます。

*Between March 30–31, 2026, GitHub Blog and GitHub Changelog published a series of significant updates. Key highlights include a detailed report on agent-driven development with Copilot, the upcoming deprecation of Claude Sonnet 4, nine new Secret Scanning detectors, and the CodeQL 2.25.0 release. Two major trends stand out: strengthened security tooling and accelerated AI agent adoption.*

---

## 1. エージェント駆動開発の実践 / Agent-Driven Development in Practice

**公開日:** 2026年3月31日  
**カテゴリ:** AI & ML, GitHub Copilot

GitHub Copilot Applied Scienceチームの研究者Tyler McGoffinが、コーディングエージェントを活用して自身の業務を自動化した実体験を詳細にレポートしています。

### 主なポイント / Key Points

- **きっかけ:** ベンチマーク評価のトラジェクトリ分析で毎回数十万行のJSONを読む必要があり、そのインテリジェントな作業をエージェントで自動化
- **開発環境:** Copilot CLI + Claude Opus 4.6 + VSCode + Copilot SDKで構築
- **3つの原則:**
  1. **プロンプト戦略** — エージェントをエンジニアのように扱い、会話的かつ詳細に指示。計画モード（`/plan`）を活用してから実装モードへ
  2. **アーキテクチャ戦略** — リファクタリング、ドキュメント更新、テスト追加を最優先に。エージェントがコードベースを理解しやすくなる
  3. **イテレーション戦略** — 「プロセスを責める、エージェントを責めない」思想。CI/CD、型チェック、リンター、統合テストでガードレールを構築
- **成果:** 5人の科学者が3日間で11の新エージェント、4つの新スキル、新概念を作成。**+28,858/-2,884行**（345ファイル）の変更を達成

> "The skills that make you a great engineer and a great teammate are the same skills that make you great at building with Copilot."

- [原文 / Original](https://github.blog/ai-and-ml/github-copilot/agent-driven-development-in-copilot-applied-science/)

---

## 2. GitHub Changelog 主要アップデート / Key Changelog Updates

### 2.1 Claude Sonnet 4 の廃止予告 / Claude Sonnet 4 Deprecation Notice

**公開日:** 2026年3月31日  
**カテゴリ:** Copilot

GitHub Copilotの全エクスペリエンス（Chat、インライン編集、Ask/Agentモード、コード補完）において、**Claude Sonnet 4が2026年5月1日に廃止**されます。推奨される代替モデルは**Claude Sonnet 4.6**です。

*Claude Sonnet 4 will be deprecated across all GitHub Copilot experiences on May 1, 2026. The recommended alternative is Claude Sonnet 4.6. Enterprise administrators should update model policies before this date.*

- [詳細 / Details](https://github.blog/changelog/2026-03-31-upcoming-deprecation-of-claude-sonnet-4-in-github-copilot)

### 2.2 Secret Scanning — 9つの新検出パターン追加 / Nine New Secret Detectors

**公開日:** 2026年3月31日  
**カテゴリ:** Application Security

Secret Scanningに7プロバイダーから9種類の新しいシークレット検出パターンが追加されました。

| プロバイダー / Provider | シークレットタイプ | Push Protection |
|---|---|---|
| Fieldguide | `fieldguide_api_token` | 設定可能 |
| Figma | `figma_scim_token` | ✓ デフォルト |
| Flickr | `flickr_api_key` | 設定可能 |
| Hack Club | `hackclub_ai_api_key` | 設定可能 |
| Langchain | `langsmith_license_key` | ✓ デフォルト |
| Langchain | `langsmith_scim_bearer_token` | ✓ デフォルト |
| PostHog | `posthog_oauth_access_token` | 設定可能 |
| PostHog | `posthog_oauth_refresh_token` | 設定可能 |
| Salesforce | `salesforce_marketing_cloud_api_oauth2_token` | ✓ デフォルト |

さらに、npmの`npm_access_token`に対するバリデーションチェックが追加され、Figma・Google・OpenVSX・PostHogのシークレットがPush Protectionのデフォルトに昇格しました。

*Nine new secret types from seven providers (including Langchain, Salesforce, and Figma) were added. Validity checks now support npm access tokens. Secrets from Figma, Google, OpenVSX, and PostHog are now push-protected by default.*

- [詳細 / Details](https://github.blog/changelog/2026-03-31-github-secret-scanning-nine-new-types-and-more)

### 2.3 CodeQL 2.25.0 — Swift 6.2.4対応 / CodeQL 2.25.0 with Swift 6.2.4 Support

**公開日:** 2026年3月31日  
**カテゴリ:** Application Security

CodeQL 2.25.0がリリースされ、以下の改善が含まれています：

- **Swift:** Swift 6.2.4のアプリ分析に対応
- **Java/Kotlin:** 制御フローグラフ（CFG）を完全書き直し。到達可能なノードのみを含めることで分析精度が向上
- **C#:** C# 14のpartialコンストラクタに対応。WebSocket接続からのリモートフローソースを追加
- **JavaScript/TypeScript:** ブラウザ固有のソースkind（`browser-url-query`、`browser-url-fragment`、`browser-message-event`）を追加

*CodeQL 2.25.0 adds Swift 6.2.4 support, rewrites the Java control flow graph for improved accuracy, adds C# 14 partial constructor support, and introduces browser-specific source kinds for JavaScript/TypeScript.*

- [詳細 / Details](https://github.blog/changelog/2026-03-31-codeql-2-25-0-adds-swift-6-2-4-support)

### 2.4 CodeQL PR Insights — 全保護ブランチに拡大 / CodeQL PR Insights for All Protected Branches

**公開日:** 2026年3月31日  
**カテゴリ:** Application Security

セキュリティオーバービューのCodeQL PRインサイトタブが、デフォルトブランチだけでなく**全保護ブランチ**のデータを集計するようになりました。Copilot Autofixの実際の効果をより正確に把握できます。

*The CodeQL pull request insights tab now aggregates data from all protected branches, not just the default branch, giving a more complete view of Copilot Autofix impact.*

- [詳細 / Details](https://github.blog/changelog/2026-03-31-codeql-pull-requests-insights-on-security-overview-now-cover-all-protected-branches)

### 2.5 EUデータレジデンシーがEFTA諸国に拡大 / EU Data Residency Expands to EFTA Countries

**公開日:** 2026年3月31日  
**カテゴリ:** Enterprise Management

2026年5月1日より、GitHub Enterprise Cloud（ghe.com）のEUデータレジデンシーリージョンが、EFTA加盟国（**ノルウェー**、**スイス**）のAzureインフラを含むよう拡大されます。MicrosoftのEU Data Boundaryと整合する形です。

*Starting May 1, 2026, GitHub Enterprise Cloud's EU data residency region will include Azure infrastructure in EFTA countries (Norway and Switzerland), aligning with Microsoft's EU Data Boundary.*

- [詳細 / Details](https://github.blog/changelog/2026-03-31-eu-data-residency-region-expanding-to-include-efta-countries)

### 2.6 SlackからCopilotでIssue作成 / Create Issues from Slack with Copilot

**公開日:** 2026年3月30日  
**カテゴリ:** Copilot, Projects & Issues

Slack上で`@GitHub`にメンションするだけで、自然言語でGitHub Issueを作成できるようになりました。サブIssueの階層的な作成やスレッドでの反復的な改善にも対応しています。

主な機能：
- 自然言語でのIssue作成（タイトル、本文、担当者、ラベル、マイルストーン自動設定）
- サブIssueの一括作成
- Slackスレッドでの会話モードによるIssue内容の精緻化
- チャンネルレベルでのデフォルトリポジトリ設定

*You can now create GitHub Issues directly from Slack using natural language with `@GitHub`. The app supports sub-issues, conversation mode for refinement, and channel-level default repository settings.*

- [詳細 / Details](https://github.blog/changelog/2026-03-30-create-issues-from-slack-with-copilot)

---

## 3. セキュリティ入門ガイド / Getting Started with GitHub Security

**公開日:** 2026年3月30日  
**カテゴリ:** Developer Skills

「GitHub for Beginners」シリーズのシーズン3第3弾として、GitHub Advanced Security（GHAS）の入門ガイドが公開されました。Secret Scanning、Dependabot、CodeQL Code Scanning、Copilot Autofixの有効化手順と活用方法をステップバイステップで解説しています。

*The "GitHub for Beginners" series published a comprehensive guide on getting started with GitHub Advanced Security, covering Secret Scanning, Dependabot, CodeQL, and Copilot Autofix with step-by-step instructions.*

- [原文 / Original](https://github.blog/developer-skills/github/github-for-beginners-getting-started-with-github-security/)

---

## Key Takeaways / まとめ

- **AIエージェント開発が本格化:** Copilot Applied Scienceチームの実践レポートは、エージェント駆動開発が研究フェーズを超え、実用的な開発手法として確立されつつあることを示している。「エージェントをジュニアエンジニアとして育てる」アプローチが具体的な成果を挙げている
- **セキュリティの多層強化:** Secret Scanning（+9パターン）、CodeQL 2.25.0（Swift/Java/C#/JS対応強化）、PR Insightsの全保護ブランチ対応と、セキュリティツールチェーン全体が一斉にアップデートされている
- **モデルの世代交代:** Claude Sonnet 4→4.6への移行予告は、GitHub CopilotのAIモデル更新サイクルの速さを示している。先日のGemini 3 Pro廃止と合わせ、最新モデルへの移行が重要
- **開発者体験の向上:** SlackからのIssue作成、EUデータレジデンシーの拡大など、企業ユーザーの利便性とコンプライアンス対応が着実に進んでいる
- **初心者への門戸拡大:** GHASの入門ガイドは、セキュリティ機能がパブリックリポジトリで無料利用可能であることを強調し、セキュリティの民主化を推進している

---

*AI agent-driven development is maturing into a practical methodology. Security tooling received comprehensive updates across Secret Scanning, CodeQL, and PR Insights. The Claude Sonnet 4 deprecation signals rapid AI model iteration. Developer experience continues to improve with Slack integration and EU data residency expansion. GitHub is simultaneously advancing its AI capabilities and security infrastructure while making both more accessible to all developers.*
