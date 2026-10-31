# Weathermaster Door and Window — website

The live site for [weathermasterinc.com](https://weathermasterinc.com): a "Choose your view" selector page with
separate commercial and residential sites.

- `site/` — everything that goes on the web host (the contents of this folder belong in `public_html`).
  - `index.html` — the selector page
  - `commercial/` — commercial glazing site
  - `residential/` — luxury residential site
  - `.htaccess` (one per folder) — HTTPS, security headers, old-page redirects, and caching
  - `sitemap.xml`, `robots.txt`, and `llms.txt`
- `.cpanel.yml` — deployment recipe for GoDaddy cPanel's Git Version Control: copies `site/` into `public_html`
  (skipping the README notes).

Each page is a single self-contained HTML file with its images beside it: no build step and no frameworks.
See `site/README.txt`, `site/commercial/README.txt`, and `site/residential/README.txt` for details.

Website designed by Titus Developments.
