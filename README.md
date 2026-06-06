# Villa Palm — Kalkan, Turkey

Website for Villa Palm, a private villa rental in Kalkan, Turkey. Built as a single-page HTML site.

## Running locally

No build step required. Clone the repo and open `index.html` in a browser:

```bash
git clone https://github.com/phoebe-jarvis/villa-palm
cd villa-palm
open index.html
```

## Deploying to Vercel

### First deploy
1. Install the Vercel CLI: `npm i -g vercel`
2. Run `vercel` from the project root and follow the prompts
3. Set **Output Directory** to `.` (the project root) when asked

### Subsequent deploys
```bash
vercel --prod
```

Or push to `main` — if the repo is linked to Vercel, it will deploy automatically on every push.

## Project structure

```
index.html        — the full website (HTML, CSS, JS all inline)
images/           — all villa photos (JPEGs)
logo/             — white and colour logo variants
vercel.json       — Vercel deployment config (caching headers)
output/           — legacy location of index.html (kept for reference)
CLAUDE.md         — full project notes for Claude Code sessions
```

## Hero video

Hosted on Cloudinary (excluded from git due to file size):
```
https://res.cloudinary.com/ddegrf3xo/video/upload/f_auto,q_auto/v1780751654/New_video_lw4ttt
```

To replace it: upload a new video to Cloudinary and update the `<source src>` in the `#hero` section of `index.html`.

## Images

All photos are JPEGs in `/images/`. Original `.heic` files and `.mov` video are excluded from git — keep them locally as originals.

To convert a new HEIC image:
```bash
sips -s format jpeg <file.heic> --out <file.jpg>
```
