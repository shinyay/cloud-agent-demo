# 🚀 Setup Guide / セットアップガイド

> **This guide helps you set up your own Intelligence Dashboard after creating a repository from the Project Miki template.**
>
> **このガイドは、Project Mikiテンプレートからリポジトリを作成した後、あなた専用のインテリジェンスダッシュボードをセットアップする手順を説明します。**

---

## 📋 Table of Contents / 目次

1. [Prerequisites / 前提条件](#-prerequisites--前提条件)
2. [Step 1: Create Repository from Template / テンプレートからリポジトリを作成](#-step-1-create-repository-from-template--テンプレートからリポジトリを作成)
3. [Step 2: Enable GitHub Pages / GitHub Pages を有効化](#-step-2-enable-github-pages--github-pages-を有効化)
4. [Step 3: Enable Copilot Coding Agent / Copilot Coding Agent を有効化](#-step-3-enable-copilot-coding-agent--copilot-coding-agent-を有効化)
5. [Step 4: Configure Firewall Allowlist / ファイアウォール許可リストを設定](#-step-4-configure-firewall-allowlist--ファイアウォール許可リストを設定)
6. [Step 5: Run Automated Setup / 自動セットアップを実行](#-step-5-run-automated-setup--自動セットアップを実行)
7. [Step 6: Verify Your Dashboard / ダッシュボードを確認](#-step-6-verify-your-dashboard--ダッシュボードを確認)
8. [Appendix: Manual Setup / 付録：手動セットアップ](#-appendix-manual-setup--付録手動セットアップ)

---

## ✅ Prerequisites / 前提条件

Before you begin, make sure you have the following:

セットアップを始める前に、以下を確認してください：

| Requirement / 要件 | Description / 説明 |
|---|---|
| **GitHub Account** | A GitHub account (free or paid)<br>GitHubアカウント（無料または有料） |
| **GitHub Copilot Subscription** | Required for the Coding Agent to work. Copilot Individual, Business, or Enterprise plan.<br>Coding Agentを動作させるために必要です。Copilot Individual、Business、またはEnterpriseプランが必要です。 |
| **Copilot Coding Agent Access** | Copilot Coding Agent must be available on your account or organization. Check your Copilot settings.<br>Copilot Coding Agentがアカウントまたは組織で利用可能であること。Copilot設定で確認してください。 |

> **📢 What's NOT copied from the template / テンプレートからコピーされないもの:**
>
> When you create a repository from a template, all **files** are copied, but the following **settings** are NOT carried over. You must configure them manually (Steps 2-4):
>
> テンプレートからリポジトリを作成すると、すべての**ファイル**はコピーされますが、以下の**設定**は引き継がれません。手動で設定する必要があります（Step 2〜4）：
>
> | Setting / 設定 | Copied? / コピー？ | Action / 対応 |
> |---|---|---|
> | Files & workflows / ファイルとワークフロー | ✅ Yes | — |
> | GitHub Pages settings / GitHub Pages設定 | ❌ No | Step 2 |
> | Copilot Coding Agent / Copilot Coding Agent | ❌ No | Step 3 |
> | Firewall allowlist / ファイアウォール許可リスト | ❌ No | Step 4 |
> | Hardcoded URLs / ハードコードされたURL | ⚠️ Copied but wrong / コピーされるが不正 | Step 5 |
> | Secrets & env variables / シークレットと環境変数 | N/A | Not used / 不使用 |
> | Commit history / コミット履歴 | ❌ No | Not needed / 不要 |

---

## 📦 Step 1: Create Repository from Template / テンプレートからリポジトリを作成

### English

1. Go to the **Project Miki template repository**: [github.com/shinyay/project-miki](https://github.com/shinyay/project-miki)
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

1. **Project Mikiテンプレートリポジトリ**にアクセス: [github.com/shinyay/project-miki](https://github.com/shinyay/project-miki)
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
> At this point, all files are copied but links still point to the original `shinyay/project-miki`. We'll fix this in Step 4.
>
> この時点ではファイルはすべてコピーされていますが、リンクは元の `shinyay/project-miki` を指しています。Step 4で修正します。

---

## 🌐 Step 2: Enable GitHub Pages / GitHub Pages を有効化

> **This step must be done manually in the GitHub UI. Copilot cannot change repository settings.**
>
> **このステップはGitHub UIで手動で行う必要があります。Copilotはリポジトリ設定を変更できません。**

### English

1. Go to your new repository on GitHub
2. Click **"Settings"** tab (top menu bar, near the right side — gear icon)
3. In the left sidebar, scroll down to **"Code and automation"** section
4. Click **"Pages"**
5. Under **"Build and deployment"**:
   - **Source**: Select **"Deploy from a branch"**
   - **Branch**: Select **`main`** (or `master`) and **`/ (root)`**
6. Click **"Save"**
7. Wait approximately 2-3 minutes for the first deployment
8. A banner will appear at the top: **"Your site is live at https://YOUR_USERNAME.github.io/YOUR_REPO/"**

### 日本語

1. GitHubで新しいリポジトリにアクセス
2. 上部メニューバーの **「Settings」** タブをクリック（右側、歯車アイコン付近）
3. 左サイドバーの **「Code and automation」** セクションまでスクロール
4. **「Pages」** をクリック
5. **「Build and deployment」** セクションで:
   - **Source**: **「Deploy from a branch」** を選択
   - **Branch**: **`main`**（または `master`）と **`/ (root)`** を選択
6. **「Save」** をクリック
7. 最初のデプロイメントが完了するまで約2〜3分待つ
8. ページ上部にバナーが表示されます: **「Your site is live at https://YOUR_USERNAME.github.io/YOUR_REPO/」**

> **📝 Note / 注意:**
> The site will deploy but links won't work correctly yet — they still point to the original repository. This is expected and will be fixed in Step 4.
>
> サイトはデプロイされますが、リンクはまだ元のリポジトリを指しているため正しく動作しません。これはStep 4で修正されます。

---

## 🤖 Step 3: Enable Copilot Coding Agent / Copilot Coding Agent を有効化

> **This step must be done manually in the GitHub UI. Copilot cannot enable itself.**
>
> **このステップはGitHub UIで手動で行う必要があります。Copilotは自分自身を有効化できません。**

### English

1. Go to your new repository on GitHub
2. Click **"Settings"** tab
3. In the left sidebar, find **"Copilot"** section (under "Code and automation")
4. Click **"Copilot"**
5. Find **"Copilot coding agent"** (or "Copilot in GitHub Actions")
6. Toggle it to **"Enabled"**
7. If prompted about permissions, accept the default permissions

**If you don't see the Copilot section:**
- Make sure you have a Copilot subscription (Individual, Business, or Enterprise)
- If you're in an organization, the org admin may need to enable Copilot Coding Agent at the organization level first
- Check [GitHub Copilot documentation](https://docs.github.com/en/copilot) for the latest setup instructions

### 日本語

1. GitHubで新しいリポジトリにアクセス
2. **「Settings」** タブをクリック
3. 左サイドバーの **「Code and automation」** セクションにある **「Copilot」** をクリック
4. **「Copilot」** をクリック
5. **「Copilot coding agent」**（または「Copilot in GitHub Actions」）を見つける
6. **「Enabled」** に切り替える
7. 権限についてプロンプトが表示された場合、デフォルトの権限を承認する

**Copilotセクションが表示されない場合:**
- Copilotサブスクリプション（Individual、Business、またはEnterprise）があることを確認してください
- 組織アカウントの場合、組織管理者が先に組織レベルでCopilot Coding Agentを有効化する必要がある場合があります
- 最新のセットアップ手順は[GitHub Copilotドキュメント](https://docs.github.com/ja/copilot)を参照してください

---

## 🔥 Step 4: Configure Firewall Allowlist / ファイアウォール許可リストを設定

> **The Copilot Coding Agent has a built-in firewall that blocks network requests to domains not on the allowlist. Without this step, Copilot cannot fetch content from Microsoft and GitHub blogs to generate reports.**
>
> **Copilot Coding Agentには、許可リストにないドメインへのネットワークリクエストをブロックするファイアウォールが内蔵されています。このステップなしでは、CopilotはMicrosoftやGitHubのブログからコンテンツを取得してレポートを生成できません。**

### English

1. Go to your repository on GitHub
2. Click **"Settings"** tab
3. In the left sidebar, find **"Copilot"** section (under "Code and automation")
4. Click **"Copilot"** → **"Coding agent"**
5. Find the **"Firewall"** or **"Allowlist"** configuration section
6. Add the following domains one by one:

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

7. Click **"Save"** to apply the allowlist

> **💡 Tip:** You can add or remove domains later at any time. If you want Copilot to fetch from additional sources (e.g., your company's blog), add those domains here too.

### 日本語

1. GitHubでリポジトリにアクセス
2. **「Settings」** タブをクリック
3. 左サイドバーの **「Code and automation」** セクションにある **「Copilot」** をクリック
4. **「Copilot」** → **「Coding agent」** をクリック
5. **「Firewall」** または **「Allowlist」** の設定セクションを見つける
6. 以下のドメインを1つずつ追加:

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

7. **「Save」** をクリックして許可リストを適用

> **💡 ヒント:** ドメインはいつでも追加・削除できます。Copilotに追加のソース（例：自社ブログ）からも取得させたい場合は、そのドメインもここに追加してください。

> **⚠️ What happens without the allowlist? / 許可リストがない場合どうなるか？**
>
> Copilot will still be able to process issues and create report files, but all `curl` commands to fetch content will be **blocked by the firewall**. The resulting reports will lack real content and may contain only AI-generated summaries based on training data — not current information.
>
> Copilotは引き続きIssueを処理しレポートファイルを作成できますが、コンテンツを取得するすべての `curl` コマンドが**ファイアウォールによりブロック**されます。結果として生成されるレポートは最新のコンテンツではなく、トレーニングデータに基づくAI生成の要約のみとなります。

---

## ⚙️ Step 5: Run Automated Setup / 自動セットアップを実行

> **This is where the magic happens! Copilot Coding Agent will automatically update all 20 hardcoded references in your repository.**
>
> **ここが本番です！Copilot Coding Agentがリポジトリ内の20箇所のハードコードされた参照を自動的に更新します。**

### English

1. In your new repository, go to **"Issues"** tab
2. Click **"New issue"**
3. Find and select the **"🔧 Initial Setup / 初期セットアップ"** template
4. Fill in the form:
   - **GitHub Username**: Enter your GitHub username (e.g., `octocat`)
   - **Repository Name**: Enter your repository name (e.g., `my-intel-dashboard`)
5. Click **"Submit new issue"**
6. Now assign the issue to **@copilot**:
   - On the right sidebar, click the **"Assignees"** gear icon (⚙️)
   - Type **`copilot`** in the search box
   - Select **"Copilot"** from the dropdown
7. Wait 3-5 minutes — Copilot will:
   - Read the issue and your inputs
   - Find all 20 hardcoded references across 8 files
   - Replace `shinyay` → your username, `project-miki` → your repo name
   - Create a Pull Request with all changes
8. You'll see a new PR appear — review it:
   - Check that URLs look correct
   - Verify `_config.yml` has your username and repo name
9. Click **"Merge pull request"** → **"Confirm merge"**
10. Wait 2-3 minutes for GitHub Pages to redeploy

### 日本語

1. 新しいリポジトリで **「Issues」** タブに移動
2. **「New issue」** をクリック
3. **「🔧 Initial Setup / 初期セットアップ」** テンプレートを選択
4. フォームを入力:
   - **GitHub Username**: 自分のGitHubユーザー名を入力（例: `octocat`）
   - **Repository Name**: リポジトリ名を入力（例: `my-intel-dashboard`）
5. **「Submit new issue」** をクリック
6. Issueを **@copilot** に割り当てる:
   - 右サイドバーの **「Assignees」** 歯車アイコン（⚙️）をクリック
   - 検索ボックスに **`copilot`** と入力
   - ドロップダウンから **「Copilot」** を選択
7. 3〜5分待つ — Copilotが以下を実行します:
   - Issueと入力内容を読み取る
   - 8ファイルにまたがる20箇所のハードコードされた参照をすべて検出
   - `shinyay` → あなたのユーザー名、`project-miki` → あなたのリポジトリ名に置換
   - すべての変更を含むPull Requestを作成
8. 新しいPRが表示されます — レビューしてください:
   - URLが正しいことを確認
   - `_config.yml` にあなたのユーザー名とリポジトリ名が入っていることを確認
9. **「Merge pull request」** → **「Confirm merge」** をクリック
10. GitHub Pagesが再デプロイされるまで2〜3分待つ

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

After merging the setup PR, verify everything works:

1. **Visit your dashboard**: `https://YOUR_USERNAME.github.io/YOUR_REPO/`
   - ✅ You should see the Intelligence Dashboard homepage
   - ✅ The header shows "🌸 Project Miki" with working navigation links

2. **Check the navigation links**:
   - Click **"Home"** — should go to your dashboard
   - Click **"About"** — should show the About page with correct issue links
   - Click **"+ New Report"** — should open a new issue form **in your repository** (not the original)
   - Click **"⚙️ Admin"** — should open the admin management page

3. **Try creating your first report**:
   - Click **"+ New Report"** or go to Issues → New Issue → Research Request
   - Fill in a topic (e.g., "This week's Microsoft blog highlights")
   - Submit the issue
   - Assign to **@copilot**
   - Wait 5-10 minutes for the PR
   - Merge the PR
   - Check your dashboard — the report should appear!

4. **Verify the admin page**:
   - Go to `https://YOUR_USERNAME.github.io/YOUR_REPO/admin/`
   - Click "🎨 Create Design Issue" — should open an issue in YOUR repo
   - Click "🛠️ Create Agent Issue" — should open an issue in YOUR repo

### 日本語

セットアップPRをマージした後、すべてが正常に動作することを確認します：

1. **ダッシュボードにアクセス**: `https://YOUR_USERNAME.github.io/YOUR_REPO/`
   - ✅ インテリジェンスダッシュボードのホームページが表示される
   - ✅ ヘッダーに「🌸 Project Miki」と正しいナビゲーションリンクが表示される

2. **ナビゲーションリンクを確認**:
   - **「Home」** をクリック — ダッシュボードに移動すること
   - **「About」** をクリック — Aboutページに正しいIssueリンクが表示されること
   - **「+ New Report」** をクリック — **自分のリポジトリ**（元のリポジトリではなく）で新しいIssueフォームが開くこと
   - **「⚙️ Admin」** をクリック — 管理ページが開くこと

3. **最初のレポートを作成してみる**:
   - **「+ New Report」** をクリック、またはIssues → New Issue → Research Requestに移動
   - トピックを入力（例: 「今週のMicrosoftブログのハイライト」）
   - Issueを送信
   - **@copilot** に割り当てる
   - PRが届くまで5〜10分待つ
   - PRをマージ
   - ダッシュボードを確認 — レポートが表示されるはずです！

4. **管理ページを確認**:
   - `https://YOUR_USERNAME.github.io/YOUR_REPO/admin/` にアクセス
   - 「🎨 Create Design Issue」をクリック — **自分のリポジトリ**でIssueが開くこと
   - 「🛠️ Create Agent Issue」をクリック — **自分のリポジトリ**でIssueが開くこと

> **🎉 Congratulations! / おめでとうございます！**
>
> Your intelligence dashboard is now fully configured and ready to use. Create issues, assign to @copilot, and start building your curated knowledge base!
>
> インテリジェンスダッシュボードの設定が完了しました！Issueを作成し、@copilotに割り当てて、キュレーションされたナレッジベースの構築を始めましょう！

---

## 📖 Appendix: Manual Setup / 付録：手動セットアップ

> **Use this if you don't have Copilot access, or prefer to make changes manually.**
>
> **Copilotを利用できない場合、または手動で変更したい場合に使用してください。**

### What Needs to Change / 変更が必要な箇所

Replace these two values throughout the repository:

リポジトリ全体で以下の2つの値を置換してください：

| Find / 検索 | Replace With / 置換 |
|---|---|
| `shinyay` | Your GitHub username / あなたのGitHubユーザー名 |
| `project-miki` | Your repository name / あなたのリポジトリ名 |

### Complete Reference List / 完全な参照リスト

Below is every hardcoded reference that must be updated:

以下は更新が必要なすべてのハードコードされた参照です：

#### File 1: `_config.yml` (2 changes / 2箇所)

```yaml
# Before / 変更前:
url: "https://shinyay.github.io"
baseurl: "/project-miki"

# After / 変更後:
url: "https://YOUR_USERNAME.github.io"
baseurl: "/YOUR_REPO"
```

#### File 2: `_layouts/default.html` (3 changes / 3箇所)

```html
<!-- Line 22: Nav CTA link / ナビCTAリンク -->
<!-- Before --> <a href="https://github.com/shinyay/project-miki/issues/new?template=research-request.yml" ...>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml" ...>

<!-- Line 38: Footer GitHub link / フッターGitHubリンク -->
<!-- Before --> <a href="https://github.com/shinyay/project-miki" ...>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO" ...>

<!-- Line 40: Footer New Report link / フッター新規レポートリンク -->
<!-- Before --> <a href="https://github.com/shinyay/project-miki/issues/new?template=research-request.yml" ...>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml" ...>
```

#### File 3: `_layouts/post.html` (1 change / 1箇所)

```html
<!-- Issue link in report header / レポートヘッダーのIssueリンク -->
<!-- Before --> <a href="https://github.com/shinyay/project-miki/issues/{{ page.issue_number }}" ...>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/{{ page.issue_number }}" ...>
```

#### File 4: `index.md` (3 changes / 3箇所)

```html
<!-- Hero CTA / ヒーローCTA -->
<!-- Before --> <a href="https://github.com/shinyay/project-miki/issues/new?template=research-request.yml" ...>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml" ...>
<!-- (3 occurrences — same replacement for all) -->
<!-- （3箇所 — すべて同じ置換） -->
```

#### File 5: `about.md` (2 changes / 2箇所)

```html
<!-- English issue link / 英語Issueリンク -->
<!-- Before --> <a href="https://github.com/shinyay/project-miki/issues/new?template=research-request.yml" ...>New Report →</a>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml" ...>New Report →</a>

<!-- Japanese issue link / 日本語Issueリンク -->
<!-- Before --> <a href="https://github.com/shinyay/project-miki/issues/new?template=research-request.yml" ...>新しいIssue →</a>
<!-- After  --> <a href="https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml" ...>新しいIssue →</a>
```

#### File 6: `admin.md` (4 changes / 4箇所)

```javascript
// All 4 window.open() calls — replace the base URL:
// すべてのwindow.open()呼び出し — ベースURLを置換:

// Before / 変更前:
window.open('https://github.com/shinyay/project-miki/issues/new?title=...')

// After / 変更後:
window.open('https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?title=...')
```

#### File 7: `README.md` (4 changes / 4箇所)

```markdown
<!-- Dashboard URL / ダッシュボードURL -->
[shinyay.github.io/project-miki](https://shinyay.github.io/project-miki/)
→ [YOUR_USERNAME.github.io/YOUR_REPO](https://YOUR_USERNAME.github.io/YOUR_REPO/)

<!-- Issue link / Issueリンク -->
[**Issues → New Issue**](https://github.com/shinyay/project-miki/issues/new?template=research-request.yml)
→ [**Issues → New Issue**](https://github.com/YOUR_USERNAME/YOUR_REPO/issues/new?template=research-request.yml)

<!-- Project structure / プロジェクト構造 -->
project-miki/  →  YOUR_REPO/

<!-- Admin page / 管理ページ -->
[/admin/](https://shinyay.github.io/project-miki/admin/)
→ [/admin/](https://YOUR_USERNAME.github.io/YOUR_REPO/admin/)
```

#### File 8: `.github/ISSUE_TEMPLATE/config.yml` (2 changes / 2箇所)

```yaml
# Before / 変更前:
url: "https://shinyay.github.io/project-miki/about/"
url: "https://shinyay.github.io/project-miki/"

# After / 変更後:
url: "https://YOUR_USERNAME.github.io/YOUR_REPO/about/"
url: "https://YOUR_USERNAME.github.io/YOUR_REPO/"
```

### Quick Replace Commands / 一括置換コマンド

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
  -exec sed -i 's/project-miki/YOUR_REPO/g' {} +

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

### GitHub Pages is not deploying / GitHub Pagesがデプロイされない

- **Check Settings → Pages**: Make sure the source is set to "Deploy from a branch" with `main` branch and `/ (root)` folder.
- **Check Actions tab**: Look for a "pages build and deployment" workflow run. If it failed, click on it to see the error.
- **Wait**: First deployment can take up to 5 minutes.

---

- **Settings → Pagesを確認**: ソースが「Deploy from a branch」に設定され、`main` ブランチと `/ (root)` フォルダが選択されていることを確認してください。
- **Actionsタブを確認**: 「pages build and deployment」ワークフローの実行を探してください。失敗した場合はクリックしてエラーを確認してください。
- **待機**: 最初のデプロイメントには最大5分かかる場合があります。

### Copilot doesn't respond to the setup issue / Copilotがセットアップissueに反応しない

- **Check assignment**: Make sure the issue is assigned to `Copilot` (not a human user named "copilot").
- **Check Copilot is enabled**: Settings → Copilot → Coding agent should be "Enabled".
- **Check organization policy**: If in an org, Copilot Coding Agent may need to be enabled at the org level.
- **Retry**: Sometimes it takes a minute. If nothing happens after 5 minutes, unassign and re-assign @copilot.

---

- **割り当てを確認**: Issueが `Copilot`（「copilot」という名前の人間のユーザーではなく）に割り当てられていることを確認してください。
- **Copilotが有効か確認**: Settings → Copilot → Coding agentが「Enabled」であること。
- **組織ポリシーを確認**: 組織アカウントの場合、Copilot Coding Agentが組織レベルで有効化されている必要がある場合があります。
- **再試行**: 反応するまで1分ほどかかる場合があります。5分経っても何も起きない場合は、@copilotの割り当てを解除して再度割り当ててください。

### Links still point to the original repository / リンクがまだ元のリポジトリを指している

- **Check the PR was merged**: The setup PR created by Copilot must be merged for changes to take effect.
- **Wait for redeploy**: After merging, GitHub Pages needs 2-3 minutes to rebuild.
- **Hard refresh**: Try Ctrl+Shift+R (or Cmd+Shift+R on Mac) to clear browser cache.
- **Check manually**: If Copilot missed something, use the [Manual Setup](#-appendix-manual-setup--付録手動セットアップ) section above.

---

- **PRがマージされたか確認**: Copilotが作成したセットアップPRがマージされている必要があります。
- **再デプロイを待つ**: マージ後、GitHub Pagesの再ビルドに2〜3分かかります。
- **ハードリフレッシュ**: Ctrl+Shift+R（Macの場合はCmd+Shift+R）でブラウザキャッシュをクリアしてください。
- **手動確認**: Copilotが見落とした箇所がある場合は、上記の[手動セットアップ](#-appendix-manual-setup--付録手動セットアップ)セクションを使用してください。

### Reports contain no real content / レポートに実際のコンテンツが含まれない

- **Check the firewall allowlist**: Go to Settings → Copilot → Coding agent → Firewall. Make sure all 13 domains from [Step 4](#-step-4-configure-firewall-allowlist--ファイアウォール許可リストを設定) are listed.
- **Check the PR comments**: If Copilot's `curl` requests were blocked, you may see warnings in the PR conversation mentioning blocked domains.
- **Add missing domains**: If a specific source isn't working, add its domain to the allowlist and try again.

---

- **ファイアウォール許可リストを確認**: Settings → Copilot → Coding agent → Firewallに移動し、[Step 4](#-step-4-configure-firewall-allowlist--ファイアウォール許可リストを設定)の13ドメインがすべてリストされていることを確認してください。
- **PRコメントを確認**: Copilotの`curl`リクエストがブロックされた場合、PRのコメントにブロックされたドメインに関する警告が表示される場合があります。
- **不足しているドメインを追加**: 特定のソースが機能しない場合は、そのドメインを許可リストに追加して再試行してください。
