---
description: Build a bootcamp landing page from a brief
---

# /produce-landing-page

Build a complete bootcamp landing page.

## Usage

```
/produce-landing-page [path-to-brief]
```

## What This Does

1. Reads your bootcamp brief (markdown file with bootcamp details)
2. Launches the Landing Page Builder agent
3. Produces a single HTML file following the Leland landing page design system
4. Runs QA checks against the landing page checklist
5. Writes the output to the bootcamp's production folder

## Brief Format

Create a markdown file with these sections:

```markdown
# Bootcamp Brief

## Basic Info
- **Title:** [Bootcamp name]
- **Tagline:** [Hero subheading]
- **Cohort Dates:** [Start — End, Year]
- **Schedule:** [Days of week]
- **Checkout URL:** [Full URL with URNs]

## Sessions
| # | Title | Date & Time | Coach | Deliverable |
|---|-------|-------------|-------|-------------|
| 1 | ... | ... | ... | ... |

## Coaches
| Coach | Slug | Photo ID | Rating | Reviews | Tags |
|-------|------|----------|--------|---------|------|
| ... | ... | ... | ... | ... | ... |

## Pricing
- Regular: $XXX
- Discount Code: CODE
- Discount Amount: $XX
- Sale Price: $XXX

## Competitors
| Name | Price | Key Differences |
|------|-------|-----------------|
| ... | ... | ... |

## Audience
1. **Persona 1:** Description
2. **Persona 2:** Description
3. **Persona 3:** Description

## Testimonials
[3 reviews with headline, quote, author name, role]

## Images
- Hero: [filename or description]
- Final CTA: [filename or description]
```

## Output
- Landing page HTML at specified output path
- QA report printed to console
