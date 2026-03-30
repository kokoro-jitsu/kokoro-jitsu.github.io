# Kokoro-Jitsu — Astro Setup Guide

## What You're Getting

This is a full Astro static site that replaces your current single-page `index.html`. Every "page" is now a real URL, browser back/forward works properly, and the layout is fully responsive on mobile.

**New URLs:**
- `/` — Home
- `/about` — About (with Four Pillars)
- `/self-defense` — Beyond Self-Defense
- `/ranks` — Ranks
- `/archive` — Archive
- `/blog` — Blog listing
- `/blog/flow-state` — Individual posts
- `/blog/what-ki-actually-is`
- `/blog/absorb-discard-add`
- `/blog/training-through-a-new-lens`

---

## One-Time Setup (5 minutes)

### 1. Install Node.js

Download and install Node.js from https://nodejs.org — choose the **LTS** version.

Verify it worked by opening a terminal and running:
```
node --version
```
You should see something like `v20.x.x`.

### 2. Unzip and navigate to the project folder

Unzip the file I gave you, then in your terminal:
```
cd kokoro-jitsu
```

### 3. Install dependencies

```
npm install
```

This downloads Astro and its dependencies. Takes about a minute, only needed once.

### 4. Preview locally

```
npm run dev
```

Open your browser to `http://localhost:4321` — you'll see the site running locally. Every change you save hot-reloads instantly.

---

## How to Deploy to GitHub Pages

### First time setup

1. Go to your GitHub repo `kokoro-jitsu.github.io`
2. Delete or archive the current `index.html` (or just replace everything)
3. Push all files from this project folder to the `main` branch

If you're starting fresh:
```bash
git init
git add .
git commit -m "Migrate to Astro"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/kokoro-jitsu.github.io.git
git push -u origin main
```

### Enable GitHub Pages with Actions

1. Go to your repo on GitHub → **Settings** → **Pages**
2. Under **Source**, select **GitHub Actions**
3. The deploy workflow (`.github/workflows/deploy.yml`) will automatically build and deploy on every push to `main`

After the first push, GitHub Actions will build the site and deploy it. Takes about 2 minutes. Your site will be live at `https://kokoro-jitsu.github.io`.

### Every update going forward

```bash
git add .
git commit -m "Your message here"
git push
```

That's it. GitHub Actions handles the build and deploy automatically.

---

## Adding a New Blog Post

Blog posts are Markdown files in `src/content/blog/`. Create a new file:

**`src/content/blog/my-post-title.md`**
```markdown
---
title: "My Post Title"
tag: "Philosophy"
excerpt: "A short description that appears on the blog listing page."
featured: false
---

Your content here. Standard Markdown.

## A Heading

A paragraph.

> A blockquote.
```

The filename becomes the URL: `my-post-title.md` → `/blog/my-post-title`

Set `featured: true` on one post to make it appear full-width at the top of the blog listing.

---

## Editing Existing Content

All page content lives in `src/pages/`. Each file is a `.astro` file — the HTML sections work exactly like regular HTML, so editing text is straightforward. The frontmatter at the top (between the `---` lines) sets the page title and which nav link is active.

The shared CSS (colors, fonts, responsive breakpoints) is in `src/styles/global.css`.

---

## What's Different from the Old Site

| Old | New |
|-----|-----|
| Single `index.html` | One `.astro` file per page |
| JS fake navigation | Real URLs, real browser history |
| No mobile layout | Full responsive breakpoints |
| Blog posts as JS sections | Blog posts as Markdown files |
| Manual base64 images | PNG files in `public/` |
| No deploy automation | GitHub Actions auto-deploys on push |

The design, colors, fonts, and all content are identical to what you had.
