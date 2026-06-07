# Villa Palm — Project Instructions

## What this project is
A single-page HTML website for **Villa Palm**, a private villa rental in Kalkan, Turkey. Target audience is middle-aged women booking a group holiday (6–12 guests, 7–14 nights) with family or friends.

## File structure
```
index.html          — the entire website (single HTML file, all CSS and JS inline)
images/             — all villa photos (JPEGs)
logo/               — white and colour logo variants (PNG)
vercel.json         — Vercel deployment config (cache headers for images/logo)
sitemap.xml         — XML sitemap pointing to villapalmkalkan.com
robots.txt          — allows all crawlers, references sitemap
README.md           — setup and deploy instructions
CLAUDE.md           — this file
```

## Tech stack
Plain HTML/CSS/JS — no framework, no build step, no dependencies. Open `index.html` directly in a browser to run locally.

## Page sections (in order)
| Section id     | Description |
|----------------|-------------|
| `#hero`        | Full-viewport autoplay video background |
| stats bar      | 4 quick-fact figures (no id) |
| `#about`       | Two-col overview — image left, text + feature list right |
| `#gallery`     | Asymmetric 6-photo grid with lightbox |
| `#bedrooms`    | 6 bedroom cards |
| `#amenities`   | 4-column icon list |
| `#area`        | Kalkan highlights + map image (images/map.jpg) |
| `#pricing`     | Seasonal rate table + Google Calendar embed |
| `#reviews`     | 3 testimonial cards (dark navy background) |
| `#how-to-book` | 4-step numbered process |
| `#faq`         | Accordion (7 questions) |
| `#contact`     | HubSpot enquiry form + contact details |
| footer         | Brand, nav links, social icons |

## Design tokens (CSS variables)
All colours, spacing and shadows are defined as CSS variables at the top of the `<style>` block:
- `--navy` — dark teal, primary brand colour
- `--gold` / `--gold-light` — warm sand/cream accent (currently `#e7ded0ff`)
- `--white` / `--off-white` / `--stone` — background tiers
- `--text` / `--text-muted` — body copy colours

Fonts: **Playfair Display** (headings) + **Inter** (body), loaded from Google Fonts.

## Hero video
Hosted on Cloudinary. Current URL:
```
https://res.cloudinary.com/ddegrf3xo/video/upload/f_auto,q_auto/v1780751654/New_video_lw4ttt
```
The `f_auto,q_auto` transformation lets Cloudinary serve the right format per browser.

To replace the video: upload a new file to Cloudinary and swap the `<source src>` URL in the `#hero` section.

## Logos
- Over hero (transparent nav): `logo/logowhite.png`
- After scroll (white nav): `logo/logoblue.png`
- Swap is handled by `.nav--scrolled` CSS class toggled via JavaScript on scroll.

## Images
- All photos live in `/images/` as JPEGs
- Paths in HTML are root-relative: `images/filename.jpg` (not `../images/`)
- Original `.heic` files and `.MOV` video are excluded from git (see `.gitignore`) — keep locally
- To convert a new HEIC to JPEG: `sips -s format jpeg <file.heic> --out <file.jpg>`

## Third-party integrations
- **Enquiry form**: HubSpot embed (portal `148649279`, form `fab70ec4-7751-45c5-a448-941702d2873c`)
  - Script loaded in `<head>`: `https://js-eu1.hsforms.net/forms/embed/148649279.js`
  - Rendered via `<div class="hs-form-frame" ...>` in the `#contact` section
  - Form only works on whitelisted domains — add new domains in HubSpot → Settings → Marketing → Forms
- **Availability calendar**: Google Calendar iframe embedded in `#pricing`
  - Calendar ID: `3ui8m78hrf54oi7t0f23upn4abmv0non@import.calendar.google.com`
  - Calendar must be set to **public** in Google Calendar settings

## SEO
The `<head>` includes:
- Optimised `<title>` and `<meta name="description">` targeting Kalkan villa search terms
- Open Graph and Twitter Card tags (og:image uses `images/outside.JPG`)
- JSON-LD `LodgingBusiness` structured data with images, address, amenities, and contact
- Canonical URL: `https://www.villapalmkalkan.com/`
- Sitemap reference: `/sitemap.xml`

To update the domain across all SEO tags, search for `villapalmkalkan.com` and replace globally.

## Placeholders still to fill
- Testimonial names and dates
- Footer social media links
- Phone number (currently blank in JSON-LD `"telephone"` field)

## Git / GitHub
- Repo: https://github.com/phoebe-jarvis/villa-palm
- Branch: `main`
- To commit and push: `git add index.html && git commit -m "message" && git push`
- Gitignored: `.MOV` video, `.heic` originals, `inspo/`, `output/`, `~$*` Office temp files

## Deployment
- Platform: Vercel
- Live domain: `https://www.villapalmkalkan.com`
- Config: `vercel.json` at project root (sets long-lived cache headers on `/images/` and `/logo/`)
- Pushing to `main` auto-deploys via Vercel's GitHub integration
- DNS managed via Namecheap: A record `@` → `76.76.21.21`, CNAME `www` → `cname.vercel-dns.com`
- `index.html` must stay at the project root — Vercel serves it as the entry point
