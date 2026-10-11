# diffdev.io — homepage (user site)

GitHub Pages **user site** repo. Local folder name `diffdev-home`; on GitHub it must be
named `bruskiguy.github.io` and it serves **https://diffdev.io/**.

- `CNAME` contains `diffdev.io` — this claims the custom domain for this GitHub account.
  Every other Pages project repo under the same account is then served under
  `diffdev.io/<repo-name>` (e.g. https://diffdev.io/video-marketing/).
- Deployment: Settings → Pages → Deploy from a branch → `main` → `/ (root)`.

## How to update
Edit `index.html`, commit, push to `main`. GitHub Pages redeploys automatically.

## Blog
Static, zero-build blog living directly in this repo (no Astro/Jekyll — GitHub Pages
serves the folders as-is):

- `blog/index.html` → https://diffdev.io/blog/ (hub: post cards + "coming soon" placeholders)
- `blog/<slug>/index.html` → https://diffdev.io/blog/<slug>/ (one folder per post; clean URLs)

To publish a new post: create `blog/<slug>/index.html` (copy an existing post as the
template), then add a card for it in `blog/index.html` and optionally on the homepage.
Source markdown drafts live in the parent workspace folder (e.g. `blog.best-opensource-seo-tools.md`).

## SEO infrastructure
- `sitemap.xml` — every page on the domain. **Add a `<url>` entry for each new post.**
- `robots.txt` — crawl rules; disallows the blog template and points crawlers at the sitemap.
- `blog/feed.xml` — RSS 2.0 feed. **Add an `<item>` per new post** (pubDate is RFC 822, e.g.
  `Sat, 10 Oct 2026 12:00:00 GMT`; run `(Get-Date 'YYYY-MM-DD').ToUniversalTime().ToString('R')` to format).
- Blog pages declare the feed via `<link rel="alternate" type="application/rss+xml">` in `<head>`.

## Publishing checklist (every new post)
1. Copy `blog/_template.html` → `blog/<slug>/index.html`; replace every `{{PLACEHOLDER}}`
   (search for `{{`); **delete the `noindex` meta line**.
2. Add a post card in `blog/index.html` (copy the existing card, update text/date).
3. Add the URL to `sitemap.xml` and an `<item>` to `blog/feed.xml`; bump the feed's
   `lastBuildDate`.
4. Optional: feature it on the homepage ("New on the blog" card).
5. Commit + push `main`; GitHub Pages redeploys automatically.
