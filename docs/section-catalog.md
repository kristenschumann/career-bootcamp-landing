# Section Catalog — Bootcamp Landing Pages

## Section Order (Recommended)

Selling sections come first, detail sections come after:

1. **Nav** (fixed) — Logo + CTA
2. **Hero** — Value prop, countdown, trust pills
3. **Problem** — Validate pain points (gray bg)
4. **Solution** — What you'll build (white bg)
5. **Comparison** — How we stack up (white bg)
6. **Value Stack** — Everything included + price anchoring (dark bg)
7. **Audience** — Who it's for (white bg)
8. **Curriculum** — Session-by-session breakdown (gray bg)
9. **Instructors** — Coach cards linked to sessions (gray bg)
10. **Testimonials** — Social proof quotes (white bg)
11. **Pricing** — Pricing card with CTA (gray bg)
12. **FAQ** — Objection handling (white bg)
13. **Final CTA** — Last push with photo bg
14. **Sources** — Citation footnotes
15. **Footer** — Copyright
16. **Mobile Sticky CTA** — Fixed bottom bar (mobile only)

### Why This Order Works
- Problem -> Solution -> Comparison creates the "why us" narrative
- Value Stack is the emotional peak — dark bg gives it weight
- Audience reassures "is this for me?" before diving into details
- Curriculum next to Instructors connects sessions to coaches
- Pricing comes after you've built full value, not before
- FAQ handles final objections right before the last CTA

---

## Section Details

### 1. Nav
**Purpose:** Persistent branding + always-available CTA
**Background:** rgba(17, 58, 45, 0.95) with backdrop blur
**HTML pattern:**
```html
<nav>
  <div class="container">
    <a href="https://www.joinleland.com" class="logo" aria-label="Leland">
      <!-- Leland SVG logo -->
    </a>
    <a href="{{CHECKOUT_URL}}" class="btn btn-primary">Enroll Now</a>
  </div>
</nav>
```

---

### 2. Hero
**Purpose:** Hook + countdown urgency + trust stats
**Background:** Photo with black overlay (0.30 opacity)
**Key elements:** Countdown timer, h1, subheading with `<br>` rhythm, trust pills, CTA
**Rules:** No pricing, no long descriptions, max ~820px container
```html
<section class="hero">
  <div class="container">
    <div class="countdown" id="countdown">...</div>
    <h1>{{BOOTCAMP_TITLE}}</h1>
    <p>{{VALUE_PROP_3_LINES}}</p>
    <div class="trust-strip">
      <div class="trust-pill"><span class="pill-num">{{N}}</span> {{Label}}</div>
      ...
    </div>
    <div class="hero-ctas">
      <a href="#curriculum" class="btn btn-outline">See Curriculum</a>
    </div>
  </div>
</section>
```

---

### 3. Problem
**Purpose:** Validate the reader's pain, create urgency
**Background:** var(--gray-50)
**Pattern:** Lead stat + 3 pain cards in grid
```html
<section class="problem">
  <div class="container">
    <h2>{{PROBLEM_HEADLINE}}</h2>
    <p style="max-width: 640px; font-size: 1.05rem;">{{STAT_AND_CONTEXT}}<sup>1</sup></p>
    <div class="problem-grid">
      <div class="pain-card">
        <div class="pain-icon"><span class="svg-icon">{{SVG}}</span></div>
        <h3>{{PAIN_TITLE}}</h3>
        <p>{{PAIN_DESCRIPTION}}</p>
      </div>
      <!-- 2 more pain-cards -->
    </div>
  </div>
</section>
```

---

### 4. Solution
**Purpose:** Show tangible deliverables (what you'll walk away with)
**Background:** white
**Pattern:** Eyebrow + headline + numbered deliverable grid
```html
<section class="solution">
  <div class="container">
    <p class="eyebrow">What You'll Build</p>
    <h2>{{SESSION_COUNT}} sessions. Everything you need to {{OUTCOME}}.</h2>
    <div class="solution-grid">
      <div class="deliverable">
        <div class="d-num">1</div>
        <div><h3>{{DELIVERABLE_TITLE}}</h3><p>{{DELIVERABLE_DESC}}</p></div>
      </div>
      <!-- more deliverables -->
    </div>
  </div>
</section>
```

---

### 5. Comparison
**Purpose:** Position against alternatives, show value
**Background:** white
**Pattern:** Desktop table + mobile stacked cards (hidden/shown via CSS)
**Rules:** Use specific details, not just check/dash. Real competitor names and prices.

---

### 6. Value Stack
**Purpose:** Itemize everything included, drive home the deal
**Background:** var(--dark) — gives this section visual weight
**Pattern:** Grid of check items + price anchoring box
**Rules:** Price anchoring stacks vertically (total value, then regular, then discounted). Featured price is large green.

---

### 7. Audience
**Purpose:** Help reader self-identify ("this is for me")
**Background:** white
**Pattern:** 3 audience cards with icon + title + description
**Rules:** Keep audience broad, don't exclude. Show 3 different personas.

---

### 8. Curriculum
**Purpose:** Session-by-session breakdown with expandable details
**Background:** var(--gray-50)
**Pattern:** Accordion list with numbered sessions
**Rules:** Each session shows date/time, expands to description + deliverable tag.

---

### 9. Instructors
**Purpose:** Build trust through coach credentials
**Background:** var(--gray-50)
**Pattern:** 6 coach cards in 3-column grid
**Rules:** No hourly rates. Tagline = session they teach. Links to base profile (no /category suffix). 64px avatar, star rating, credential tags.

---

### 10. Testimonials
**Purpose:** Social proof from real reviews
**Background:** white
**Pattern:** 3 testimonial cards with stars, headline quote, full review, author
**Rules:** Bold headline, italic blockquote. Use reviews of coaches on the page when possible.

---

### 11. Pricing
**Purpose:** Single focused pricing card with full details
**Background:** var(--gray-50)
**Pattern:** Centered card with badge, price anchoring, discount box, feature list, full-width CTA
**Rules:** CTA button includes strikethrough price. Include cohort dates.

---

### 12. FAQ
**Purpose:** Handle remaining objections
**Background:** white
**Pattern:** Accordion, max-width 720px centered
**Rules:** 6-8 questions. Widen audience in answers. Clarify permanent vs temporary access.

---

### 13. Final CTA
**Purpose:** Last conversion push
**Background:** Photo with dark overlay (0.60 opacity)
**Pattern:** Centered h2, urgency line, CTA button with strikethrough price, reassurance
**Rules:** Mention seats left, discount code, and cohort timing.

---

### 14. Sources
**Purpose:** Citation footnotes for stats used on page
**Pattern:** Small text below footer-ish area

---

### 15. Footer
**Purpose:** Legal + brand
**Background:** var(--gray-900)

---

### 16. Mobile Sticky CTA
**Purpose:** Always-available conversion on mobile
**Pattern:** Fixed bottom bar with struck price + sale price + compact CTA button
**Rules:** Only visible at 768px and below. Hidden when hero is in viewport.
