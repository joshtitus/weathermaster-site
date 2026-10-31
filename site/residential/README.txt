Weathermaster Residential landing page
======================================

Lives at /residential/. To preview, open index.html at the top of the site folder and click Residential, or open
this folder's index.html directly. It is the light half of the pair with the commercial site:
honed marble and pale oak instead of the commercial site's dark concrete, serif headlines instead of wide caps, and a page that moves from golden hour into
evening (the commercial page moves from a dark room into light).

Same build rules as commercial: one self-contained index.html, images/ beside it, no frameworks or CDNs.
The only outside request is Google Fonts (Archivo and Instrument Serif).

The hero
- The house is a real Weathermaster home (from Instagram). ChatGPT made a sharper widescreen dusk version
  (hero-evening.jpg) and a matching golden-hour version (hero-day.jpg). The two are lined up to the pixel; keep
  them as a pair if either is replaced.
- Scrolling fades golden hour into evening while the hero stays on screen. The limestone "dimmer" plate on the
  right does the same by hand: drag it, click Golden hour / Evening, or Tab to it and use the arrow keys.
- The Auto-play button (bottom right) scrolls the whole page slowly. The evening picks up from wherever the
  dimmer is, and the tour pauses for a few seconds on "Come home to the view" before carrying on. Any scroll,
  swipe, key press, or click on the page hands control back. Pressing it at the end of the page restarts the visit
  like a refresh: the page reloads at the top at golden hour and plays from the beginning.
- While it plays, the button opens into a small control bar: Slow / Normal / Fast, a skip-to-next-section arrow,
  and a progress ring with the time left (it counts the evening pause still ahead). The bar tucks away after a
  few seconds; hovering, or one tap on a phone, brings it back, and a second tap pauses. Left and right arrow keys
  change the speed and the space bar pauses. Each visitor's speed is remembered for their next visit (browser storage).
  At Normal a full run takes about 2.5 minutes on a desktop; Fast about 1.7 minutes; Slow about 3.5 minutes.

Images
- Real project photos (Instagram): everything named ig-*.jpg, used in "Homes we've opened up", the product
  list and the process steps. They were upscaled and given the site's shared warm grade, nothing else.
- Enhanced from real projects (ChatGPT, keeping the architecture): hero-day.jpg, hero-evening.jpg,
  scene-open.jpg, scene-entry.jpg, scene-suite.jpg. They are labelled "image enhanced" on the page.
- Illustrative (ChatGPT, no matching real photo): mat-wood.jpg and mat-clad.jpg, labelled on the page.
- tex-marble.jpg (page background) and tex-oak.jpg (the materials band) are seamless textures generated
  in code, not photos. They tile, so any size of screen is covered.
- mat-steel.jpg is a real photo. logo-ink*.png is the official logo with the wordmark in ink for light
  backgrounds; logo*.png is the original white version used over photos.

Before launch
- Testimonials: the three quotes are placeholders, labelled on the page. Replace them in index.html
  (search for QUOTES). Placeholders are deliberately left out of the structured data.
- Unilux: the sourcing line mentions Unilux windows from Germany, taken from a Weathermaster Instagram post.
  Remove it if that should not be named.
- "Arched steel window, Vaquero" and "Setting the glass, Houston" captions come from the Instagram posts.
- The consultation form opens a pre-filled email to joe@weathermasterinc.com (Joe Hiller is listed as the
  contact on the current residential site).
- Add the street address only if the business wants it shown (search "PostalAddress").

Links
- The footer opens with a card linking to the commercial site (../commercial/). The other footer links are
  Facebook and Instagram only, and the header has no cross-link, by choice. The footer logo quietly links
  back to the selector (../); the header logo scrolls to the top. Both also work when the page is opened straight from the folder (file://).

Tested
- Phone 390x844, tablet 768x1024, laptop 1280x800 and 1440x900, and desktop 2560x1440, plus "reduce motion",
  where every section is shown in its finished state.

Hosting
- .htaccess (Apache hosts; others ignore it): sends every visit to the secure https address without "www",
  adds security headers (HSTS, a content security policy that only allows this site and Google Fonts, no framing
  by other sites, nosniff, referrer, and permissions policies), turns off folder listings, blocks README and
  hidden files, and turns on compression and long caching. If the host shows a 500 error, delete the
  "Options -Indexes" line.
