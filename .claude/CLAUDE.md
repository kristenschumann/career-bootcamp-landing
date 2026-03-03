# Leland Bootcamp Landing Pages

This repo contains landing pages for Leland's live bootcamps, deployed via GitHub Pages.

## Repo Structure

```
career-bootcamp-landing/
├── .claude/
│   ├── CLAUDE.md                ← This file
│   ├── agents/
│   │   └── landing-page-builder.md   ← Agent for building new pages
│   └── commands/
│       └── produce-landing-page.md   ← /produce-landing-page command
├── docs/                        ← Design system & reference docs
│   ├── landing-page-playbook.md      ← Colors, typography, components
│   ├── copy-guidelines.md            ← Writing rules, pricing copy, FAQ patterns
│   ├── section-catalog.md            ← Every section type with HTML snippets
│   ├── template.html                 ← Starter HTML with {{PLACEHOLDER}} tokens
│   ├── qa-checklist.md               ← Pre-launch verification checklist
│   └── deployment-guide.md           ← Repos, GitHub Pages, sync, cohort updates
├── land-your-next-job/          ← Job search bootcamp landing page
│   ├── index.html
│   └── img/
└── [future-bootcamp]/           ← Additional bootcamp pages
```

## Deployment

- **GitHub Pages:** Push to `main` → auto-deploys
- **Account:** `kristenschumann`
- **Live URL:** https://kristenschumann.github.io/career-bootcamp-landing/

## Commands

| Command | Description |
|---------|-------------|
| `/produce-landing-page` | Build a new landing page from a brief |

## Key Rules

- Single HTML file per landing page (no build tools, no frameworks)
- All CSS inline in `<style>`, all JS inline in `<script>`
- Coach photos from `leland.imgix.net`, hero/CTA images in local `img/` folder
- Coach links: base profile URL only (no `/category` suffix)
- No hourly rates on coach cards
- CTA buttons include strikethrough original price
- Discount code appears in 9+ locations per page
- Section order: Hero → Problem → Solution → Comparison → Value → Audience → Curriculum → Instructors → Testimonials → Pricing → FAQ → Final CTA
- Black overlays on photos, never green

## Cohort Updates

When launching a new cohort, see `docs/qa-checklist.md` for the full update checklist (dates, prices, discount codes, coach roster, checkout URLs).
