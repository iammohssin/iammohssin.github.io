# Mohsin Javaid — Portfolio

Personal portfolio / CV site. Single self-contained `index.html` — no build step, no dependencies.

Live at: https://iammohssin.github.io/ (once deployed — see below)

## Stack

Plain HTML, CSS, and vanilla JS. Inline styles and scripts, no bundler. Theme toggle (light/dark, persisted via `localStorage`), scroll-reveal via `IntersectionObserver`, and a small canvas-drawn schematic animation in the hero — all respect `prefers-reduced-motion`.

## Structure

```
portfolio/
├── index.html      # the entire site
├── robots.txt       # allows all crawlers, points to sitemap.xml
├── sitemap.xml       # single-URL sitemap for the root page
└── README.md
```

## Run locally

No build step — just open `index.html` in a browser, or serve it:

```bash
npx serve .
```

## Deploy to GitHub Pages

This is set up for a **user site**, served at the repo root with no subpath.

1. Create a GitHub repo named exactly `iammohssin.github.io` (must match your username exactly — this is what makes it a user site instead of a project site).
2. Push this folder's contents to the `main` branch:
   ```bash
   git init
   git add index.html robots.txt sitemap.xml README.md
   git commit -m "Initial portfolio site"
   git branch -M main
   git remote add origin https://github.com/iammohssin/iammohssin.github.io.git
   git push -u origin main
   ```
3. In the repo on GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `main` / `(root)`**.
4. Wait a minute or two, then visit `https://iammohssin.github.io/`.

No GitHub Actions workflow needed — Pages serves static files directly from the branch.

### If you'd rather use a project repo instead

Any repo name works (e.g. `portfolio`), but the site then lives at `https://iammohssin.github.io/portfolio/` instead of the root. If you go this route, update the following in `index.html`, `robots.txt`, and `sitemap.xml` to match the real path:
- `<link rel="canonical" href="...">`
- `og:url`, `og:image`, `twitter:image`
- the JSON-LD `"url"` field
- `sitemap.xml`'s `<loc>`

## SEO

- Open Graph + Twitter Card meta tags, canonical URL, `robots.txt`, `sitemap.xml`
- JSON-LD `Person` structured data (name, role, employer, location, social profiles)
- Single `<h1>`, semantic section headings, decorative icons marked `aria-hidden`
- `og:image` / `twitter:image` point to `/og-image.png`, which doesn't exist yet — add a 1200×630 image at the repo root (or drop the two meta tags) before relying on social link previews.

## Content

Bio, work history, and project details are sourced from GitHub (github.com/iammohssin), LinkedIn (linkedin.com/in/iammoshin), and the AuthLume/SimShare/Utility-Grid repos directly. Update the `/about`, `/experience`, and `/projects` sections in `index.html` by hand as things change — there's no CMS.
