# Landing Page Deployment Guide

## Repository Structure

Two repos host bootcamp landing pages:

### 1. career-bootcamp-landing (primary)
- **GitHub:** `kristenschumann/career-bootcamp-landing`
- **GitHub Pages:** https://kristenschumann.github.io/career-bootcamp-landing/
- **Structure:**
  ```
  career-bootcamp-landing/
  └── land-your-next-job/
      ├── index.html      ← The landing page
      └── img/
          ├── hero-bg.jpg
          └── handshake.jpg
  ```
- **Deploy:** Push to `main` branch → GitHub Pages auto-deploys

### 2. lelandcourses (mirror)
- **Local path:** `/tmp/lelandcourses/land-your-next-job/`
- **Purpose:** Backup/staging mirror
- **Sync:** Manual copy from career-bootcamp-landing

## Deployment Steps

### Deploying Updates
1. Edit `/tmp/career-bootcamp-landing/land-your-next-job/index.html`
2. Mirror: `cp /tmp/career-bootcamp-landing/land-your-next-job/index.html /tmp/lelandcourses/land-your-next-job/index.html`
3. Preview locally (open file in browser or use local server)
4. Commit and push career-bootcamp-landing:
   ```bash
   cd /tmp/career-bootcamp-landing
   git add land-your-next-job/index.html
   git commit -m "Update landing page: [description]"
   git push origin main
   ```
5. Verify live site at GitHub Pages URL

### Adding New Landing Pages
1. Create new folder: `career-bootcamp-landing/new-bootcamp-name/`
2. Copy `img/` folder with appropriate hero images
3. Use `template.html` from `courses/_design/landing-pages/` as starting point
4. Replace all `{{PLACEHOLDER}}` tokens
5. Test locally, then commit and push

## GitHub Pages Setup
- Deploy from `main` branch (NOT workflow-based)
- Simple static hosting, no build tools
- GitHub account: `kristenschumann`

## Architecture Notes
- **Single HTML file** per landing page — no frameworks, no build step
- All CSS is inline in `<style>` tags (no external CSS files)
- All JS is inline in `<script>` tags (no external JS)
- Coach photos served from `leland.imgix.net` (Leland's CDN)
- Hero/CTA background images are local in `img/` folder
- Google Fonts loaded via preconnect + stylesheet link
- Checkout URLs point to `joinleland.com/checkout` with bootcamp URN parameters

## Image Guidelines
- Hero images: high-quality photos, work well with black overlay
- Use `background-position: center 30%` when faces need to stay visible
- Coach photos: use imgix URLs with `?w=128&h=128&fit=crop` parameters
- Always include `onerror` fallback on coach `<img>` tags for broken images

## Keeping Repos in Sync
Both repos must contain identical `index.html` files. After any edit:
```bash
cp /tmp/career-bootcamp-landing/land-your-next-job/index.html /tmp/lelandcourses/land-your-next-job/index.html
```
Then commit and push both repos independently.
