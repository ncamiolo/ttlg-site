# Through The Looking Glass Photo Booths — Site Files

This replaces the Canva site with plain HTML/CSS, ready for GitHub + Cloudflare Pages.

## What's here
- `index.html` — the whole one-page site (Hero, Services, Why Choose Us, Pricing, Reviews, FAQ, Backdrops, Contact)
- `styles.css` — styling, matching your current dark navy / gold look
- `images/` — empty folder; drop in real photos (see below)

## 1. Add your photos
`index.html` is already wired up to look for these photos in the `images/` folder. **You don't need to edit any code** — just export each photo from Canva and save it into `images/` using these exact file names (lowercase, matches what's already in the HTML):

```
images/
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

## 5. Contact form note
The form in `index.html` is set up for Netlify-style form handling (`data-netlify="true"`), which **won't work on Cloudflare Pages**. Options:
- Use [Cloudflare Pages Functions](https://developers.cloudflare.com/pages/functions/) with a small script to email submissions
- Use a third-party form service like Formspree or Web3Forms (just point the form's `action` at their endpoint)
- Simplest: remove the form and just keep the `mailto:` link
