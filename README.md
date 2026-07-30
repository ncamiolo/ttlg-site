# Through The Looking Glass Photo Booths — Site Files

This replaces the Canva site with plain HTML/CSS, ready for GitHub + Cloudflare Pages.

## What's here
- `index.html` — the whole one-page site (Hero, Services, Why Choose Us, Pricing, Reviews, FAQ, Backdrops, Contact)
- `styles.css` — styling, matching your current dark navy / light blue look
- `robots.txt` — tells search engines they can crawl the whole site
- `sitemap.xml` — tells search engines what pages exist
- `images/` — empty folder; drop in real photos (see below)

## 6. SEO — what's already done, and what's left
Already built in:
- Descriptive `<title>` and meta description with real keywords ("photo booth rentals," "Southwest Florida")
- Open Graph + Twitter Card tags, so links shared on Facebook/iMessage/Twitter show a nice preview card
- `LocalBusiness` structured data (helps Google understand this is a local business)
- `FAQPage` structured data — this can make your FAQ answers show up directly in Google search results as an expandable list
- Clean heading structure (one H1, then H2s per section, H3s for cards) and descriptive `alt` text on every image
- `robots.txt` and `sitemap.xml` for crawlability

Two things worth doing once the site is live:
1. **Submit to Google Search Console** ([search.google.com/search-console](https://search.google.com/search-console)) — add your domain, verify ownership (Cloudflare has a simple DNS-based verification option), and submit `https://ttlgphotobooths.com/sitemap.xml`. This is what actually gets you indexed and gets you into local search results.
2. **Add a real `images/og-image.jpg`** — this is the photo used when your site link is shared on social media. Recommended size: 1200×630px, JPG. Until it's added, shared links just won't show a preview image (no error, just a blank spot).

Optional but valuable: **add a phone number and physical service address** to the `LocalBusiness` structured data block near the top of `index.html` — this significantly helps local map-pack rankings if you're comfortable listing them publicly. Ask me if you'd like this added.

## 1. Add your photos
`index.html` is already wired up to look for these photos in the `images/` folder. **You don't need to edit any code** — just export each photo from Canva and save it into `images/` using these exact file names (lowercase, matches what's already in the HTML):

```
images/
  logo.png                        (your logo, shown top-left in the header)
  hero-photo.jpg                 (circular photo in the hero section)
  service-event-booth.jpg        (photo above "Event Photo Booth Rental" card)
  service-custom-backdrops.jpg   (photo above "Custom Backdrops" card)
  service-wedding-packages.jpg   (photo above "Wedding & Event Packages" card)
  why-choose-us.jpg              (large photo in the "Why Choose Us" section)
  red-curtain.jpg
  yellow-balloons.jpg
  silver-disco.jpg
  gold-disco.jpg
  champagne-sparkle.jpg
  mermaid-sparkle.jpg
  marble-1.jpg
  marble-2.jpg
  rose-garden.jpg
  down-the-rabbit-hole.jpg
  through-the-looking-glass.jpg
  wooden-it-be-nice.jpg
  snow-place-like-home.jpg
  merry-and-bright.jpg
```

Once a file with the right name lands in `images/`, that photo will show up automatically when you open `index.html` — no further editing needed. Missing files just won't show an image (broken image icon) until you add them, so you can do this gradually.

Before saving them in, resize to roughly 1200–1600px on the longest side and compress with a free tool like [Squoosh](https://squoosh.app) — keeps the site fast to load. The hero and why-choose-us photos look best as portrait/tall crops; the service card photos look best as roughly 4:3 landscape crops.

**Logo specifically:** save it as a **PNG with a transparent background** (not JPG) if your logo has one — that way it won't show a white or colored box behind it against the dark navy header. It displays at 48px tall, so anything roughly 150–300px tall as the source file is plenty.

## 2. Push to GitHub
```bash
cd ttlg-site
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/ttlg-site.git
git push -u origin main
```
(Create the empty repo on GitHub first — no README/license, so it stays empty for this push.)

## 3. Deploy with Cloudflare Pages
1. Go to the Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
2. Authorize GitHub, pick the `ttlg-site` repo.
3. Build settings: no build command needed, just set **Output directory** to `/` (root).
4. Deploy — you'll get a `*.pages.dev` URL to confirm it works.

## 4. Point your domain at Cloudflare
1. In Cloudflare dashboard, **Add a site** → enter `ttlgphotobooths.com`.
2. Cloudflare gives you two nameservers (e.g. `xxx.ns.cloudflare.com`).
3. Go to wherever you registered the domain, find **Nameservers** / **DNS management**, and replace the existing nameservers with Cloudflare's two.
4. This can take anywhere from a few minutes to 24 hours to propagate.
5. Back in Cloudflare Pages → your project → **Custom domains** → add `ttlgphotobooths.com` (and `www.ttlgphotobooths.com` if you want both).

## 5. Contact form
The contact section now uses your HoneyBook widget embed — no setup needed, it's already wired in and will pull your live HoneyBook form styling and submission handling automatically. Submissions go straight to your HoneyBook account like they would on any other HoneyBook-embedded site.

Note: the widget loads via HoneyBook's own script (`widget.honeybook.com`), so it needs an internet connection to render — it'll show blank in any offline/local preview, but works normally once the site is live.
