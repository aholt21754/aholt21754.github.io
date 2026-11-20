# Ann Holt — blog

Astro blog, deployed to GitHub Pages by `.github/workflows/deploy.yml` on every push to `main`.

## One-time setup
1. In the repo on GitHub: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
2. Push to `main` (or run the workflow from the Actions tab). The site appears at
   https://ann-holt.dev within a minute or two.

## Writing a post
Add `src/content/blog/my-post.md` (or `.mdx`):

```md
---
title: 'Post title'
description: 'One-line summary (used in previews and RSS)'
pubDate: 'Nov 20 2026'
heroImage: '../../assets/my-image.jpg'   # optional
---
Body in Markdown.
```

Commit and push. Preview locally with `npm install` then `npm run dev` (http://localhost:4321).

## Connecting a custom domain (later)
1. Buy the domain (e.g. Cloudflare or Porkbun).
2. Settings → Pages → Custom domain: enter it and save.
3. At the registrar, add the DNS records GitHub shows:
   - apex (`annholt.dev`): A records → 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153
   - `www`: CNAME → `aholt21754.github.io`
   (If using Cloudflare DNS, set these to "DNS only", not proxied.)
4. Add `public/CNAME` containing just the domain, and change `site` in `astro.config.mjs` to it.
5. Once the DNS check passes, tick **Enforce HTTPS**.

## Where things live
- Site title/description: `src/consts.ts`
- Home / About pages: `src/pages/index.astro`, `src/pages/about.astro`
- Header/footer links: `src/components/`
