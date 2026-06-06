# Villa Palm — Project Instructions

## What this project is
A single-page HTML website for **Villa Palm**, a private villa rental in Kalkan, Turkey. Target audience is middle-aged women booking a group holiday (6–10 guests, 7–14 nights) with family or friends.

## File structure
```
/output/index.html      — the entire website (single HTML file, all CSS and JS inline)
/images/                — all villa photos (JPEGs)
/logo/                  — white logo.jpg and colour logo.jpg used in the nav
/inspo/                 — empty (inspiration reference, not used in code)
```

## Tech stack
Plain HTML/CSS/JS — no framework, no build step, no dependencies. Open `output/index.html` directly in a browser to run locally.

## Page sections (in order)
| Section id       | Description |
|------------------|-------------|
| `#hero`          | Full-viewport autoplay video background |
| stats bar        | 4 quick-fact figures (no id) |
| `#about`         | Two-col overview — image left, text + feature list right |
| `#gallery`       | Asymmetric 6-photo grid with lightbox |
| `#bedrooms`      | 5 bedroom cards |
| `#amenities`     | 4-column icon list |
| `#area`          | Kalkan highlights + map placeholder |
| `#pricing`       | Seasonal rate table + availability calendar placeholder |
| `#reviews`       | 3 testimonial cards (dark navy background) |
| `#how-to-book`   | 4-step numbered process |
| `#faq`           | Accordion (7 questions) |
| `#contact`       | Enquiry form + contact details |
| footer           | Brand, nav links, social icons |

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
The `f_auto,q_auto` transformation lets Cloudinary serve the right format per browser. Poster fallback is `../images/outside.JPG`.

To replace the video: upload a new file to Cloudinary and swap the `<source src>` URL in the `#hero` section.

## Logos
- Over hero (transparent nav): `../logo/white logo.jpg`
- After scroll (white nav): `../logo/colour logo.jpg`
- Swap is handled by `.nav--scrolled` CSS class toggled via JavaScript on scroll.

## Images
- All photos live in `/images/` as JPEGs
- Original `.heic` files and `.MOV` video are excluded from git (see `.gitignore`) — keep locally
- To convert a new HEIC to JPEG: `sips -s format jpeg <file.heic> --out <file.jpg>`

## Placeholders still to fill
- Gallery slots 2–6 (bedroom, lounge, kitchen, terrace, pool)
- All 5 bedroom card images
- Google Map embed in `#area`
- Availability calendar widget in `#pricing`
- Real pricing figures, contact email, phone number
- Testimonial names and dates
- Footer social media links

## Git / GitHub
- Repo: https://github.com/phoebe-jarvis/villa-palm
- Branch: `main`
- To commit and push changes: `git add output/index.html && git commit -m "message" && git push`
- The `.MOV` video, `.heic` originals, and `inspo/` folder are all gitignored
