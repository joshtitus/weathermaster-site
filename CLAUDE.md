# Weathermaster website: notes for making updates

The live site for **weathermasterinc.com** (Weathermaster Door and Window, Fort Worth, TX). It was built and launched
on October 31, 2026. Josh Titus (GitHub: joshtitus) is the site admin. Joe Hiller owns the business.
Credit: "Website designed by Titus Developments."

## How an update ships

1. Edit files under `site/`, test them locally (see Testing), then commit and push to `main` on
   github.com/joshtitus/weathermaster-site. The repo is private, and the Claude GitHub App is installed on it.
2. Deploy from GoDaddy cPanel: **Git Version Control → weathermaster-site → Manage → Pull or Deploy**.
   Click **Update from Remote**, then **Deploy HEAD Commit**.
   - Claude can do this in Josh's Chrome, where he is already signed in to GoDaddy. It goes through
     the cPanel File Manager tab, either by clicking or by calling UAPI `VersionControl/update` and
     `VersionControlDeployment/create` with fetch.
   - Josh signs in to GoDaddy himself. Never type a password.
   - GoDaddy's bot protection blocks the built-in browser, so use Chrome.
   - Auto-mode has blocked typing into GoDaddy DNS fields. Josh enters DNS records himself.
3. `.cpanel.yml` copies `site/.` into `/home/xtmzof1etue8/public_html/` and deletes the README.txt notes.
   Files outside `site/`, including this one, are never deployed.
4. Check the live site with Chrome (`fetch` from a weathermasterinc.com tab works). The sandbox shell can't reach
   the domain.
   - Confirm the pages return 200 and that http and www redirect to https without www.
   - Confirm `/images/` and the READMEs return 403.
   - Check for broken images and console errors.
5. If page content changed, update `<lastmod>` in `site/sitemap.xml`. Google and Bing re-read the sitemap
   automatically. Only use "Request indexing" in Search Console for a big change, and only for the page that changed.

## Layout

- `site/index.html`: the "Choose your view" selector, linking to `commercial/` and `residential/`.
- `site/commercial/index.html`: the commercial glazing site (about 2,000 lines), with `images/` beside it.
- `site/residential/index.html`: the luxury residential site (about 1,300 lines), with `images/` beside it.
- `.htaccess` in each folder:
  - HTTPS and www→non-www redirects, HSTS, and the CSP.
  - X-Frame-Options and nosniff, no directory listing, and blocks on README, dotfiles, md, bak, zip, and log files.
  - 301s from the old WordPress URLs and caching rules.
- `sitemap.xml`, `robots.txt`, `llms.txt`.
- The `README.txt` files in `site/` explain each page in detail. Read them before a big change.

Every page is a single self-contained HTML file with inline CSS and JS. There is no build step, framework, or npm.

## Brand and copy rules

- **Fonts:** Archivo and Instrument Serif, from Google Fonts. **Colors:** ink, paper, sun, and amber.
- **Textures:** residential uses marble and oak on linen or ivory (not white). Commercial uses concrete on charcoal
  (not pure black). The two sites are a yin-yang pair: different, but they complement each other.
- **Logo:** use only the existing Weathermaster logo files in `images/`.
- **Case:** section-name menu items are in Title Case. Buttons and body text are in sentence case.
- **Commas:** use Oxford commas everywhere.
- **Photos:** prefer real Weathermaster project photos. Use AI images only where they're clearly appropriate.

## Things that must stay true

- **No phone number or email in the HTML source** (to stop scraping). Contact goes through the free-consultation
  form or the `.call-joe` button.
  - The button dials on phones and reveals the number on desktop.
  - The contact details are assembled at runtime from `WM_C` near the end of each site's script, with the
    phone digits shifted by one character code.
  - JSON-LD has no telephone or email field. Never paste the plain number or email into the markup.
- **CSP:** scripts and styles come only from 'self' (inline is allowed). Fonts come only from Google Fonts. Images
  and video come only from 'self'. Adding analytics, embeds, maps, or any outside host means updating the
  `Content-Security-Policy` line in all three `.htaccess` files.
- **Header and footer:**
  - The header logo scrolls to the top. The footer logo goes to the selector (`../`).
  - Each footer has a clear cross-link to the other site, plus Facebook and Instagram, and nothing else.
  - The Titus Developments credit (`images/titus-developments.svg`, 56px tall) sits at the bottom of each footer,
    with padding so the auto-play bar doesn't cover it.
- **Local-preview links:** links carry `data-local` attributes that point at `index.html` files. A small script swaps
  them in when the page runs from file:// or localhost. Keep `data-local` on any new cross-page link.
- **Testimonial sections:** there are no real testimonials yet. Commercial shows **project spotlights**
  (Waggoner Building, The Star, Star-Telegram Building, and Mule Alley). Residential shows **Joe Hiller's promise**.
  Both live in the `QUOTES` array. Keep the section layout if real reviews replace them later.
- **Gallery:**
  - The residential mobile grid uses `grid-auto-flow: row dense`, so there are no blank cells.
  - Both galleries end with a "More on Instagram" link.

## Auto-play

- **Engine:** `AP`, `apSet`, `apStep`, `apEnd`, and `apRestart`. Pinned sections expose hold hooks (`__film`,
  `__entry`, `__dusk`), each with `.left()` for the time-left estimate.
- **Control bar (`#apbar`):** expands to Slow, Normal, and Fast plus skip, with a progress ring that shows time left.
  - Speeds are `{slow: .6, normal: 1, fast: 1.7}`. The choice is saved in localStorage as `wm-ap-speed`.
  - On touch, the first tap expands the bar and the second tap pauses.
  - Arrow keys change speed, and Space pauses.
- **Run times at Normal:** about 2:31 for commercial and 2:19 for residential. Re-test auto-play after changing
  any pinned section.

## Testing

- The sandbox can't reach Google Fonts. Route fonts.gstatic.com to local font files, or accept fallback fonts in
  screenshots.
- Serve `site/` with `python3 -m http.server` and use Playwright (preinstalled) to take screenshots at desktop
  (1440 wide) and phone (390 wide). Check the console, auto-play, the call button, and the form.
- Before putting a new video or major visual on the site, show it to Josh and get his OK.

## Working rules from Josh

- Don't spend Kling or other paid generation credits without asking first. For images, the ChatGPT desktop app on
  Josh's PC is fine to use through computer use.
- Get Josh's OK before downloading anything.
- When copying files to his computer, write each one under a new filename, then read it back from the device to
  confirm it changed.
- Commit as Josh Titus <josh.titus@gmail.com> with clear messages. Push only to this repo.
- Josh handles sign-ins, OAuth grants, DNS entries, and permanent deletes himself.

## Accounts and status (as of October 31, 2026)

- **Hosting:** GoDaddy cPanel (Economy). The old WordPress sites and their databases have been removed.
- **SSL:** Standard SSL covering the root domain and www. The certificate expires March 4, 2027 (the subscription
  renews October 2027), so check renewal in mid-February 2027.
- **Google Search Console:** domain property verified by DNS TXT. Sitemap submitted (Success), and indexing
  requested for the three pages.
- **Bing Webmaster Tools:** imported from Search Console. The sitemap and the three URLs have been submitted.
  Bing also feeds ChatGPT search, Copilot, and DuckDuckGo.
- **Google Business Profile:**
  - "Weathermaster Door and Window", category Window installation service, set up as a service-area business with
    no public address.
  - Service areas: DFW and Houston (11 areas). Phone and website are set.
  - Joe has been invited as an owner and emailed instructions for the video verification. The old duplicate
    profile was removed.
  - After it's verified, add hours, a description, photos, and secondary categories, then ask clients for reviews.

## Open items

- Joe signs off on the wording of the residential promise.
- Test the form and the call button on a phone.
- Update the website link on Facebook and Instagram.
- Change the GoDaddy login email from joe@weathermasterinc.com to a personal address (Josh will handle this later).
- Optional analytics (needs a CSP update).
- Cancel or refund the leftover Managed WordPress plan, and decide on Website Security Essential.
- Ideas parked for later:
  - Commercial hero concepts 2 and 3.
  - Residential testimonial effects (sun through the window, sheers, door, lights on, and signed by hand). The mocks
    are in `Downloads\weathermaster-testimonial-mocks` on Josh's PC.
