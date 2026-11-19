# Ubersoft company site

Public website for Ubersoft LLC at [ubersoft.pro](https://ubersoft.pro/). The pages are hand-written HTML for a software studio that builds mobile apps and offers web services and IT consulting. GitHub Pages publishes the `main` branch. The custom domain comes from the `CNAME` file (`ubersoft.pro`).

This repository is the company site only. Each product's app and its own marketing site live in other repositories. The cards on the home page link out to those sites.

Repository docs (this file and `docs/`) are for people editing the site. [`_config.yml`](_config.yml) keeps them off the published site, the same way it keeps `CLAUDE.md` off ubersoft.pro.

- [docs/overview.md](docs/overview.md) — what the site is and how the files fit together
- [docs/deploy.md](docs/deploy.md) — how GitHub Pages publishes it

## Page map

| URL | File | Role |
|---|---|---|
| https://ubersoft.pro/ | `index.html` | Home. Sections: `#services`, `#apps`, `#about`, `#contact`. |
| https://ubersoft.pro/privacy.html | `privacy.html` | Privacy policy. Listed in `sitemap.xml`. |
| Any missing path | `404.html` | GitHub Pages uses this filename as the site 404. `noindex`. Omitted from the sitemap. Asset paths are root-absolute (`/assets/...`) so they still load when the 404 is shown for a URL below the root. |
| https://ubersoft.pro/robots.txt | `robots.txt` | Allows all crawlers and points at the sitemap. |
| https://ubersoft.pro/sitemap.xml | `sitemap.xml` | Lists `/` and `/privacy.html` only. |

`CNAME` is the Pages domain file. GitHub also serves it at https://ubersoft.pro/CNAME. It contains the hostname and nothing else.

## How the home page links to each product

The product cards are the blocks in `index.html` under `#apps`. A card with a public Play listing shows the shared badge image (`assets/img/google-play-badge.png`) and a link to that app's own listing. punchi.tv is a website, so its card links to the site only.

The privacy policy repeats the same products in section 05, with each app's own privacy URL. punchi.tv's policy is `https://punchi.tv/privacy` (no `.html`). When you add or rename a product, update the card and section 05 together.

| Product | On the home card | Privacy policy link |
|---|---|---|
| Zombie Bill Tracker | [zbilltracker.com](https://zbilltracker.com) and [Play `com.zbilltracker.app`](https://play.google.com/store/apps/details?id=com.zbilltracker.app) | https://zbilltracker.com/privacy.html |
| Invasion Of Zombies | [invasionofzombies.com](https://invasionofzombies.com) and [Play `com.invasionofzombies.app`](https://play.google.com/store/apps/details?id=com.invasionofzombies.app) | https://invasionofzombies.com/privacy.html |
| The App Lockr | [theapplockr.com](https://theapplockr.com) and [Play `com.theapplockr.app`](https://play.google.com/store/apps/details?id=com.theapplockr.app) | https://theapplockr.com/privacy.html |
| Wave: Check-In | [wavetoday.app](https://wavetoday.app) and [Play `com.wavetoday.app`](https://play.google.com/store/apps/details?id=com.wavetoday.app) | https://wavetoday.app/privacy.html |
| punchi.tv | [punchi.tv](https://punchi.tv) | https://punchi.tv/privacy |

A product announced before its Play listing is public can use the `.soon` label already styled in `index.html`. Add the Play badge after the listing is public. The footer carries the Google Play trademark line because those badges are on the page, and a Support Development link to https://ko-fi.com/ubersoft.

## Edit and preview

There is no install and no build step. CSS and the small scripts are inside each HTML file. Shared header, footer, and font setup are duplicated in `index.html`, `privacy.html`, and `404.html` (the 404 copy is shorter). A change to that chrome is an edit in each file that should show it.

From the repository root:

```bash
python3 -m http.server 8000
```

Open http://127.0.0.1:8000/ , http://127.0.0.1:8000/privacy.html , and http://127.0.0.1:8000/404.html . Use the local server rather than opening the files directly: the 404 page's asset URLs start with `/`, and the visit counter uses a protocol-relative script URL. Python does not serve `404.html` for a missing path. GitHub Pages does.

Contact mail is `info@ubersoft.pro` (the mailto link and the click-to-copy button). The street address in the contact block and the footer is part of the page copy: 332 W Lee Hwy, Suite 230, Warrenton, VA 20186.

## Publishing

Merging to `main` publishes https://ubersoft.pro/. See [docs/deploy.md](docs/deploy.md).
