# Publishing Documentation

This guide explains how to publish **DocWeaver** documentation to a live site using **GitHub Pages** or export-ready formats such as **MkDocs** and **GitBook**.  
It assumes your local repository is already up to date and passing CI (Docs Quality Check).

---

## 🌐 Publishing Options Overview

| Method | Output | Best For | Notes |
|--------|---------|-----------|-------|
| **GitHub Pages** | Static HTML rendered from `/docs` | Portfolio, demos | Built-in hosting, no config required |
| **MkDocs** | Themed static site (`/site`) | Larger documentation sets | Requires Python and MkDocs installed |
| **GitBook** | Cloud-hosted site | Collaborative teams | Markdown sync via GitHub |

---

## 🚀 Option 1 — GitHub Pages (Recommended)

Publishing from the `/docs` folder directly on GitHub is the simplest way to make your documentation public.

### 1. Prepare the `docs/` folder
Ensure your documentation site structure looks like this:

```
docs/
├── index.md
├── overview/
│   ├── what-is-docweaver.md
│   └── architecture.md
├── guides/
│   ├── getting-started.md
│   └── publishing.md
├── reference/
│   └── config-file.md
└── contributing/
    ├── content-standards.md
    └── branching-and-reviews.md
```

### 2. Enable GitHub Pages
1. Go to your repository on GitHub.  
2. Navigate to **Settings → Pages**.  
3. Under **Build and deployment**, set:
   - **Source:** “Deploy from a branch”  
   - **Branch:** `main`  
   - **Folder:** `/docs`
4. Click **Save**.

Your documentation will be published at:  
```
https://<your-username>.github.io/<repository-name>/
```

For example:  
[`https://chandlerpm.github.io/docweaver/`](https://chandlerpm.github.io/docweaver/)

### 3. Verify after deployment
- GitHub automatically builds and serves the `/docs` folder.  
- Refresh after 1–2 minutes; static Markdown pages render directly.  
- Confirm Mermaid diagrams, tables, and internal links render properly.

---

## ⚙️ Option 2 — Build Locally with MkDocs

If you want a more styled, navigable site:

### 1. Install MkDocs
```bash
pip install mkdocs mkdocs-material
```

### 2. Create `mkdocs.yml`
At your repo root:
```yaml
site_name: DocWeaver
theme:
  name: material
  palette:
    scheme: default
    primary: pink
    accent: coral
nav:
  - Home: index.md
  - Overview:
      - What is DocWeaver: docs/overview/what-is-docweaver.md
      - Architecture: docs/overview/architecture.md
  - Guides:
      - Getting Started: docs/guides/getting-started.md
      - Publishing: docs/guides/publishing.md
  - Reference:
      - Config File: docs/reference/config-file.md
  - Contributing:
      - Content Standards: docs/contributing/content-standards.md
      - Branching and Reviews: docs/contributing/branching-and-reviews.md
```

### 3. Build the site
```bash
mkdocs build
```
This creates a `/site` directory with HTML output.

### 4. Preview locally
```bash
mkdocs serve
```
Then open [http://127.0.0.1:8000](http://127.0.0.1:8000).

### 5. Optional: Deploy to Pages via Action
Add workflow `.github/workflows/mkdocs-deploy.yml`:

```yaml
name: MkDocs Deploy
on:
  push:
    branches: [main]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.x'
      - name: Install dependencies
        run: pip install mkdocs mkdocs-material
      - name: Build site
        run: mkdocs build
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./site
```

---

## ☁️ Option 3 — Sync to GitBook

GitBook allows you to connect your GitHub repository directly:

1. Sign in to [GitBook](https://www.gitbook.com/).  
2. Create a new space → choose **Import from GitHub**.  
3. Select your `docweaver` repository.  
4. Configure auto-sync on push.  
5. GitBook will build and host your Markdown content automatically.

**Tip:** Disable link-check CI for GitBook branches if you use special GitBook syntax.

---

## 🧩 Post-Publish Checklist

- ✅ All internal links work  
- ✅ Mermaid diagrams render  
- ✅ README badges match live status  
- ✅ Examples and code blocks format correctly  
- ✅ License and version footer visible  

---

## 🏁 Summary

| Method | Effort | Hosting | Recommended Use |
|---------|--------|----------|----------------|
| GitHub Pages | ⭐ Easy | GitHub | Portfolio showcase |
| MkDocs | ⭐⭐ Moderate | GitHub or custom | Themed documentation site |
| GitBook | ⭐⭐ Moderate | GitBook Cloud | Collaborative publishing |

---

> Choose the simplest publishing path first—**GitHub Pages** gives you a clean, linkable live site that pairs perfectly with your portfolio and CI workflow.
