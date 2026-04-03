# 🚀 Setup Guide / セットアップガイド

> **This guide walks you through setting up your own ⚡ Copilot Pulse intelligence dashboard — a website that uses GitHub's AI agent to automatically research and publish curated reports on Microsoft and GitHub news.**
>
> **このガイドでは、⚡ Copilot Pulse インテリジェンスダッシュボードのセットアップ手順を説明します。GitHubのAIエージェントが自動的にMicrosoftやGitHubのニュースを調査し、キュレーションされたレポートを公開するウェブサイトです。**

---

## 💡 What is Copilot Pulse? / Copilot Pulseとは？

**Copilot Pulse** is a ready-made intelligence dashboard that automatically publishes news and analysis reports. Here's how it works — no technical knowledge required to understand this:

1. **You ask** — Create a GitHub Issue describing a topic (e.g., "This week's Azure announcements")
2. **AI researches** — GitHub's AI agent (Copilot Cloud Agent) reads the issue, visits real websites, and gathers information
3. **Reports appear** — Within a few minutes, a report is published on your dashboard website

**Copilot Pulse** は、ニュースや分析レポートを自動的に公開するインテリジェンスダッシュボードです。仕組みは次の通りです：

1. **リクエスト** — GitHub Issueでトピックを記述（例：「今週のAzureの発表内容」）
2. **AIが調査** — GitHubのAIエージェント（Copilot Cloud Agent）がIssueを読み取り、実際のウェブサイトを参照して情報を収集
3. **レポート公開** — 数分でダッシュボードにレポートが公開

---

## ⏱️ Setup Time & What You Need / セットアップ時間と必要なもの

| Item / 項目 | Detail / 詳細 |
|---|---|
| ⏱️ **Total time** / 合計時間 | About 20-30 minutes / 約20〜30分 |
| 🖥️ **What you use** / 使うもの | GitHub website (no coding required) / GitHubウェブサイト（コーディング不要） |
| 📋 **Steps** / ステップ数 | 6 steps / 6ステップ |

**What you'll need / 必要なもの:**
- A GitHub account (free) — [github.com](https://github.com)
- A **GitHub Copilot subscription** that includes Copilot Cloud Agent access
  - Individual, Business, or Enterprise plan
  - Not sure? Check [github.com/settings/copilot](https://github.com/settings/copilot)

**GitHubアカウント**（無料）— [github.com](https://github.com)  
**GitHub Copilotサブスクリプション**（Copilot Cloud Agentが含まれるプラン）  
- Individual、Business、またはEnterpriseプラン  
- 不明な場合は [github.com/settings/copilot](https://github.com/settings/copilot) を確認してください

---

## 📋 Table of Contents / 目次

1. [Prerequisites / 前提条件](#-prerequisites--前提条件)
2. [Step 1: Create Repository from Template / テンプレートからリポジトリを作成](#-step-1-create-repository-from-template--テンプレートからリポジトリを作成)
3. [Step 2: Enable GitHub Pages / GitHub Pages を有効化](#-step-2-enable-github-pages--github-pages-を有効化)
4. [Step 3: Enable Copilot Cloud Agent / Copilot Cloud Agent を有効化](#-step-3-enable-copilot-cloud-agent--copilot-cloud-agent-を有効化)
5. [Step 4: Configure Firewall Allowlist / ファイアウォール許可リストを設定](#-step-4-configure-firewall-allowlist--ファイアウォール許可リストを設定)
6. [Step 5: Run Automated Setup / 自動セットアップを実行](#-step-5-run-automated-setup--自動セットアップを実行)
7. [Step 6: Verify Your Dashboard / ダッシュボードを確認](#-step-6-verify-your-dashboard--ダッシュボードを確認)
8. [Appendix: Manual Setup (Advanced) / 付録：手動セットアップ（上級者向け）](#-appendix-manual-setup-advanced--付録手動セットアップ上級者向け)
9. [Troubleshooting / トラブルシューティング](#-troubleshooting--トラブルシューティング)

---

## ✅ Prerequisites / 前提条件

Before you begin, make sure you have the following:

セットアップを始める前に、以下を確認してください：

| Requirement / 要件 | Description / 説明 |
|---|---|
| **GitHub Account** | A GitHub account (free or paid) — [Sign up at github.com](https://github.com/signup)<br>GitHubアカウント（無料または有料）— [github.comでサインアップ](https://github.com/signup) |
| **GitHub Copilot Subscription** | Required for the AI agent to work. Individual, Business, or Enterprise plan.<br>AIエージェントを動作させるために必要。Individual、Business、またはEnterpriseプランが必要です。 |
| **Copilot Cloud Agent Access** | Must be available on your account/organization. Check at [github.com/settings/copilot](https://github.com/settings/copilot)<br>アカウントまたは組織で利用可能であること。[github.com/settings/copilot](https://github.com/settings/copilot) で確認できます。 |

> **📢 What's NOT copied from the template / テンプレートからコピーされないもの:**
>
> When you create a repository from a template, all **files** are copied, but the following **settings** are NOT carried over. You must configure them manually (Steps 2–4):
>
> テンプレートからリポジトリを作成すると、すべての**ファイル**はコピーされますが、以下の**設定**は引き継がれません。手動で設定する必要があります（Step 2〜4）：
>
> | Setting / 設定 | Copied? / コピー？ | Action / 対応 |
> |---|---|---|
> | Files & workflows / ファイルとワークフロー | ✅ Yes | — |
> | GitHub Pages settings / GitHub Pages設定 | ❌ No | Step 2 |
> | Copilot Cloud Agent / Copilot Cloud Agent | ❌ No | Step 3 |
> | Firewall allowlist / ファイアウォール許可リスト | ❌ No | Step 4 |
> | Hardcoded URLs / ハードコードされたURL | ⚠️ Copied but wrong / コピーされるが不正 | Step 5 |
> | Secrets & env variables / シークレットと環境変数 | N/A | Not used / 不使用 |
> | Commit history / コミット履歴 | ❌ No | Not needed / 不要 |

---

## 📦 Step 1: Create Repository from Template / テンプレートからリポジトリを作成

### English

1. Go to the **Copilot Pulse template repository** (repository name: `cloud-agent-demo`): [github.com/shinyay/cloud-agent-demo](https://github.com/shinyay/cloud-agent-demo)
2. Click the green **"Use this template"** button (top right of the page)
3. Select **"Create a new repository"**
4. Fill in the form:
   - **Owner**: Select your GitHub username or organization
   - **Repository name**: Choose a name (e.g., `my-intel-dashboard`, `weekly-digest`, etc.)
   - **Description** (optional): e.g., "My AI-curated intelligence dashboard"
   - **Visibility**: Choose **Public** (required for free GitHub Pages) or **Private** (requires GitHub Pro/Team/Enterprise for Pages)
5. Click **"Create repository"**
6. Wait a few seconds — your new repository will be ready

### 日本語

1. **Copilot Pulseテンプレートリポジトリ**（リポジトリ名: `cloud-agent-demo`）にアクセス: [github.com/shinyay/cloud-agent-demo](https://github.com/shinyay/cloud-agent-demo)
2. ページ右上の緑色の **「Use this template」** ボタンをクリック
3. **「Create a new repository」** を選択
4. フォームを入力:
   - **Owner**: 自分のGitHubユーザー名または組織を選択
   - **Repository name**: リポジトリ名を入力（例: `my-intel-dashboard`、`weekly-digest` など）
   - **Description**（任意）: 例: 「AI キュレーションによるインテリジェンスダッシュボード」
   - **Visibility**: **Public**（無料のGitHub Pagesに必要）または **Private**（GitHub Pages にはPro/Team/Enterpriseが必要）
5. **「Create repository」** をクリック
6. 数秒待つと、新しいリポジトリが作成されます

> **⚠️ Important / 重要:**
> At this point, all files are copied but links still point to the original `shinyay/cloud-agent-demo`. We'll fix this automatically in Step 5.
>
> この時点ではファイルはすべてコピーされていますが、リンクは元の `shinyay/cloud-agent-demo` を指しています。Step 5で自動的に修正します。

---

## 🌐 Step 2: Enable GitHub Pages / GitHub Pages を有効化

> **This step must be done manually in the GitHub UI. There are no command-line tools needed — everything is done through clickable buttons and dropdowns.**
>
> **このステップはGitHub UIで手動で行います。コマンドラインツールは不要で、すべてボタンとドロップダウンで操作します。**

### English

1. Go to your new repository on GitHub (e.g., `https://github.com/YOUR_USERNAME/YOUR_REPO`)
2. Click the **"Settings"** tab — it's in the top menu bar of your repository (look for the ⚙️ gear icon or the word "Settings" near the right end)
3. In the **left sidebar**, scroll down until you see a section called **"Code and automation"**
4. Click **"Pages"** in that section
5. Under **"Build and deployment"**, you'll see two dropdowns:
   - **Source**: Click the dropdown and select **"Deploy from a branch"**
   - **Branch**: Click the first dropdown and select **`main`** (or `master`), then click the second dropdown and select **`/ (root)`**
6. Click the **"Save"** button
7. Wait approximately **2–3 minutes** for the first deployment to complete
8. Refresh the page — a blue banner will appear at the top: **"Your site is live at `https://YOUR_USERNAME.github.io/YOUR_REPO/`"**

> **💡 Tip:** Copy that URL! That will be your dashboard address.

### 日本語

1. GitHubで新しいリポジトリにアクセス（例: `https://github.com/YOUR_USERNAME/YOUR_REPO`）
2. リポジトリの上部メニューバーにある **「Settings」** タブをクリック（⚙️ 歯車アイコン、または右端付近の「Settings」という文字）
3. **左サイドバー**を下にスクロールして **「Code and automation」** セクションを探す
4. そのセクションにある **「Pages」** をクリック
5. **「Build and deployment」** セクションに2つのドロップダウンが表示されます:
   - **Source**: ドロップダウンをクリックして **「Deploy from a branch」** を選択
   - **Branch**: 最初のドロップダウンで **`main`**（または `master`）を選択し、2番目のドロップダウンで **`/ (root)`** を選択
6. **「Save」** ボタンをクリック
7. 最初のデプロイが完了するまで約 **2〜3分** 待つ
8. ページを再読み込みすると、青いバナーが上部に表示されます: **「Your site is live at `https://YOUR_USERNAME.github.io/YOUR_REPO/`」**

> **💡 ヒント:** そのURLをメモしておいてください！それがあなたのダッシュボードのアドレスになります。

> **📝 Note / 注意:**
> The site will deploy but links won't work correctly yet — they still point to the original repository. This is expected and will be fixed in Step 5.
>
> サイトはデプロイされますが、リンクはまだ元のリポジトリを指しているため正しく動作しません。これはStep 5で修正されます。

---

## 🤖 Step 3: Enable Copilot Cloud Agent / Copilot Cloud Agent を有効化

> **This step must be done manually in the GitHub UI. No coding required — just toggle some settings.**
>
> **このステップはGitHub UIで手動で行います。コーディングは不要で、設定をオンにするだけです。**

### English

1. Go to your new repository on GitHub
2. Click the **"Settings"** tab
3. In the **left sidebar**, look for **"Copilot"** under the "Code and automation" section
4. Click **"Copilot"** — you'll see a submenu appear with **"Cloud agent"**
5. Click **"Cloud agent"**
6. On the settings page, make sure the main toggle at the top is turned **"On"** (it should turn blue/green)
7. **Recommended**: Enable all the safety features shown on the page — these protect your repository:
   - ✅ Firewall (controls which websites Copilot can visit)
   - ✅ CodeQL analysis (security scanning)
   - ✅ Secret scanning (prevents accidentally sharing passwords)

**If you don't see the "Copilot" section in Settings:**

- ✅ Make sure you're signed into the GitHub account with a Copilot subscription
- ✅ If you're in an organization (your company's GitHub account), your org admin may need to enable Copilot Cloud Agent at the organization level first — contact your IT/admin team
- ✅ Check [GitHub Copilot documentation](https://docs.github.com/en/copilot) for the latest setup instructions

### 日本語

1. GitHubで新しいリポジトリにアクセス
2. **「Settings」** タブをクリック
3. **左サイドバー**の「Code and automation」セクションにある **「Copilot」** を探す
4. **「Copilot」** をクリックするとサブメニューが表示され、**「Cloud agent」** が見えます
5. **「Cloud agent」** をクリック
6. 設定ページで、上部のメイントグルを **「On」** に設定（青または緑色になります）
7. **推奨**: ページに表示されているすべての安全機能を有効にする:
   - ✅ Firewall（Copilotがアクセスできるウェブサイトを制御）
   - ✅ CodeQL analysis（セキュリティスキャン）
   - ✅ Secret scanning（パスワードの誤共有防止）

**Settings に「Copilot」セクションが表示されない場合:**

- ✅ Copilotサブスクリプションのあるアカウントでサインインしているか確認してください
- ✅ 組織アカウント（会社のGitHubアカウント）の場合は、組織管理者が先に組織レベルでCopilot Cloud Agentを有効化する必要があります。IT/管理者チームに連絡してください
- ✅ 最新の手順は[GitHub Copilotドキュメント](https://docs.github.com/ja/copilot)を参照してください

---

## 🔥 Step 4: Configure Firewall Allowlist / ファイアウォール許可リストを設定

> **Think of the firewall allowlist as a "permission list" of websites that the AI is allowed to visit. Without it, the AI can't fetch news from Microsoft and GitHub blogs, so reports will contain no real content.**
>
> **ファイアウォール許可リストとは、AIがアクセスを許可されているウェブサイトの「許可リスト」です。これがないと、AIはMicrosoftやGitHubのブログからニュースを取得できないため、レポートに実際のコンテンツが含まれません。**

### English

1. Go to your repository on GitHub
2. Click the **"Settings"** tab
3. In the **left sidebar**, find **"Copilot"** under "Code and automation"
4. Click **"Copilot"** → **"Cloud agent"**
5. Scroll down to find the **"Firewall"** section
6. Look for a **"Custom allowlist"** or **"Allowed domains"** input area
7. Add the following domains — you can type or paste them one by one:

**Microsoft domains (10):**

| Domain | Content |
|--------|---------|
| `blogs.microsoft.com` | Official Microsoft Blog, On the Issues |
| `microsoft.com` | AI Blog, Security Blog |
| `devblogs.microsoft.com` | Developer Blogs (.NET, VS Code, Azure SDK) |
| `azure.microsoft.com` | Azure Blog |
| `news.microsoft.com` | News Center (including Japan: /ja-jp/) |
| `blogs.windows.com` | Windows Blog |
| `developer.microsoft.com` | Microsoft for Developers |
| `techcommunity.microsoft.com` | Tech Community Hub |
| `tech.hub.ms` | Tech Hub |
| `learn.microsoft.com` | Microsoft Learn |

**GitHub domains (3):**

| Domain | Content |
|--------|---------|
| `github.blog` | Official GitHub Blog + Changelog |
| `docs.github.com` | GitHub Documentation |
| `githubuniverse.com` | GitHub Universe Conference |

8. Click **"Save"** to apply the allowlist

> **⚠️ What happens without the allowlist? / 許可リストがない場合どうなるか？**
>
> Copilot will still be able to process issues and create report files, but all attempts to fetch content will be **blocked**. The resulting reports will lack real content and may contain only AI-generated summaries based on training data — not current information.
>
> Copilotは引き続きIssueを処理しレポートファイルを作成できますが、コンテンツを取得するすべての試みが**ブロック**されます。結果として生成されるレポートは最新のコンテンツではなく、トレーニングデータに基づくAI生成の要約のみとなります。

### 日本語

1. GitHubでリポジトリにアクセス
2. **「Settings」** タブをクリック
3. **左サイドバー**の **「Code and automation」** セクションにある **「Copilot」** をクリック
4. **「Copilot」** → **「Cloud agent」** をクリック
5. 下にスクロールして **「Firewall」** セクションを探す
6. **「Custom allowlist」** または **「Allowed domains」** の入力エリアを探す
7. 以下のドメインを1つずつ入力または貼り付けて追加:

**Microsoftドメイン（10個）:**

| ドメイン | コンテンツ |
|---------|-----------|
| `blogs.microsoft.com` | Microsoft公式ブログ、On the Issues |
| `microsoft.com` | AIブログ、セキュリティブログ |
| `devblogs.microsoft.com` | 開発者ブログ（.NET、VS Code、Azure SDK） |
| `azure.microsoft.com` | Azureブログ |
| `news.microsoft.com` | ニュースセンター（日本語版: /ja-jp/ を含む） |
| `blogs.windows.com` | Windowsブログ |
| `developer.microsoft.com` | Microsoft for Developers |
| `techcommunity.microsoft.com` | Tech Community Hub |
| `tech.hub.ms` | Tech Hub |
| `learn.microsoft.com` | Microsoft Learn |

**GitHubドメイン（3個）:**

| ドメイン | コンテンツ |
|---------|-----------|
| `github.blog` | GitHub公式ブログ + Changelog |
| `docs.github.com` | GitHubドキュメント |
| `githubuniverse.com` | GitHub Universeカンファレンス |

8. **「Save」** をクリックして許可リストを適用

> **💡 ヒント:** ドメインはいつでも追加・削除できます。Copilotに追加のソース（例：自社ブログ）からも取得させたい場合は、そのドメインもここに追加してください。

---

### 🔧 Alternative for Technical Users: Actions Variable Method / 技術者向け代替手段：Actions変数を使用する方法

> **⚠️ This section is for technical users only. If you're not familiar with GitHub Actions variables or the command line, skip this section — the UI method above is all you need.**
>
> **⚠️ このセクションは技術者向けです。GitHub Actions変数やコマンドラインに不慣れな場合はこのセクションをスキップしてください。上記のUI手順だけで十分です。**

You can also configure the firewall allowlist using a repository Actions variable. This method can be used alongside the UI method above.

**Variable name:** `COPILOT_AGENT_FIREWALL_ALLOW_LIST_ADDITIONS`

**Value** (comma-separated list of all domains):

```
blogs.microsoft.com,microsoft.com,devblogs.microsoft.com,azure.microsoft.com,news.microsoft.com,blogs.windows.com,developer.microsoft.com,techcommunity.microsoft.com,tech.hub.ms,learn.microsoft.com,github.blog,github.com,docs.github.com,githubuniverse.com
```

**Using GitHub CLI:**

```bash
gh variable set COPILOT_AGENT_FIREWALL_ALLOW_LIST_ADDITIONS \
  --body "blogs.microsoft.com,microsoft.com,devblogs.microsoft.com,azure.microsoft.com,news.microsoft.com,blogs.windows.com,developer.microsoft.com,techcommunity.microsoft.com,tech.hub.ms,learn.microsoft.com,github.blog,github.com,docs.github.com,githubuniverse.com"
```

**Using GitHub UI (Settings → Secrets and variables → Actions):**

1. Go to **Settings** → **Secrets and variables** → **Actions**
2. Click the **"Variables"** tab
3. Click **"New repository variable"**
4. Name: `COPILOT_AGENT_FIREWALL_ALLOW_LIST_ADDITIONS`
5. Value: paste the comma-separated list above
6. Click **"Add variable"**

> **💡 Note:** Both the UI Custom allowlist (above) and the Actions variable work together. The Actions variable adds domains to the allowlist automatically when Copilot runs in GitHub Actions.
>
> **💡 注:** UIのカスタム許可リストとActions変数は併用できます。Actions変数は、CopilotがGitHub Actionsで実行される際に自動的にドメインを許可リストに追加します。

---

## ⚙️ Step 5: Run Automated Setup / 自動セットアップを実行

> **This is the "personalization" step — the AI will automatically update your repository files so all links point to your repository instead of the original template. You don't need to edit any files manually!**
>
> **これは「パーソナライズ」ステップです。AIがリポジトリ内のファイルを自動的に更新し、すべてのリンクが元のテンプレートではなくあなたのリポジトリを指すようにします。ファイルを手動で編集する必要はありません！**

### English

1. In your new repository, click the **"Issues"** tab (in the top menu)
2. Click the green **"New issue"** button
3. You'll see a list of issue templates — find and click **"🔧 Initial Setup / 初期セットアップ"**
   - (If you don't see templates, click "New issue" and look for a template list)
4. Fill in the short form that appears:
   - **GitHub Username**: Type your GitHub username exactly as it appears in your GitHub URL (e.g., if your profile is `github.com/octocat`, enter `octocat`)
   - **Repository Name**: Type your repository name exactly as it appears in the URL (e.g., `my-intel-dashboard`)
5. Click **"Submit new issue"**
6. Now assign the issue to **@copilot** — this is what triggers the AI:
   - Look at the **right sidebar** of the issue page
   - Click the **⚙️ gear icon** next to **"Assignees"**
   - Type **`copilot`** in the search box that appears
   - Click **"Copilot"** in the dropdown list
   - The gear icon closes — you should now see "Copilot" listed under Assignees
7. **Wait 3–5 minutes** — the AI will:
   - Read your username and repository name from the issue
   - Find all the links in 8 files that still point to the original template
   - Replace them with links pointing to your repository
   - Create a **Pull Request** (PR) with all the changes
8. You'll get a notification and see a new **Pull Request** appear in the "Pull requests" tab — click on it to review:
   - Scroll through to verify your username and repo name appear in the file previews
   - ✅ If it looks correct, you're ready to merge
9. Click the green **"Merge pull request"** button, then **"Confirm merge"**
10. **Wait 2–3 minutes** for GitHub Pages to rebuild and redeploy your site

### 日本語

1. 新しいリポジトリで上部メニューの **「Issues」** タブをクリック
2. 緑色の **「New issue」** ボタンをクリック
3. Issueテンプレートの一覧が表示されたら、**「🔧 Initial Setup / 初期セットアップ」** を探してクリック
   - （テンプレートが表示されない場合は「New issue」をクリックしてテンプレート一覧を探してください）
4. 表示される短いフォームを入力:
   - **GitHub Username**: GitHubのURLに表示されるとおりにGitHubユーザー名を入力（例: プロフィールが `github.com/octocat` なら `octocat` を入力）
   - **Repository Name**: URLに表示されるとおりにリポジトリ名を入力（例: `my-intel-dashboard`）
5. **「Submit new issue」** をクリック
6. Issueを **@copilot** に割り当てる — これがAIのトリガーになります:
   - Issueページの **右サイドバー** を確認
   - **「Assignees」** の横にある **⚙️ 歯車アイコン** をクリック
   - 表示される検索ボックスに **`copilot`** と入力
   - ドロップダウンリストで **「Copilot」** をクリック
   - 歯車アイコンが閉じ、Assigneesに「Copilot」が表示されます
7. **3〜5分待つ** — AIが以下を実行します:
   - IssueからユーザーIDとリポジトリ名を読み取る
   - 元のテンプレートを指している8ファイルのリンクをすべて検出
   - あなたのリポジトリを指すリンクに置換
   - すべての変更を含む **Pull Request（PR）** を作成
8. 通知が届き、「Pull requests」タブに新しい **Pull Request** が表示されます。クリックして確認:
   - ファイルのプレビューにあなたのユーザー名とリポジトリ名が表示されていることを確認
   - ✅ 正しければマージの準備完了
9. 緑色の **「Merge pull request」** ボタンをクリックし、**「Confirm merge」** をクリック
10. GitHub Pagesの再ビルドと再デプロイが完了するまで **2〜3分待つ**

> **💡 What Copilot Changes / Copilotが変更する内容:**
>
> | File / ファイル | Changes / 変更内容 |
> |---|---|
> | `_config.yml` | `url` and `baseurl` — Jekyll site URL configuration<br>`url` と `baseurl` — Jekyll サイトURL設定 |
> | `_layouts/default.html` | Navigation links (nav, footer) — issue creation & repo links<br>ナビゲーションリンク（ナビ、フッター）— Issue作成 & リポジトリリンク |
> | `_layouts/post.html` | Issue link in report header<br>レポートヘッダーのIssueリンク |
> | `index.md` | "New Report" CTA buttons (3 locations)<br>「New Report」CTAボタン（3箇所） |
> | `about.md` | Issue creation links in English & Japanese sections<br>英語・日本語セクションのIssue作成リンク |
> | `admin.md` | JavaScript `window.open()` URLs for design & agent management (4 locations)<br>デザイン＆エージェント管理のJavaScript `window.open()` URL（4箇所） |
> | `README.md` | Dashboard URL, issue links, admin page URL<br>ダッシュボードURL、Issueリンク、管理ページURL |
> | `.github/ISSUE_TEMPLATE/config.yml` | Contact links to About & Dashboard pages<br>About & ダッシュボードページへのリンク |

---

## ✨ Step 6: Verify Your Dashboard / ダッシュボードを確認

### English

After merging the setup PR, let's make sure everything is working:

1. **Visit your dashboard**: Open `https://YOUR_USERNAME.github.io/YOUR_REPO/` in your browser
   - ✅ You should see the ⚡ Copilot Pulse Intelligence Dashboard homepage
   - ✅ The header shows "⚡ Copilot Pulse" with navigation links
   - ❌ If you see a 404 error, wait another 2–3 minutes and try again (GitHub Pages may still be building)

2. **Check the navigation links work correctly**:
   - Click **"Home"** — should stay on your dashboard
   - Click **"About"** — should show the About page
   - Click **"+ New Report"** — **important!** This should open a new issue form **in YOUR repository** (the URL should show your username, not `shinyay`)
   - Click **"⚙️ Admin"** — should open the admin management page

3. **Create your first report** — this is the ultimate test!
   - Click **"+ New Report"** (or go to Issues → New Issue → select "Research Request")
   - Fill in a topic, for example: *"This week's highlights from the Microsoft blog"*
   - Click **"Submit new issue"**
   - Assign the issue to **@copilot** (same as you did in Step 5)
   - Wait **5–10 minutes** for Copilot to research and create a Pull Request
   - Go to the **"Pull requests"** tab and merge the PR Copilot created
   - Visit your dashboard — the new report should appear!

4. **Verify the admin page works**:
   - Go to `https://YOUR_USERNAME.github.io/YOUR_REPO/admin/`
   - Click **"🎨 Create Design Issue"** — the issue should open in YOUR repository
   - Click **"🛠️ Create Agent Issue"** — the issue should open in YOUR repository

### 日本語

セットアップPRをマージした後、すべてが正常に動作することを確認します：

1. **ダッシュボードにアクセス**: ブラウザで `https://YOUR_USERNAME.github.io/YOUR_REPO/` を開く
   - ✅ ⚡ Copilot Pulseインテリジェンスダッシュボードのホームページが表示される
   - ✅ ヘッダーに「⚡ Copilot Pulse」とナビゲーションリンクが表示される
   - ❌ 404エラーが表示された場合は、さらに2〜3分待ってから再試行（GitHub Pagesがまだビルド中の可能性があります）

2. **ナビゲーションリンクが正しく動作することを確認**:
   - **「Home」** をクリック — ダッシュボードに留まること
   - **「About」** をクリック — Aboutページが表示されること
   - **「+ New Report」** をクリック — **重要！** **あなたのリポジトリ**でIssueフォームが開くこと（URLにあなたのユーザー名が表示され、`shinyay` ではないこと）
   - **「⚙️ Admin」** をクリック — 管理ページが開くこと

3. **最初のレポートを作成** — これが最終テストです！
   - **「+ New Report」** をクリック（またはIssues → New Issue → 「Research Request」を選択）
   - トピックを入力、例: 「今週のMicrosoftブログのハイライト」
   - **「Submit new issue」** をクリック
   - Step 5と同様に、Issueを **@copilot** に割り当てる
   - CopilotがリサーチしてPull Requestを作成するまで **5〜10分** 待つ
   - **「Pull requests」** タブに移動し、Copilotが作成したPRをマージ
   - ダッシュボードを確認 — 新しいレポートが表示されます！

4. **管理ページを確認**:
   - `https://YOUR_USERNAME.github.io/YOUR_REPO/admin/` にアクセス
   - **「🎨 Create Design Issue」** をクリック — **あなたのリポジトリ**でIssueが開くこと
   - **「🛠️ Create Agent Issue」** をクリック — **あなたのリポジトリ**でIssueが開くこと

> **🎉 Congratulations! / おめでとうございます！**
>
> Your ⚡ Copilot Pulse intelligence dashboard is now fully set up and ready to demo! Create issues, assign them to @copilot, and start building your curated knowledge base. Great for weekly briefings, team updates, and Microsoft seller demos.
>
> ⚡ Copilot Pulseインテリジェンスダッシュボードの設定が完了しました！Issueを作成し、@copilotに割り当てて、キュレーションされたナレッジベースの構築を始めましょう。週次ブリーフィング、チームアップデート、Microsoftのセラーデモに最適です。

---

## 📖 Appendix: Manual Setup (Advanced) / 付録：手動セットアップ（上級者向け）

> **⚠️ This section is for technical users only. If you completed Step 5 successfully using the automated Copilot method, you do NOT need this section.**
>
> Use this if you don't have Copilot access, prefer to make changes manually, or want to understand exactly what was changed.
>
> **⚠️ このセクションは技術者向けです。Step 5のCopilot自動化手順が正常に完了した場合、このセクションは不要です。**
>
> Copilotにアクセスできない場合、手動で変更したい場合、または変更内容を詳しく理解したい場合に使用してください。

### What Needs to Change / 変更が必要な箇所

Replace these two values throughout the repository:

リポジトリ全体で以下の2つの値を置換してください：

| Find / 検索 | Replace With / 置換 |
|---|---|
| `shinyay` | Your GitHub username / あなたのGitHubユーザー名 |
| `cloud-agent-demo` | Your repository name / あなたのリポジトリ名 |

### Complete Reference List / 完全な参照リスト

Below is every hardcoded reference that must be updated:

以下は更新が必要なすべてのハードコードされた参照です：

#### File 1: `_config.yml` (2 changes / 2箇所)

```yaml
# Before / 変更前:
url: "https://shinyay.github.io"
baseurl: "/cloud-agent-demo"

# After / 変更後:
url: "https://YOUR_USERNAME.github.io"
baseurl: "/YOUR_REPO"
```

#### File 2: `_layouts/default.html` (3 changes / 3箇所)

```html
<!-- Line 22: Nav CTA link / ナビCTAリンク -->
<!-- Before --> <a href="https://github.com/shinyay/cloud-agent-demo/issues/new?template=research-request.yml" ...>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml" ...>

<!-- Line 38: Footer GitHub link / フッターGitHubリンク -->
<!-- Before --> <a href="https://github.com/shinyay/cloud-agent-demo" ...>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO" ...>

<!-- Line 40: Footer New Report link / フッター新規レポートリンク -->
<!-- Before --> <a href="https://github.com/shinyay/cloud-agent-demo/issues/new?template=research-request.yml" ...>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml" ...>
```

#### File 3: `_layouts/post.html` (1 change / 1箇所)

```html
<!-- Issue link in report header / レポートヘッダーのIssueリンク -->
<!-- Before --> <a href="https://github.com/shinyay/cloud-agent-demo/issues/{{ page.issue_number }}" ...>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/{{ page.issue_number }}" ...>
```

#### File 4: `index.md` (3 changes / 3箇所)

```html
<!-- Hero CTA / ヒーローCTA -->
<!-- Before --> <a href="https://github.com/shinyay/cloud-agent-demo/issues/new?template=research-request.yml" ...>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml" ...>
<!-- (3 occurrences — same replacement for all) -->
<!-- （3箇所 — すべて同じ置換） -->
```

#### File 5: `about.md` (2 changes / 2箇所)

```html
<!-- English issue link / 英語Issueリンク -->
<!-- Before --> <a href="https://github.com/shinyay/cloud-agent-demo/issues/new?template=research-request.yml" ...>New Report →</a>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml" ...>New Report →</a>

<!-- Japanese issue link / 日本語Issueリンク -->
<!-- Before --> <a href="https://github.com/shinyay/cloud-agent-demo/issues/new?template=research-request.yml" ...>新しいIssue →</a>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml" ...>新しいIssue →</a>
```

#### File 6: `admin.md` (4 changes / 4箇所)

```javascript
// All 4 window.open() calls — replace the base URL:
// すべてのwindow.open()呼び出し — ベースURLを置換:

// Before / 変更前:
window.open('https://github.com/shinyay/cloud-agent-demo/issues/new?title=...')

// After / 変更後:
window.open('https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?title=...')
```

#### File 7: `README.md` (4 changes / 4箇所)

```markdown
<!-- Dashboard URL / ダッシュボードURL -->
[shinyay.github.io/cloud-agent-demo](https://shinyay.github.io/cloud-agent-demo/)
→ [YOUR_USERNAME.github.io/YOUR_REPO](https://YOUR_USERNAME.github.io/YOUR_REPO/)

<!-- Issue link / Issueリンク -->
[**Issues → New Issue**](https://github.com/shinyay/cloud-agent-demo/issues/new?template=research-request.yml)
→ [**Issues → New Issue**](https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml)

<!-- Project structure / プロジェクト構造 -->
cloud-agent-demo/  →  YOUR_REPO/

<!-- Admin page / 管理ページ -->
[/admin/](https://shinyay.github.io/cloud-agent-demo/admin/)
→ [/admin/](https://YOUR_USERNAME.github.io/YOUR_REPO/admin/)
```

#### File 8: `.github/ISSUE_TEMPLATE/config.yml` (2 changes / 2箇所)

```yaml
# Before / 変更前:
url: "https://shinyay.github.io/cloud-agent-demo/about/"
url: "https://shinyay.github.io/cloud-agent-demo/"

# After / 変更後:
url: "https://YOUR_USERNAME.github.io/YOUR_REPO/about/"
url: "https://YOUR_USERNAME.github.io/YOUR_REPO/"
```

### 🔧 Quick Replace Commands (Command Line / Terminal) / 一括置換コマンド（コマンドライン・ターミナル）

> **⚠️ This section requires using the Terminal / command line. Non-technical users should use the Copilot automated method in Step 5 instead.**
>
> **⚠️ このセクションはターミナル/コマンドラインの使用が必要です。非技術者の方はStep 5のCopilot自動化手順を使用してください。**

If you have the repository cloned locally, you can use these commands:

リポジトリをローカルにクローンしている場合、以下のコマンドで一括置換できます：

```bash
# Replace GitHub username / GitHubユーザー名を置換
# ⚠️ Replace YOUR_USERNAME with your actual username
# ⚠️ YOUR_USERNAME を実際のユーザー名に置き換えてください
find . -type f \( -name "*.md" -o -name "*.html" -o -name "*.yml" \) \
  -not -path "./.git/*" -not -path "./SETUP.md" \
  -exec sed -i 's/shinyay/YOUR_USERNAME/g' {} +

# Replace repository name / リポジトリ名を置換
# ⚠️ Replace YOUR_REPO with your actual repository name
# ⚠️ YOUR_REPO を実際のリポジトリ名に置き換えてください
find . -type f \( -name "*.md" -o -name "*.html" -o -name "*.yml" \) \
  -not -path "./.git/*" -not -path "./SETUP.md" \
  -exec sed -i 's/cloud-agent-demo/YOUR_REPO/g' {} +

# Commit the changes / 変更をコミット
git add -A
git commit -m "chore: configure repository for my account"
git push
```

> **⚠️ Important / 重要:**
> The `sed` commands above replace ALL occurrences. Review the changes with `git diff` before committing to make sure nothing unexpected was changed.
>
> 上記の `sed` コマンドはすべての出現箇所を置換します。コミットする前に `git diff` で変更内容を確認し、予期しない変更がないことを確かめてください。

---

## ❓ Troubleshooting / トラブルシューティング

### Problem: GitHub Pages is not deploying / GitHub Pagesがデプロイされない

**English:**
- **Check Settings → Pages**: Make sure Source is set to "Deploy from a branch", Branch is `main`, folder is `/ (root)`.
- **Check the Actions tab**: Look for a workflow called "pages build and deployment". If it failed, click it to see the error details.
- **Just wait**: The first deployment can take up to 5 minutes.

**日本語:**
- **Settings → Pagesを確認**: Sourceが「Deploy from a branch」、Branchが`main`、フォルダが`/ (root)`に設定されていることを確認。
- **Actionsタブを確認**: 「pages build and deployment」というワークフローを探す。失敗している場合はクリックしてエラー内容を確認。
- **待機**: 最初のデプロイには最大5分かかることがあります。

---

### Problem: Copilot doesn't respond to the issue / CopilotがIssueに反応しない

**English:**
- **Check the assignment**: The issue must be assigned to the official GitHub `Copilot` bot — not a human user named "copilot". Check the Assignees section on the issue — it should show a robot/bot icon.
- **Check Copilot is enabled**: Go to Settings → Copilot → Cloud agent and make sure it shows "Enabled".
- **Check organization policy**: If your account is part of a company/organization, the org admin may need to enable Copilot Cloud Agent at the organization level first.
- **Retry**: If nothing happens after 5 minutes, remove @copilot from Assignees and re-add it.

**日本語:**
- **割り当てを確認**: Issueは公式の GitHub `Copilot` ボットに割り当てる必要があります（「copilot」という名前の人間ユーザーではありません）。IssueのAssigneesセクションにロボット/ボットアイコンが表示されていることを確認。
- **Copilotが有効か確認**: Settings → Copilot → Cloud agentで「Enabled」になっていることを確認。
- **組織ポリシーを確認**: 会社・組織のアカウントの場合、組織管理者が先に組織レベルでCopilot Cloud Agentを有効化する必要がある場合があります。
- **再試行**: 5分経っても何も起きない場合は、AssigneesからCopilotを削除して再度追加してください。

---

### Problem: Links still point to the original repository / リンクがまだ元のリポジトリを指している

**English:**
- **Check the PR was merged**: The setup PR created by Copilot in Step 5 must be merged — changes don't take effect until it's merged.
- **Wait for redeploy**: After merging, GitHub Pages needs 2–3 minutes to rebuild. Watch the Actions tab for a new "pages build and deployment" run.
- **Hard refresh your browser**: Press **Ctrl+Shift+R** (Windows/Linux) or **Cmd+Shift+R** (Mac) to force-reload without browser cache.
- **If Copilot missed something**: Use the [Manual Setup (Advanced)](#-appendix-manual-setup-advanced--付録手動セットアップ上級者向け) section above.

**日本語:**
- **PRがマージされたか確認**: Step 5でCopilotが作成したセットアップPRがマージされている必要があります。マージするまで変更は反映されません。
- **再デプロイを待つ**: マージ後、GitHub Pagesの再ビルドに2〜3分かかります。Actionsタブで新しい「pages build and deployment」の実行を確認してください。
- **ブラウザをハードリフレッシュ**: **Ctrl+Shift+R**（Windows/Linux）または **Cmd+Shift+R**（Mac）でキャッシュをクリアして強制再読み込み。
- **Copilotが見落とした箇所がある場合**: 上記の[手動セットアップ（上級者向け）](#-appendix-manual-setup-advanced--付録手動セットアップ上級者向け)セクションを使用してください。

---

### Problem: Reports contain no real content / レポートに実際のコンテンツが含まれない

**English:**
- **Check the firewall allowlist**: Go to Settings → Copilot → Cloud agent → scroll to the Firewall section. Make sure all 13 domains from [Step 4](#-step-4-configure-firewall-allowlist--ファイアウォール許可リストを設定) are listed.
- **Check the PR comments**: If the AI's web requests were blocked, you'll see warnings in the PR conversation listing the blocked domains.
- **Add missing domains**: If a specific news source isn't appearing, add its domain to the allowlist in Settings and try creating a new report issue.

**日本語:**
- **ファイアウォール許可リストを確認**: Settings → Copilot → Cloud agentに移動し、Firewallセクションまでスクロール。[Step 4](#-step-4-configure-firewall-allowlist--ファイアウォール許可リストを設定)の13ドメインがすべてリストされていることを確認。
- **PRコメントを確認**: AIのウェブリクエストがブロックされた場合、PRの会話欄にブロックされたドメインに関する警告が表示されます。
- **不足しているドメインを追加**: 特定のニュースソースが表示されない場合は、そのドメインをSettingsの許可リストに追加して、新しいレポートIssueを作成してみてください。
