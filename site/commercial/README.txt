Weathermaster Commercial landing page
=====================================

Upload this whole folder to your web host as is. index.html expects the images/ folder next to it.
The footer opens with a card linking to the residential site (../residential/). The other footer links are
Facebook and Instagram only. The footer logo quietly links back to the selector (../); the header logo
scrolls to the top. Both also work when the page is opened straight from the folder (file://).
The page has no outside code dependencies: all animation is built in, so nothing breaks if a CDN goes down.
The only outside request is Google Fonts.

Before launch
- Testimonials: the three quotes are placeholders, labeled on the page. Replace them in index.html (search for QUOTES).
  Real reviews can also be added to the structured data once you have them; placeholders are deliberately left out of it.
- Consultation form: it opens a pre-filled email to joe@weathermasterinc.com. Swap in a real form service if you want submissions collected.

Auto-play
- The Auto-play button (bottom right) scrolls the page slowly and pauses for each film until it finishes. Visitors start
  it themselves; pulling the window cord no longer starts it, so people can play with the shade.
- Any scroll, swipe, key press, menu link, or opening a service or FAQ hands control back.
- Pressing it at the end of the page restarts the visit like a refresh: the page reloads at the top, the shade closes
  again and the tour plays from the beginning.
- While it plays, the button opens into a small control bar: Slow / Normal / Fast, a skip-to-next-section arrow,
  and a progress ring with the time left (it counts the films and pauses still ahead). The bar tucks away after a
  few seconds; hovering, or one tap on a phone, brings it back, and a second tap pauses. Left and right arrow keys
  change the speed and the space bar pauses. Each visitor's speed is remembered for their next visit (browser storage).
  At Normal a full run takes about 2.5 minutes on a desktop; Fast about 1.7 minutes; Slow about 3.5 minutes.

The robot film (the "No crane needed" section)
- images/lift/robot-film.mp4 (2.5 MB, 20 s) with a WebM backup (0.9 MB). It starts playing once the section fills the screen
  and the page has stopped moving, and pauses when visitors scroll away. It plays once per visit to the section.
- The progress bar under the captions is also a scrubber: click or drag it to jump, or Tab to it and use the arrow keys.
- On phones the video pans sideways to follow the robot. The path is tuned to this clip (the CX list in index.html), so a new
  clip needs that path rebuilt.
- poster.jpg shows until it starts; end.jpg is the still shown to visitors who turn on "reduce motion".
- A "Play video" button appears only if a phone blocks auto-play (battery or data saver).
- To replace it, swap in a new robot-film.mp4 (and .webm) with the same names, and bump the ?v=2 on the four lift file links
  in index.html so returning visitors don't see a cached copy.

The entrance film (the section before the consultation form)
- images/entry/entry-film.mp4 (10 s) with a WebM backup: the closed doors slide open and the camera glides into the lobby.
- It plays once when the section is on screen and the page has stopped moving, then shows the caption and a down arrow.
  It replays only when the page is reloaded.

Search, AI, and accessibility (built in)
- Each page has a search-friendly title and description, a canonical address, and share previews for social and messaging apps.
- Structured data (JSON-LD in the page head) describes the business for Google and AI assistants: name, Fort Worth location,
  service area, phone, email, founding year, social profiles, the ten commercial services, and the six FAQ answers (eligible for rich results).
- llms.txt is a plain-language summary of the company for AI assistants. robots.txt and sitemap.xml help crawlers find the pages.
- favicon.ico and the icons in images/ show in browser tabs, bookmarks, and phone home screens.
- .htaccess (Apache hosts, which most WordPress hosts use; other hosts ignore it):
  security: sends every visit to https://weathermasterinc.com (secure, no "www"), adds security headers
  (HSTS, a content security policy that only allows this site and Google Fonts, no framing by other sites,
  nosniff, referrer, and permissions policies), turns off folder listings, and blocks README and hidden files;
  speed: compression and long caching. After uploading, open the site once over http:// and www. to check
  the redirects. If the host shows a 500 error, delete the "Options -Indexes" line (a few hosts don't allow it).
- Accessibility: skip link, labelled navigation, keyboard support for every control (including the window cord: Tab to it and press Enter), visible focus, readable contrast,
  and a calm version for visitors who turn on "reduce motion".

Before launch, for the best ranking
- The canonical and share addresses assume this page lives at https://weathermasterinc.com/commercial/. If it goes somewhere else,
  search index.html for "https://weathermasterinc.com/commercial/" and update it (also in sitemap.xml and llms.txt).
- robots.txt, sitemap.xml, and llms.txt belong at the root of weathermasterinc.com (one copy for the whole site).
- Add the site to Google Search Console and submit sitemap.xml. Keep the Google Business Profile's name, phone, and city
  matching the page exactly.
- Add the street address to the structured data and footer if the business wants it shown (search "PostalAddress").

Swapping images
- images/tex-concrete.jpg is the dark poured-concrete page background, a seamless texture generated in code.
- images/logo.png is the official logo from weathermasterinc.com, used in the intro, the header, and the footer.
- Images are progressive JPGs, which every browser and phone can show. Replace any file in images/ with a new one of the same name.
- All images share one color grade. New images will look most at home if they're golden hour or dusk.
- tower-1.jpg and tower-2.jpg are the same building before and after, lined up for the wipe. Replace them as a pair.
- hero-closed.jpg and hero-open.jpg must stay pixel aligned, and the painted pull cord was removed from both. Keep the pair together if you replace them.

Tested
- Phone 390x844, tablet 768x1024, laptop 1280x800 and 1440x900, and desktop 1920x1080 and 2560x1440.
- Visitors who turn on "reduce motion" get a calm version with every section shown in its finished state.

Imagery
- Real project photos (from Weathermaster's Instagram): the "Landmarks we've glazed" section (pj-*.jpg), real-robot.jpg,
  real-crew.jpg, and the curtain wall and high rise service photos.
- The other images and both films are AI generated and illustrative.
