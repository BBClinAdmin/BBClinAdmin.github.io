# Handoff: Boulder Biologics — Website Redesign

A complete, production-ready static-HTML redesign of `boulderbiologics.com` — 22 pages, schema-rich, regulatory-aligned, ready to deploy. This document is self-sufficient: a developer who wasn't in the design conversation can implement and deploy from this README alone.

## Overview

Boulder Biologics is a physician-led clinic in Boulder, Colorado offering autologous orthobiologic therapy, PRP, regenerative medicine, and longevity care. The redesign delivers:

- **Cellular-therapy service pages** (orthopedic + investigational systemic indications) aligned to FDA-guidance language verbatim from the live site
- **Patient education hub** with three long-form explainers + a clinician-leaning MSC science deep-dive (E-E-A-T anchor content)
- **Physician bio page** with full Schema.org `Physician` markup
- **PRP family of service pages** with full `MedicalProcedure` + `FAQPage` schema
- **A standardized footer disclaimer** rolled out across all cellular-therapy-adjacent pages
- **Clean URL slugs** replacing the live site's `/stem-cell-therapy`, `/stem-cell-therapy-3`, `/stem-cell-therapy-4`, with a 301 redirect plan in `REDIRECTS.md`
- **Comprehensive structured data** — `MedicalBusiness`, `Physician`, `MedicalProcedure`, `MedicalScholarlyArticle`, `FAQPage`, `BreadcrumbList` — covering every production page

## About the design files

**These files ARE production HTML, not mockups.** The pages in `pages/` are deploy-ready static HTML+CSS. There is no compilation step. There is no framework dependency. They can be uploaded as-is to any static host (Netlify, Vercel, Cloudflare Pages, S3, Apache, nginx) and served immediately.

**Two valid paths forward:**

1. **Static deploy.** Upload `pages/`, `assets/`, and `colors_and_type.css` to any web host. Set up the 301 redirects per `REDIRECTS.md`. Add a `sitemap.xml`. Submit to Google Search Console. Done.

2. **Framework reimplementation.** If the deployment target is a CMS or framework (Squarespace, WordPress, Webflow, Next.js, Astro, etc.), recreate the pages in that environment using the existing patterns. Preserve the structure, the schema, and — non-negotiably — the voice and regulatory framing. See "Critical non-negotiables" below.

The original project is in a separate workspace; everything you need to deploy or reimplement is in this folder.

## Fidelity

**High-fidelity / production.** Final colors, typography, spacing, copy, schema, and regulatory framing are all final. No placeholders for design decisions. The few placeholders that DO exist (headshot for Dr. Glowney, expanded publications list, BMAC explainer article) are explicitly flagged in the markup with `placeholder-note` blocks.

## Critical non-negotiables

**Read `PROJECT_GUIDELINES.md` in full before editing any patient-facing content.** The short version:

### 1. boulderbiologics.com is the source of truth for regulatory copy

Every page that discusses cellular therapy pulls regulatory language verbatim from the live site. These passages appear in the markup wrapped in `.reg-verbatim` blocks with a cream-yellow background and a `[REG]`-style label. **Do not paraphrase, soften, or "improve" verbatim regulatory passages.** If a future content edit requires reworking one of these passages, pull the equivalent language from the live site first.

The single most-protective verbatim sentence on the site:

> "At Boulder Biologics, we use autologous stem cells only."

This appears in:
- The `.footer-disclaimer` block on every cellular-therapy-adjacent page
- The hero / "What it is" section on `cellular-therapy.html`
- The full regulatory disclosure on `long-covid.html`, `tbi-cte.html`, `medical-applications-other.html`
- All three Learn explainers

**Removing or weakening this sentence breaks the site's regulatory posture.** Don't.

### 2. The two-register copy rule

| Register | Where it lives | Editorial freedom |
|---|---|---|
| **Regulatory / FDA-adjacent** | `.reg-verbatim` blocks, footer disclaimers, "Regulatory Disclosure" sections | **Copy verbatim from live site.** Do not edit for voice. |
| **Patient-facing clinical** | Body copy, FAQs, headings, hero ledes | Softened from live site for readability. Editable for voice. |

### 3. Lexicon guard-rails

| Use | Avoid |
|---|---|
| "autologous biologic therapy" | "stem cell cure" |
| "patient-derived" | "regrowth guaranteed" |
| "mesenchymal stromal cell" | "miracle" |
| "may support endogenous repair" | "reverse aging" (without context) |
| "image-guided" | "cell replacement" (unless precisely meant) |
| "FDA-guidance aligned" | "FDA approved" (unless naming specific approved product + indication) |
| "investigational" | "proven" / "cure" |

### 4. Voice

Plain, clinical, slightly understated. Confident but not boastful. Short declarative sentences. Avoid: writerly meta-commentary headings, rhetorical triplets, colloquialisms ("no pressure," "is for you"), invented statistics, AI-slop tropes (gradient backgrounds beyond the one logo gradient, emoji, decorative SVG illustrations of medical concepts).

## Page inventory

22 production HTML pages. URLs are the canonical slugs the site deploys at.

### Hub pages
| File | URL | Purpose |
|---|---|---|
| `index.html` | `/` | Homepage |
| `learn.html` | `/learn` | Patient education hub (Article cards + about block) |
| `faq.html` | `/faq` | Full FAQ (57 Q&A; FAQPage schema) |
| `fda-guidelines.html` | `/fda-guidelines` | Canonical regulatory page (HCT/P, 21 CFR 1271, minimal manipulation) |
| `contact.html` | `/contact` | Location + intake form |
| `facilities.html` | `/our-clinic` | Lab + clinic walkthrough |

### Service pages — orthopedic cellular therapy
| File | URL | Purpose |
|---|---|---|
| `cellular-therapy.html` | `/cellular-therapy` | Bone marrow cellular therapy (BMAC) for orthopedic indications |

### Service pages — investigational systemic indications
| File | URL | Purpose |
|---|---|---|
| `long-covid.html` | `/long-covid` | Investigational autologous biologic for post-COVID conditions |
| `tbi-cte.html` | `/tbi-cte` | Investigational autologous biologic for post-traumatic neurological symptoms |
| `medical-applications-other.html` | `/medical-applications-other` | Pulmonary/cardiac/GI/neuro investigational indications |

### Service pages — PRP family
| File | URL | Purpose |
|---|---|---|
| `prp.html` | `/prp` | Platelet-Rich Plasma — the main PRP page |
| `prp-ha.html` | `/prp-ha` | PRP + Hyaluronic Acid for knee OA |
| `prp-protein.html` | `/prp-protein` | PRP + Protein-Rich Plasma (A2M) for knee OA |
| `prp-hydrodissection.html` | `/prp-hydrodissection` | LD-PRP + PPP hydrodissection for nerve entrapment |
| `prolotherapy.html` | `/prolotherapy` | Dextrose prolotherapy for SI joint, ligamentous laxity |
| `epat.html` | `/epat` | EPAT (extracorporeal pulse activation / shockwave) |

### Service pages — longevity
| File | URL | Purpose |
|---|---|---|
| `longevity.html` | `/longevity` | Healthspan medicine — epigenetics, hormones, cardiometabolic, cognition |

### Patient education explainers (Learn hub)
| File | URL | Purpose |
|---|---|---|
| `is-stem-cell-therapy-fda-approved.html` | `/is-stem-cell-therapy-fda-approved` | High-volume defensive search target |
| `autologous-vs-donor-derived-stem-cells.html` | `/autologous-vs-donor-derived-stem-cells` | Regulatory + positioning explainer |
| `mesenchymal-stromal-vs-stem-cells.html` | `/mesenchymal-stromal-vs-stem-cells` | Terminology shift explainer |
| `msc.html` | `/mesenchymal-stem-cells-mscs` | Clinician-leaning deep dive on MSC biology |

### Team
| File | URL | Purpose |
|---|---|---|
| `jason-glowney-md.html` | `/jason-glowney-md` | Founder bio with Physician JSON-LD |

## CSS architecture

Three CSS files in `pages/`, plus one design-token file in the root:

| File | Loaded by | Purpose |
|---|---|---|
| `colors_and_type.css` | (via `_shared.css` / `_v2-service.css`) | Root design tokens — color palette, semantic aliases, font stacks, spacing scale, radii, shadows, motion |
| `pages/_shared.css` | `faq.html` (and any future shared-chrome page) | Header, footer, common UI chrome |
| `pages/_v2-service.css` | All service + Learn + bio pages | Service-page scaffolding, hero variants, footer disclaimer styles, navy footer |
| `pages/_learn-explainer.css` | The 3 Learn explainer pages | Shared explainer-specific styles: TOC card, direct-answer card, definition rows, verbatim regulatory blocks |

**No build step.** No PostCSS, no Sass, no JS bundler. Plain CSS that references the design tokens via CSS custom properties.

### Tokens you'll find in `colors_and_type.css`

- **Color scales:** `--bb-teal-100` through `--bb-teal-700`, `--bb-blue-400` through `--bb-blue-700`, `--bb-navy-500/600/900`, `--bb-bone-50/100`, `--bb-stone-200/300`
- **Semantic aliases:** `--color-bg`, `--color-fg`, `--color-fg-muted`, `--color-fg-subtle`, `--color-divider`, `--color-accent`
- **Brand gradient:** `--brand-gradient` — teal → blue → navy linear gradient (used at most twice per page, never on cards or under body copy)
- **Type:** `--font-display` (Montserrat), `--font-body` (Source Sans 3), `--font-serif` (Source Serif 4), `--font-mono` (IBM Plex Mono) — all from Google Fonts
- **Spacing:** `--space-1` (4px) through `--space-10` (128px), 4-pixel base grid
- **Radii:** `--r-md` (8px), `--r-lg` (14px), `--r-xl` (20px), `--r-pill` (999px)
- **Shadows:** `--shadow-xs` through `--shadow-xl`, navy-tinted (never neutral black)
- **Motion:** `--ease` = `cubic-bezier(0.2, 0.7, 0.2, 1)`, `--dur` = `220ms`

## Schema strategy

Every production page has Schema.org JSON-LD in `<head>` as a single `<script type="application/ld+json">` block containing an `@graph` array.

| Schema type | Where it appears | Purpose |
|---|---|---|
| `MedicalBusiness` | `index.html` | Anchor entity for the clinic (with `medicalSpecialty`, `address`, `telephone`, `sameAs`) |
| `Physician` | `index.html`, `jason-glowney-md.html` | Dr. Glowney's entity with credentials, alumni, affiliations |
| `MedicalProcedure` | All service pages | Per-procedure: alternateName, bodyLocation, indication, performer, legalStatus |
| `MedicalScholarlyArticle` | All Learn explainers + `msc.html` | Patient education articles with Glowney author |
| `CollectionPage` | `learn.html` | Hub with `hasPart` listing all child explainers |
| `FAQPage` | `faq.html` (57 Q&A), `prp.html`, `prp-ha.html`, `prp-protein.html`, `prp-hydrodissection.html`, `prolotherapy.html`, `epat.html`, `cellular-therapy.html`, `longevity.html` | Question/answer structured data |
| `BreadcrumbList` | Every production page | URL hierarchy |
| `WebSite` | `index.html` | Site-wide entity reference |

**If reimplementing in a framework:** the JSON-LD must be preserved or regenerated identically. The schema is doing real SEO + LLM-extraction work; don't drop it. Most frameworks have idiomatic ways to emit `<script type="application/ld+json">` — Next.js: `<Head>` or `next/head`, Astro: a `<script>` tag in `<head>`, etc.

**Investigational vs. approved pages:**
- `long-covid.html`, `tbi-cte.html`, `medical-applications-other.html` deliberately have `"legalStatus": "Investigational..."` in their `MedicalProcedure` and do NOT have `FAQPage` schema. This is intentional — we don't want investigational-indication FAQs surfacing in search results as if they were approved-treatment Q&A.

## Deployment plan

See `REDIRECTS.md` for the full plan. Summary:

### Redirects required (301)

| Old (live) URL | New URL |
|---|---|
| `/stem-cell-therapy` | `/long-covid` |
| `/stem-cell-therapy-3` | `/tbi-cte` |
| `/stem-cell-therapy-4` | `/medical-applications-other` |
| `/fda-guidlines` (typo fix) | `/fda-guidelines` |

### New URLs (sitemap-only)

- `/learn`, `/is-stem-cell-therapy-fda-approved`, `/autologous-vs-donor-derived-stem-cells`, `/mesenchymal-stromal-vs-stem-cells`, `/jason-glowney-md`

### Steps on deployment day

1. Apply the 4 redirects per `REDIRECTS.md` (host-specific syntax included for Squarespace, Wix, WordPress, nginx, Apache, Netlify/Vercel)
2. Build and submit a sitemap.xml that includes ALL new URLs (both redirected and net-new), and OMITS the old `/stem-cell-therapy*` URLs
3. Submit each new URL for indexing in Google Search Console
4. Verify each redirect with `curl -I` — confirm `301` status and correct `Location:` header
5. Audit any GMB profile / external backlinks pointing to old URLs
6. Set up a 404 monitoring alert in Search Console

## Open items / placeholders

These are explicitly flagged in markup with `.placeholder-note` blocks. Fill in when source material is available:

### High-priority
1. **Dr. Glowney headshot** — `jason-glowney-md.html` uses a 4:5 striped placeholder. Drop a JPG/PNG into `assets/` and update the `.bio-photo` div to use it as an `<img>`.
2. **Publications & talks list** on `jason-glowney-md.html` — flagged section needs peer-reviewed publications, invited talks, podcast appearances, professional society memberships, and teaching appointments.

### Medium-priority
3. **"What is BMAC?" article** — `learn.html` has a placeholder card (Article 04 · Coming soon). When Glowney source material is ready, build using the same `_learn-explainer.css` pattern as the other three explainers.

### Site-wide imagery
The pages use striped SVG placeholders with monospace captions (`<div class="img-slot" data-label="...">`) where photography hasn't been delivered. These should be replaced with real clinical photography per the project's image direction (warm-cool balanced, lightly desaturated, sharp — never moody or "luxury wellness").

## Layout & spacing rules (for reimplementation)

If reimplementing in a framework, preserve these layout patterns:

- **Generous vertical rhythm:** 64–128px between major sections on desktop
- **Content density:** 16–24px within cards
- **Page-wide max-width:** `var(--max)` = 1240px (homepage) or 1280px (most other pages)
- **Editorial column max-width:** ~880px for long-form articles (explainers + bio)
- **Hero grids:** 1.2fr-1.3fr / 1fr split for content vs. sidebar
- **Footer disclaimer:** standardized `<aside class="footer-disclaimer">` above the legal strip on every cellular-therapy-adjacent page (do NOT include on `longevity.html` — that page is not cellular-therapy adjacent)

## Interactions & states

The site is mostly static. JavaScript is minimal:

- **Forms:** vanilla `onsubmit` handlers that prevent default and change button label to "Request received ✓". These are demos — wire to your actual backend / Formspree / etc.
- **`<details>` accordions:** native HTML `<details>`/`<summary>` for FAQ. No JS needed.
- **No SPA routing.** Each page is a separate HTML document. Internal links use relative `.html` paths today; on deploy these should map to the clean canonical URLs.

States are CSS-only:
- **Hover:** color step up + 220ms transition
- **Focus:** 3px teal halo at 35% alpha
- **Active:** subtle 1px translate-Y
- **Press / nav-current:** `aria-current="page"` on active nav link with teal color

## Voice & content rules

`PROJECT_GUIDELINES.md` (in this folder, originally the project's `CLAUDE.md`) is the canonical source. Highlights:

- "We" = the clinic; "you" = the patient; "Dr. Glowney" for clinical action
- Acronyms (PRP, BMAC, MSC, EPAT, CTE) spelled out on first reference per page
- Sentence-case headlines, **except**: the BOULDER BIOLOGICS wordmark and high-emphasis service banners
- Eyebrows / kickers use UPPERCASE with `letter-spacing: 0.16em`
- No emoji, anywhere. Ever.
- No invented outcome percentages. No before/after marketing for cellular therapy.
- Testimonials, when used, need inline disclaimers ("individual results; experimental approach; not FDA-approved for this indication")

## Files in this handoff

```
design_handoff_boulder_biologics_site/
├── README.md                           ← this file
├── PROJECT_GUIDELINES.md               ← voice + regulatory rules (originally CLAUDE.md)
├── REDIRECTS.md                        ← 301 plan + deploy checklist
├── colors_and_type.css                 ← design tokens
├── assets/
│   └── logo-stacked.png                ← master stacked logotype
├── screenshots/                        ← reference captures (7 key pages)
│   ├── README.md                       ← what each screenshot shows
│   ├── 01-homepage.png
│   ├── 02-cellular-therapy.png
│   ├── 03-learn-hub.png
│   ├── 04-learn-fda-approved.png
│   ├── 05-glowney-bio.png
│   ├── 06-long-covid.png
│   └── 07-faq.png
└── pages/
    ├── _shared.css                     ← shared chrome (header, footer, common UI)
    ├── _v2-service.css                 ← service-page scaffolding + footer disclaimer
    ├── _learn-explainer.css            ← explainer-page styles (TOC, direct-answer, verbatim blocks)
    ├── index.html                      ← homepage
    ├── learn.html                      ← patient education hub
    ├── faq.html                        ← full FAQ
    ├── fda-guidelines.html             ← canonical regulatory page
    ├── contact.html
    ├── facilities.html
    ├── cellular-therapy.html
    ├── long-covid.html
    ├── tbi-cte.html
    ├── medical-applications-other.html
    ├── msc.html                        ← MSC science deep-dive
    ├── longevity.html
    ├── prp.html
    ├── prp-ha.html
    ├── prp-protein.html
    ├── prp-hydrodissection.html
    ├── prolotherapy.html
    ├── epat.html
    ├── is-stem-cell-therapy-fda-approved.html
    ├── autologous-vs-donor-derived-stem-cells.html
    ├── mesenchymal-stromal-vs-stem-cells.html
    └── jason-glowney-md.html
```

## Quick-start: deploy as static site (5 minutes)

1. Drop the `pages/` folder, `assets/` folder, and `colors_and_type.css` onto any static host (Netlify drag-and-drop, S3 upload, Vercel `vercel deploy`, etc.)
2. Configure the host to serve `pages/index.html` at `/`, and map each `.html` file to its canonical URL (most hosts do this automatically; for Netlify a `_redirects` file handles it, syntax in `REDIRECTS.md`)
3. Apply the 4 redirects in `REDIRECTS.md`
4. Build a `sitemap.xml` listing all new URLs and submit to Google Search Console + Bing Webmaster Tools

That's the floor. Subsequent improvements (CDN, image optimization, web vitals tuning, custom fonts hosted locally) layer on top.

## Reimplementation: notes for framework dev

If you're moving this to Next.js / Astro / Webflow / Squarespace / etc.:

- **Each `.html` file becomes one route.** No SPA shell needed — the site is content-heavy, not interactive.
- **Layouts:** the header/nav/footer pattern is identical across pages. Extract once as a layout component.
- **The three CSS files** can stay as-is (load them in your root layout) OR be ported to your styling system. If porting, preserve the design tokens (`colors_and_type.css`) faithfully — they are the brand.
- **JSON-LD blocks** must be preserved per-page. Render them server-side or at build time (not client-side — search engines and LLMs scrape the source HTML).
- **Forms** are placeholder; wire `<form class="cta-form">` and `<form class="final-cta__form">` to your backend / Formspree / Mailchimp / etc.
- **Internal links** use `.html` extensions today; rewrite to clean URLs on the destination platform.

Everything else — the voice, the regulatory framing, the schema, the content structure — must be preserved 1:1.

## Questions or revisions

If anything in this handoff needs clarification, the original project workspace has the full conversation history and ongoing maintenance hooks. The most opinionated piece — the regulatory voice — is also the most important to preserve. When in doubt, default to **softer, more conservative copy** and **more verbatim live-site language**, never the reverse.
