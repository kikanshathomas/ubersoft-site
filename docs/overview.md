# Overview

Source of truth for this site: the repository root [README](../README.md) and this `docs/` folder. GitHub Pages does not publish these files. See [deploy.md](deploy.md).

## What it is

ubersoft.pro is the public company site for Ubersoft LLC. Visitors use it to see what the studio does (mobile apps, web services, IT consulting), open a product, or write to info@ubersoft.pro.

The home page (`index.html`) is one long page:

- **Services** (`#services`) — mobile app development, web services, IT consulting.
- **Our Products** (`#apps`) — one card per product. Cards link to the product site. Apps with a public Google Play listing also link to that listing. punchi.tv links to https://punchi.tv only.
- **About** (`#about`) — short studio description.
- **Contact** (`#contact`) — mailto and a click-to-copy button for info@ubersoft.pro, plus the Warrenton, VA mailing address.

`privacy.html` is the site privacy policy (effective date on the page: August 1, 2026). It describes a static site: GitHub Pages for hosting, GoatCounter for visit counts, and a separate privacy link for each product. `404.html` is the GitHub Pages error page ("Signal Lost").

The footer on the home and privacy pages links to the privacy policy, to https://ko-fi.com/ubersoft, and shows a copyright year. The home footer also includes the Google Play trademark line required wherever the Play badge is shown.

## Who it is for

People looking up the studio, possible clients, and anyone following a link from a product site back to the company. It is a marketing and contact page. Accounts, billing, and the products themselves are on the linked sites.

## How the files fit

Three HTML documents. Each one carries its own `<style>` and `<script>` blocks. There is no shared stylesheet, no bundler, and no template that stitches the pages together at build time. Jekyll copies the HTML through as static files (see [deploy.md](deploy.md)).

| Path | Role |
|---|---|
| `index.html`, `privacy.html`, `404.html` | The pages. |
| `assets/fonts/` | Self-hosted Chakra Petch (weights 400, 500, 600, 700) and Norwester. The pages do not request a Google font host. |
| `assets/img/` | Hero, section photos (WebP plus JPEG fallback), product icons, favicon SVG, Play badge. |
| `favicon.ico`, `favicon-32x32.png`, `apple-touch-icon.png` | Icons linked from every page. |
| `robots.txt`, `sitemap.xml` | Crawl rules. The sitemap lists the home page and the privacy policy. |
| `CNAME` | Custom domain `ubersoft.pro`. |
| `_config.yml` | Tells GitHub Pages' Jekyll build what to leave unpublished. |
| `CLAUDE.md` | Agent working rules. Excluded from the live site. |
| `README.md`, `docs/` | These docs. Excluded from the live site. |

Visit counting is the GoatCounter script at the bottom of each page (`https://ubersoft.goatcounter.com/count`, loaded from `gc.zgo.at`). That script is the only third-party request the pages make. The privacy policy states the same thing, so a new third-party tag needs a policy edit in the same change.

## Editing a product card

Copy an existing card in `index.html` (`#apps`). Point the site button at that product's site. Point the Play badge at that app's own listing, using the badge image already in the repo, and only when the listing is public. Then add the matching privacy link in `privacy.html` section 05.

The `.soon` style in `index.html` is the "Coming soon" marker for a card whose Play listing is not public yet. No card uses it right now. It stays so the next unreleased product can use the same treatment. Weight 700 of Chakra Petch is the face that marker uses.

There is no changelog in this repository. QA & Security owns product changelogs when a changelog file exists. This site does not have one.
