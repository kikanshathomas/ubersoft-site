# Deploy

https://ubersoft.pro/ is this repository, published by GitHub Pages.

## What publishes

Pages is configured on the repository as a legacy Jekyll build from branch `main`, folder `/`. The `CNAME` file contains:

```
ubersoft.pro
```

HTTPS is enforced in the Pages settings. The built-in workflow `pages-build-deployment` runs the build. This repository has no workflow file of its own.

Merging a pull request into `main` publishes the site. Company rules in `CLAUDE.md` still apply: a live site gets QA clearance and Thomas's go before it ships. Opening a docs pull request does not publish. Merging it does.

## What the Jekyll build does

`_config.yml` is the whole build configuration:

- No page has front matter. `require_front_matter: true` makes Jekyll copy markdown that lacks front matter as a raw file instead of turning it into HTML.
- `theme: null` keeps Pages from injecting its default theme stylesheet (`assets/css/style.css`).
- `exclude` holds files that must stay in git and stay off the public site: `CLAUDE.md`, `.claude`, `README.md`, and `docs/`.

Those excluded paths return the site 404 on ubersoft.pro. Everything else at the repository root is copied onto the site, including `CNAME` (so https://ubersoft.pro/CNAME serves the hostname), `robots.txt`, `sitemap.xml`, and the HTML pages.

Keep this Jekyll setup. A `.nojekyll` file would skip the build, the exclude list would stop applying, and `CLAUDE.md` would become a public URL again.

A new markdown file at the repository root would be published as a raw file unless it is added to `exclude`.

## Files the domain and crawlers depend on

Leave these in place. They are not linked from the home page, and they are still part of the live site:

- `CNAME` — removing or renaming it drops the custom domain.
- `404.html` — the filename is how GitHub Pages finds the error page.
- `sitemap.xml` — listed from `robots.txt` as `https://ubersoft.pro/sitemap.xml`. It names `/` and `/privacy.html`. Add a URL here only when a new public page should be crawled. Leave `404.html` out.
- `robots.txt` — `Allow: /` plus the sitemap line.

`sitemap.xml` `lastmod` is `2026-09-22`. Change it when the page content changes and you want crawlers to recrawl.

## Check before merging

Preview from a local static server, as the [README](../README.md) describes. On the preview, confirm:

- Home, privacy, and `/404.html` render, and in-page links (`#services`, `#apps`, `#about`, `#contact`) still scroll.
- The privacy footer link, each product URL, and each Play URL on the home cards match the table in the README.
- A new asset path used in HTML exists in the tree. A removed asset is not still named by `index.html`, `privacy.html`, `404.html`, or `sitemap.xml`.

After merge, the Pages build is the publish step. The public home page should match `index.html`. `https://ubersoft.pro/README.md` and `https://ubersoft.pro/docs/overview.md` should keep returning the 404 page.
