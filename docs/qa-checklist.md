# Landing Page QA Checklist

## Pre-Launch Checks

### Content
- [ ] All coach names, photos, ratings, and review counts are current
- [ ] Coach profile links go to base URL (no category suffix like /career-development)
- [ ] No hourly rates displayed on coach cards
- [ ] Discount code is correct and appears in all 9+ locations (search for the code name)
- [ ] Prices are consistent across: comparison table, value stack, pricing card, CTA buttons, sticky CTA
- [ ] Strikethrough prices appear on CTA buttons (`<s>$OLD</s> $NEW`)
- [ ] Cohort dates are correct in: hero countdown, session dates, pricing card, pricing dates line
- [ ] "Seats Left" count is updated in: hero trust pill, pricing badge, final CTA
- [ ] All source citations (sup tags) have matching entries in Sources section
- [ ] FAQ answers are accurate for current cohort (dates, access terms, pricing)
- [ ] Checkout URL is correct (includes bootcampCohort and order URNs)

### Design
- [ ] Hero image loads and is positioned correctly (faces visible above text)
- [ ] Final CTA image loads with appropriate dark overlay
- [ ] All coach photos load (check onerror fallback initials are correct)
- [ ] No horizontal scroll on any viewport width
- [ ] Comparison table switches to card layout on mobile (≤768px)
- [ ] Mobile sticky CTA appears after scrolling past hero
- [ ] Mobile sticky CTA hidden when hero is visible
- [ ] All accordion sections expand/collapse correctly (curriculum + FAQ)
- [ ] Chevrons rotate on expand
- [ ] Countdown timer counts down to correct start date/time
- [ ] Countdown shows "Bootcamp has started!" after target time

### Links
- [ ] Nav CTA → checkout URL
- [ ] "See Curriculum" → scrolls to #curriculum section
- [ ] All 6 coach cards → correct Leland profile pages (open in new tab)
- [ ] Pricing CTA → checkout URL
- [ ] Final CTA → checkout URL
- [ ] Mobile sticky CTA → checkout URL
- [ ] Value stack CTA → checkout URL
- [ ] Footer Leland link → joinleland.com
- [ ] No broken links (run link checker)

### Responsive (test at 768px and 375px)
- [ ] Hero text readable, no overflow
- [ ] Pain cards stack to single column
- [ ] Deliverable cards stack to single column
- [ ] Coach cards stack to single column
- [ ] Audience cards stack to single column
- [ ] Testimonial cards stack to single column
- [ ] Pricing card has adequate padding on mobile
- [ ] FAQ text doesn't overflow
- [ ] Sticky CTA price and button fit on smallest screens

### Performance
- [ ] Images use imgix with w= and h= parameters for proper sizing
- [ ] Google Fonts preconnect tags present
- [ ] No external JS dependencies (vanilla JS only)
- [ ] Single HTML file, no build step required
- [ ] Page loads in under 3 seconds on 3G

### Section Order
- [ ] Hero → Problem → Solution → Comparison → Value → Audience → Curriculum → Instructors → Testimonials → Pricing → FAQ → Final CTA

---

## Cohort Update Checklist

When launching a new cohort, update these items:

1. **Countdown target date** — in JavaScript at bottom of file
2. **Session dates** — all 6 session dates in curriculum section
3. **Cohort dates** — in pricing card and pricing-dates line
4. **Discount code** — search and replace ALL instances (9+ locations)
5. **Discount amount** — update struck/sale prices if discount changes
6. **Checkout URL** — update bootcampCohort and order URNs in ALL CTA links (6+ locations)
7. **Seats left count** — update in trust pill, pricing badge, final CTA
8. **Coach roster** — verify all 6 coaches are still assigned, update if changed
9. **Coach photos/ratings** — refresh from Leland profiles
10. **Mirror to lelandcourses** — copy updated file to `/tmp/lelandcourses/land-your-next-job/index.html`
