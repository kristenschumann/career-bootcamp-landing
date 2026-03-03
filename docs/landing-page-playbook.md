# Landing Page Design Playbook

Design system guide for Leland bootcamp landing pages. Documented from the "Land Your Next Job" bootcamp page (`/tmp/career-bootcamp-landing/land-your-next-job/index.html`). All patterns here are production-tested and should be reused as-is for new bootcamp pages.

---

## Brand Colors

```css
:root {
  --dark: #113A2D;           /* Primary dark green (nav, value stack bg, badges) */
  --medium: #185440;         /* Medium green (secondary dark elements) */
  --green: #15B078;          /* Primary CTA green (buttons, accents, checkmarks) */
  --green-light: rgba(21, 176, 120, 0.08);    /* Subtle green tint (tags, discount boxes) */
  --green-lighter: rgba(21, 176, 120, 0.04);  /* Barely-there green (deliverable cards) */
  --white: #ffffff;
  --gray-50: #f9fafb;        /* Section backgrounds (problem, curriculum, pricing, instructors) */
  --gray-100: #f3f4f6;       /* Borders, table dividers */
  --gray-200: #e5e7eb;       /* FAQ item borders, card borders */
  --gray-400: #9ca3af;       /* Chevrons, muted icons, struck prices */
  --gray-500: #6b7280;       /* Secondary text, labels, dates */
  --gray-600: #4b5563;       /* Body paragraph text */
  --gray-700: #374151;       /* Table row labels */
  --gray-800: #1f2937;       /* Default body color */
  --gray-900: #111827;       /* Headings, strong text, footer bg */
}
```

### Usage rules
- Dark sections (hero, value stack, final CTA) use white text on `--dark` or photo backgrounds.
- Light sections alternate between `--white` and `--gray-50` backgrounds.
- `--green` is reserved for CTAs, checkmarks, eyebrow text, and accent elements. Never use it as a section background.
- Gold star color: `#f59e0b` (for review stars only).

---

## Typography

**Font:** Inter from Google Fonts, weights 400 (regular), 500 (medium), 600 (semibold), 700 (bold), 800 (extrabold).

```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
```

```css
body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  color: var(--gray-800);
  line-height: 1.6;
  -webkit-font-smoothing: antialiased;
}
```

| Element | Size | Weight | Line Height | Color | Letter Spacing |
|---------|------|--------|-------------|-------|----------------|
| h1 | 3rem | 800 | 1.15 | white (on dark bg) | -0.02em |
| h2 | 2rem | 700 | 1.25 | gray-900 | -0.01em |
| h3 | 1.25rem | 600 | 1.35 | gray-900 | -- |
| Body (p) | inherit | 400 | 1.6 | gray-600 | -- |
| Eyebrow | 0.8rem | 600 | -- | green | 0.08em, uppercase |

### Mobile typography (max-width: 768px)
- h1 shrinks to **2.1rem**
- h2 shrinks to **1.6rem**

### Contextual overrides
- Hero `p`: `rgba(255,255,255,0.8)`, 1.2rem, line-height 1.7
- Final CTA `h2`: 2.2rem, white
- Final CTA `p`: `rgba(255,255,255,0.7)`, 1.1rem
- Section intro `p`: 1.05rem, max-width 640px

---

## Image Treatment

### Hero section
- Black overlay at **0.30 opacity**, uniform across gradient stops.
- `background-position: center 30%` — positions faces in upper third.
- Subtle radial glow: `radial-gradient(circle, rgba(21,176,120,0.10) 0%, transparent 70%)` as `::before` pseudo-element.

```css
.hero {
  background: linear-gradient(165deg, rgba(0,0,0,0.30) 0%, rgba(0,0,0,0.30) 50%, rgba(0,0,0,0.30) 100%),
              url('img/hero-bg.jpg') center 30%/cover no-repeat;
}
```

### Final CTA section
- Black overlay at **0.60 opacity** — darker photos need more overlay to keep text readable.

```css
.final-cta {
  background: linear-gradient(165deg, rgba(0,0,0,0.60) 0%, rgba(0,0,0,0.60) 100%),
              url('img/handshake.jpg') center/cover no-repeat;
}
```

### Key rules
- **NEVER use green overlays** — black lets natural photo colors through while maintaining readability.
- Use `165deg` angle on the gradient for visual consistency.
- Hero images with faces: use `center 30%` to keep faces visible.
- General photos: use `center/cover`.

---

## Buttons

```css
.btn {
  display: inline-flex; align-items: center; justify-content: center;
  padding: 16px 32px; border-radius: 8px;
  font-size: 1rem; font-weight: 600;
  text-decoration: none; cursor: pointer; border: none;
  transition: all 0.2s;
}

.btn-primary {
  background: var(--green); color: var(--white);
}
.btn-primary:hover {
  background: #12a06a;
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(21,176,120,0.3);
}

.btn-outline {
  background: transparent; color: var(--white);
  border: 2px solid rgba(255,255,255,0.4);
}
.btn-outline:hover {
  border-color: var(--white);
  background: rgba(255,255,255,0.1);
}

.btn-lg { padding: 18px 40px; font-size: 1.1rem; }
```

### Strikethrough pricing in buttons
```css
.btn s { opacity: 0.6; font-weight: 400; margin-right: 4px; }
```
Usage: `<a class="btn btn-primary btn-lg">Enroll Now, <s>$699</s> $599</a>`

### Nav button (smaller)
```css
nav .btn { padding: 10px 24px; font-size: 0.875rem; }
```

---

## Component Patterns

### Nav (Fixed)

Fixed top bar with dark green semi-transparent background and backdrop blur.

```css
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  background: rgba(17, 58, 45, 0.95);
  backdrop-filter: blur(8px);
  padding: 16px 0;
  border-bottom: 1px solid rgba(255,255,255,0.1);
}
nav .container { display: flex; align-items: center; justify-content: space-between; }
nav .logo svg { height: 28px; width: auto; }
```

**Structure:**
- Leland SVG logo (white fill) on the left
- Single CTA button (btn-primary) on the right
- Logo links to `https://www.joinleland.com`

### Hero

Full-width photo background with black overlay. Contains countdown timer, headline, trust strip, and CTA buttons.

```css
.hero { padding: 140px 0 100px; position: relative; overflow: hidden; }
.hero .container { position: relative; z-index: 1; max-width: 820px; }
```

**Layout order:**
1. Countdown timer pill
2. `<h1>` headline
3. `<p>` subhead (use `<strong>` and `<br>` for emphasis)
4. Trust strip (flex row of pills)
5. Hero CTAs (flex row of buttons)

**Countdown timer:**
```css
.countdown {
  display: inline-flex; align-items: center; gap: 12px;
  background: rgba(21,176,120,0.15); border-radius: 100px;
  padding: 10px 20px; margin-bottom: 24px;
}
```
- Green label + units (days/hrs/min/sec) with separators
- Numbers: white, 1.1rem, 700 weight
- Labels: `rgba(255,255,255,0.5)`, 0.65rem, uppercase
- Pulse animation on the countdown dot: `opacity 1 -> 0.4 -> 1`

**Trust strip:**
```css
.trust-strip { display: flex; gap: 10px; margin-bottom: 40px; flex-wrap: wrap; }
.trust-pill {
  display: inline-flex; align-items: center; gap: 6px;
  background: rgba(21,176,120,0.12); border-radius: 100px;
  padding: 8px 16px; color: rgba(255,255,255,0.85);
  font-size: 0.85rem; font-weight: 500;
}
.trust-pill .pill-num { color: var(--green); font-weight: 700; font-size: 0.95rem; }
```

### Pain Cards (Problem Section)

Gray-50 section background. 3-column responsive grid of white cards.

```css
.problem { background: var(--gray-50); }
.problem-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 24px; margin-top: 40px;
}
.pain-card {
  background: var(--white); border-radius: 12px; padding: 28px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.06);
}
```

**Card structure:**
1. SVG icon (32x28px, green stroke, wrapped in `.svg-icon`)
2. `<h3>` at 1.1rem
3. `<p>` at 0.95rem

### Deliverable Cards (Solution Section)

White section background. 2-column responsive grid.

```css
.solution-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px; margin-top: 40px;
}
.deliverable {
  display: flex; gap: 16px; align-items: flex-start;
  background: var(--green-lighter); border-radius: 12px; padding: 24px;
}
.deliverable .d-num {
  flex-shrink: 0; width: 36px; height: 36px; border-radius: 8px;
  background: var(--green); color: var(--white);
  font-weight: 700; font-size: 0.9rem;
  display: flex; align-items: center; justify-content: center;
}
```

**Card structure:**
1. Numbered badge (green square with rounded corners, white number)
2. Flex column: `<h3>` at 1rem + `<p>` at 0.875rem

### Session Accordion (Curriculum)

Gray-50 section background. Vertical stack of expandable session cards.

```css
.curriculum { background: var(--gray-50); }
.session-list { display: flex; flex-direction: column; gap: 16px; margin-top: 40px; }
.session {
  background: var(--white); border-radius: 12px; overflow: hidden;
  box-shadow: 0 1px 3px rgba(0,0,0,0.06);
}
```

**Session header (always visible):**
- Dark numbered badge (40x40, `--dark` bg, 10px radius)
- Title (1.05rem) + date line (0.85rem, gray-500)
- Chevron SVG that rotates 180deg on open

**Session body (hidden by default):**
- Description paragraphs (0.95rem)
- Deliverable tag: inline-flex pill with `--green-light` bg, 0.85rem, 600 weight

**Toggle mechanism:** `onclick="this.parentElement.classList.toggle('open')"`

### Comparison Table

White section background. Desktop shows a full HTML table; mobile shows stacked cards.

**Desktop table:**
```css
.comparison-table { width: 100%; border-collapse: collapse; font-size: 0.9rem; min-width: 700px; }
.comparison-table thead th.highlight {
  color: var(--green);
  border-top: 3px solid var(--green);
  border-radius: 8px 8px 0 0;
}
.comparison-table td.highlight { background: rgba(21, 176, 120, 0.04); }
.comparison-table .check { color: var(--green); font-weight: 700; }
.comparison-table .dash { color: var(--gray-300); }
```

**Mobile stacked cards (below 768px):**
```css
.compare-card { background: var(--gray-50); border-radius: 12px; padding: 24px; margin-bottom: 16px; }
.compare-card.featured { background: var(--white); border: 2px solid var(--green); }
```

**Breakpoint switch:**
```css
@media (max-width: 768px) {
  .comparison-table-wrap { display: none; }
  .comparison-mobile { display: block; }
}
```

### Value Stack

Dark green section (`--dark` background). 2-column grid of check items with price anchoring.

```css
.value-section { background: var(--dark); color: var(--white); }
.value-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 16px; margin-top: 40px;
}
.value-item {
  display: flex; align-items: flex-start; gap: 14px;
  padding: 20px; border-radius: 10px;
  background: rgba(255,255,255,0.06);
}
```

**Price anchoring (vertical stack, centered):**
```css
.value-pricing-tiers { display: flex; flex-direction: column; align-items: center; gap: 4px; }
.value-tier .tier-price.struck { color: rgba(255,255,255,0.35); text-decoration: line-through; font-size: 1.2rem; }
.value-tier .tier-price.struck-med { color: rgba(255,255,255,0.45); text-decoration: line-through; font-size: 1.3rem; }
.value-tier .tier-price.featured { color: var(--green); font-size: 2.8rem; font-weight: 800; display: block; }
```

**Price tiers pattern:** Total value (struck, faintest) -> Bootcamp price (struck, slightly brighter) -> Discounted price (featured, large green). Stacked vertically, not horizontally.

**Discount code display:**
```css
.value-total .discount-note code {
  background: rgba(255,255,255,0.15); color: var(--green);
  padding: 3px 8px; border-radius: 4px; font-weight: 700;
}
```

### Coach Cards (Instructors)

Gray-50 section background. 3-column responsive grid.

```css
.instructors { background: var(--gray-50); }
.instructor-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 24px; margin-top: 40px;
}
.instructor-card {
  background: var(--white); border-radius: 8px;
  border: 1px solid #E5E5E5; padding: 20px;
  display: flex; flex-direction: column; gap: 12px;
  transition: box-shadow 0.2s, transform 0.2s;
}
.instructor-card:hover {
  box-shadow: 0 8px 24px rgba(0,0,0,0.10);
  transform: translateY(-2px);
}
```

**Card structure:**
1. 64px circular avatar (`object-fit: cover`, fallback to initials on `onerror`)
2. Name row: name (1.05rem, 700) + star rating inline (`#f59e0b` filled star SVG + count)
3. Tagline: session topic (0.85rem, gray-600, 2-line clamp)
4. Credential tags: SVG icon (briefcase for work, mortarboard for education) + text (0.8rem, gray-600)

**Key rules:**
- NO hourly rate displayed.
- Entire card is wrapped in an `<a>` link to the coach profile.
- Coach profile URL format: `https://www.joinleland.com/coach/{slug}` — no category suffix.
- Avatar images from `leland.imgix.net` with `?w=128&h=128&fit=crop` params.

### Testimonials

White section background. 3-column responsive grid.

```css
.testimonial-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 24px; margin-top: 40px;
}
.testimonial-card {
  background: var(--gray-50); border-radius: 12px; padding: 28px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.06);
}
```

**Card structure:**
1. 5 gold star SVGs in a flex row (`.star-row`)
2. Bold headline quote (`.review-headline`: 1rem, 600, gray-900)
3. Blockquote (0.95rem, italic, gray-600, line-height 1.7)
4. Author row: 40px circular avatar (initials) + name + role

### Pricing Card

Gray-50 section background. Single centered card.

```css
.pricing-card {
  max-width: 560px; margin: 40px auto 0;
  background: var(--white); border-radius: 16px; padding: 40px;
  text-align: center;
  box-shadow: 0 4px 24px rgba(0,0,0,0.08);
  border: 2px solid var(--green);
  position: relative;
}
```

**Elements:**
1. "Seats Left" badge: absolute positioned, `top: -14px`, green bg, white text, pill shape
2. Title + subtitle (dates)
3. Price anchoring: 3 columns — 1:1 coaching (struck), bootcamp (struck), with-code (green highlight)
4. Discount code box: `--green-light` bg, code in dark bg pill
5. Feature checklist: left-aligned, green checkmarks
6. Full-width CTA button with strikethrough price
7. Dates note below

**Price anchor (horizontal in pricing card):**
```css
.pricing-anchor { display: flex; justify-content: center; gap: 40px; margin: 24px 0; flex-wrap: wrap; }
.pricing-anchor .anchor-price.muted { color: var(--gray-400); text-decoration: line-through; }
.pricing-anchor .anchor-price.highlight { color: var(--green); }
```

### FAQ Accordion

White section background. Max-width 720px centered.

```css
.faq-list { max-width: 720px; margin: 40px auto 0; }
.faq-item { border-bottom: 1px solid var(--gray-200); }
.faq-q {
  display: flex; align-items: center; justify-content: space-between;
  padding: 20px 0; cursor: pointer; user-select: none; gap: 16px;
}
.faq-q h3 { font-size: 1rem; font-weight: 600; }
```

**Toggle mechanism:** Same as session accordion — `onclick` toggles `.open` class. Chevron rotates 180deg. Answer div toggles from `display: none` to `display: block`.

### Final CTA

Full-width photo background with 0.60 opacity black overlay. Centered text.

```css
.final-cta {
  text-align: center; color: var(--white); padding: 80px 0;
}
.final-cta h2 { color: var(--white); font-size: 2.2rem; margin-bottom: 12px; }
.final-cta p { color: rgba(255,255,255,0.7); font-size: 1.1rem; margin-bottom: 32px; }
.final-cta .reassurance { margin-top: 16px; font-size: 0.85rem; color: rgba(255,255,255,0.5); }
```

**Structure:**
1. Headline
2. Urgency line (seats left, date, discount code)
3. Large CTA button with strikethrough price
4. Reassurance line (recordings + refund policy)

### Mobile Sticky CTA

Fixed bottom bar that appears after scrolling past the hero on mobile.

```css
.sticky-cta {
  display: none; position: fixed; bottom: 0; left: 0; right: 0; z-index: 99;
  background: var(--white); padding: 12px 16px;
  box-shadow: 0 -2px 12px rgba(0,0,0,0.1);
  border-top: 1px solid var(--gray-200);
}
```

**Structure:** Flex row with struck original price + sale price on the left, enroll button on the right.

**Show/hide via IntersectionObserver:**
```javascript
const observer = new IntersectionObserver(([entry]) => {
  if (window.innerWidth <= 768) {
    stickyCta.style.display = entry.isIntersecting ? 'none' : 'block';
  }
}, { threshold: 0 });
observer.observe(hero);
```

Only shows at 768px and below. Final section gets extra bottom padding (100px) to avoid overlap.

### Footer

```css
footer {
  background: var(--gray-900); color: var(--gray-500);
  text-align: center; padding: 32px 0; font-size: 0.85rem;
}
footer a { color: var(--gray-400); }
footer a:hover { color: var(--white); }
```

### Sources (Footnotes)

Small text block between final CTA and footer for citation references.

```css
.sources {
  max-width: 1080px; margin: 0 auto; padding: 24px 24px 8px;
  font-size: 0.75rem; color: var(--gray-500); line-height: 1.6;
}
```

---

## Inline SVG Icons

All icons are inline SVGs (not icon fonts, not external files). Two sizes:

```css
.svg-icon { display: inline-flex; align-items: center; justify-content: center; width: 32px; height: 32px; }
.svg-icon svg { width: 28px; height: 28px; }
.svg-icon svg path, .svg-icon svg circle { stroke: var(--green); }

.svg-icon-lg { width: 36px; height: 36px; }
.svg-icon-lg svg { width: 32px; height: 32px; }
```

**Star icons (testimonials):** Filled `#f59e0b`, no stroke, 18x18px in a `.star-row`.

**Credential tag icons (instructor cards):** 14x14px, `stroke="currentColor"`, inherits gray-400 from parent. Two types:
- Briefcase icon for work experience
- Mortarboard icon for education

---

## Spacing

| Context | Value |
|---------|-------|
| Section padding | 80px top/bottom |
| Section padding (mobile) | 56px top/bottom |
| Container max-width | 1080px |
| Container horizontal padding | 24px |
| Hero container max-width | 820px |
| Hero padding | 140px top, 100px bottom |
| Card grid gap | 24px (standard), 20px (compact/deliverables), 16px (value items) |
| Session list gap | 16px |
| h2 margin-bottom | 16px |
| Grid margin-top (from heading) | 40px |
| Intro paragraph to heading | 0 (directly under h2) |
| Pricing card max-width | 560px |
| FAQ list max-width | 720px |

---

## Animations

| Animation | CSS |
|-----------|-----|
| Button hover | `transform: translateY(-1px); box-shadow: 0 4px 12px rgba(21,176,120,0.3);` |
| Card hover | `transform: translateY(-2px); box-shadow: 0 8px 24px rgba(0,0,0,0.10);` |
| Countdown pulse | `@keyframes pulse { 0%, 100% { opacity: 1; } 50% { opacity: 0.4; } }` |
| Chevron rotation | `transform: rotate(180deg);` on `.open` class, `transition: transform 0.2s` |
| All transitions | `transition: all 0.2s` (buttons), `transition: box-shadow 0.2s, transform 0.2s` (cards) |

---

## Responsive Design

**Single breakpoint:** 768px

### What changes at 768px and below:
- h1: 3rem -> 2.1rem
- h2: 2rem -> 1.6rem
- Section padding: 80px -> 56px
- Card grids: collapse to single column (via `minmax` in `auto-fit`)
- Comparison table: hidden, replaced by stacked cards
- Sticky CTA bar: appears (fixed bottom)
- Final section: gets `padding-bottom: 100px` for sticky CTA clearance

### Grid columns by component:
| Component | Desktop | Mobile |
|-----------|---------|--------|
| Pain cards | 3-col (minmax 280px) | 1-col |
| Deliverables | 2-col (minmax 300px) | 1-col |
| Value items | 2-col (minmax 260px) | 1-col |
| Audience cards | 3-col (minmax 280px) | 1-col |
| Instructor cards | 3-col (minmax 280px) | 1-col |
| Testimonials | 3-col (minmax 300px) | 1-col |

---

## Page Section Order

Standard bootcamp landing page follows this exact section flow:

1. **Nav** (fixed)
2. **Hero** (photo bg, countdown, headline, trust strip, CTAs)
3. **Problem** (gray-50 bg, pain cards)
4. **Solution** (white bg, deliverable cards)
5. **Comparison** (white bg, table/cards)
6. **Value Stack** (dark bg, check items, price anchoring, CTA)
7. **Who It's For** (white bg, audience cards)
8. **Curriculum** (gray-50 bg, session accordion)
9. **Instructors** (gray-50 bg, coach cards)
10. **Testimonials** (white bg, quote cards)
11. **Pricing** (gray-50 bg, single pricing card)
12. **FAQ** (white bg, accordion)
13. **Final CTA** (photo bg, dark overlay)
14. **Sources** (footnotes)
15. **Footer** (gray-900 bg)
16. **Mobile Sticky CTA** (fixed bottom, mobile only)

---

## JavaScript Patterns

### Countdown Timer
Targets a specific UTC datetime. Updates every second. Shows "Bootcamp has started!" after expiry.

```javascript
const target = new Date('2026-03-17T22:00:00Z'); // Convert target time to UTC
function update() {
  const diff = target - new Date();
  if (diff <= 0) { /* show expired message */ return; }
  // Calculate days, hours, minutes, seconds from diff
}
setInterval(update, 1000);
```

### Accordion Toggle
Simple class toggle via inline `onclick`:
```html
<div class="session-header" onclick="this.parentElement.classList.toggle('open')">
```
CSS handles show/hide via `.open .session-body { display: block; }`.

### Sticky CTA (IntersectionObserver)
Observes the hero section. When hero is no longer visible and viewport is 768px or less, shows the sticky CTA bar.

---

## Checkout URL Pattern

All CTA buttons link to the Leland checkout with bootcamp cohort and order URNs as query params:

```
https://www.joinleland.com/checkout?bootcampCohort=urn%3AbootcampCohort%3A%28urn%3Abootcamp%3A{BOOTCAMP_ID}%2C{COHORT_ID}%29&order=urn%3Aorder%3A{ORDER_ID}
```

Replace the three IDs for each new bootcamp cohort.

---

## Audience Cards

White section background. 3-column grid with bordered cards (unlike pain cards which have shadow only).

```css
.audience-card {
  background: var(--white); border-radius: 12px; padding: 32px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.06);
  border: 1px solid var(--gray-200);
}
```

**Card structure:** Large SVG icon -> h3 -> descriptive paragraph (0.95rem).

---

## Discount Code Box (Pricing Card)

```css
.discount-box {
  background: var(--green-light); border-radius: 10px;
  padding: 16px 24px; margin: 24px 0;
}
.discount-box code {
  background: var(--dark); color: var(--green);
  padding: 4px 10px; border-radius: 4px;
  font-weight: 700; font-size: 1rem;
}
```

---

## Quick Reference: Shadow Scale

| Use | Shadow |
|-----|--------|
| Cards at rest | `0 1px 3px rgba(0,0,0,0.06)` |
| Pricing card | `0 4px 24px rgba(0,0,0,0.08)` |
| Card hover | `0 8px 24px rgba(0,0,0,0.10)` |
| Button hover | `0 4px 12px rgba(21,176,120,0.3)` |
| Sticky CTA | `0 -2px 12px rgba(0,0,0,0.1)` |

---

## Quick Reference: Border Radius Scale

| Element | Radius |
|---------|--------|
| Buttons | 8px |
| Cards (standard) | 12px |
| Pricing card | 16px |
| Session number badge | 10px |
| Deliverable number badge | 8px |
| Instructor card | 8px |
| Pills / badges | 100px (full round) |
| Avatars | 50% (circle) |
| Discount box | 10px |
