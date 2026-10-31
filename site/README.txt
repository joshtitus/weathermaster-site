WEATHERMASTER WEBSITE (selector + commercial + residential)
===========================================================
Upload everything in this folder to the root of weathermasterinc.com.

  /                 the "Choose your view" selector page (index.html + images/)
  /commercial/      the new commercial site
  /residential/     the new residential site (replaces the old WordPress residential pages;
                    remove or redirect those on the server when this goes live)

The three pages link to each other: the selector's doors open commercial/ and residential/. Each site's footer
starts with a large card linking to the other site; the rest of the footer links are Facebook and Instagram.
The only way back to the selector is the footer logo on each site (the header logo scrolls to the top). The headers stay focused on booking a consultation and don't link across.

robots.txt, sitemap.xml, and llms.txt live at the root and cover all three pages.
To preview on a computer, open index.html at the top of this folder and click either door. Links between the pages
also work when opened straight from the folder (file://).

--- Selector notes ---
Weathermaster selector page (concept)
=====================================

A replacement for the "Commercial / Residential" choice page at weathermasterinc.com.
Two frosted glass panes in one frame. Visitors wipe the fog off the glass with the mouse or a finger to see the view
behind it, and the fog slowly creeps back. Hovering a pane clears it and widens it; clicking or tapping slides it open
and goes to that site.

Upload the whole folder as is. No outside code; the only outside request is Google Fonts.

Search, AI, and accessibility (built in)
- Each page has a search-friendly title and description, a canonical address, and share previews for social and messaging apps.
- Structured data (JSON-LD in the page head) describes the business for Google and AI assistants: name, Fort Worth location,
  service area, phone, email, founding year, social profiles, and its commercial and residential divisions.
- llms.txt is a plain-language summary of the company for AI assistants. robots.txt and sitemap.xml help crawlers find the pages.
- favicon.ico and the icons in images/ show in browser tabs, bookmarks, and phone home screens.
- .htaccess (Apache hosts, which most WordPress hosts use; other hosts ignore it):
  security: sends every visit to https://weathermasterinc.com (secure, no "www"), adds security headers
  (HSTS, a content security policy that only allows this site and Google Fonts, no framing by other sites,
  nosniff, referrer, and permissions policies), turns off folder listings, and blocks README and hidden files;
  speed: compression and long caching. After uploading, open the site once over http:// and www. to check
  the redirects. If the host shows a 500 error, delete the "Options -Indexes" line (a few hosts don't allow it).
- Accessibility: skip link, labelled navigation, keyboard support for every control, visible focus, readable contrast,
  and a calm version for visitors who turn on "reduce motion".

Before launch, for the best ranking
- The canonical and share addresses assume this page lives at https://weathermasterinc.com/. If it goes somewhere else,
  search index.html for "https://weathermasterinc.com/" and update it (also in sitemap.xml and llms.txt).
- robots.txt, sitemap.xml, and llms.txt belong at the root of weathermasterinc.com (one copy for the whole site).
- Add the site to Google Search Console and submit sitemap.xml. Keep the Google Business Profile's name, phone, and city
  matching the page exactly.
- Add the street address to the structured data and footer if the business wants it shown (search "PostalAddress").

Links
- The Commercial pane opens /commercial/ and the Residential pane opens /residential/ (both in this upload).

Images
- images/commercial.jpg and images/residential.jpg are the views. Each has a matching -frost.jpg (a blurred,
  milky copy) that is drawn as the fog. If you replace a view, also replace its frost copy, or ask for it to be rebuilt.
- residential.jpg is the same real Weathermaster home as the residential hero, at golden hour (enhanced from an
  Instagram photo with ChatGPT; residential/images/hero-day.jpg is the full version).

commercial.jpg is AI generated and illustrative.
