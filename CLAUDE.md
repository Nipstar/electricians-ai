# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Marketing website for **AI for Electricians** — a UK-wide industry vertical site from Antek Automation, specialising in AI voice agents, chatbots, and workflow automation specifically for electricians and electrical contractors.

**Live domain:** aiforelectricians.co.uk

**Note:** The repository folder is named "aiforelectricians.co.uk" and README.md currently references an older location-based site. This is a UK-wide industry vertical (not a location satellite), targeting electricians nationwide.

## Tech Stack & Build

- **Zero build step.** No frameworks, no bundler, no package manager, no dependencies.
- Single `index.html` (~2400 lines) containing all HTML, CSS (inline `<style>`), and JS (inline `<script>`).
- Vanilla JS only — no libraries.
- Google Fonts loaded via `<link>` (Sora for headings, DM Sans for body text).
- To develop: open `index.html` in a browser. Any static file server works (e.g. `python3 -m http.server`).

## Architecture

### index.html Structure

The file is organised in this order:

1. **`<head>`** — meta tags, Open Graph, JSON-LD structured data (ProfessionalService, Organization, FAQPage with 12 electrician-focused FAQs), CSS custom properties in `:root`, all CSS
2. **`<body>` HTML sections** (each with a distinct `id`): `hero`, `pain-points`, `services`, `demo`, `how-it-works`, `industries`, `why-us`, `faq`, `contact`
3. **About micro-section** — electrician/LLM-optimised blurb after the main content with dense semantic keywords for the electrical trade
4. **Footer** — with links to `privacy-policy.html`, `terms.html`, and satellite location sites
5. **Cal.com embed script** — lazy-loaded via IntersectionObserver
6. **Main JS IIFE** — mobile nav toggle, scroll-reveal animations, waveform bar generation, FAQ accordion (single-open), animated stat counters, contact form submission

### CSS Design System

All colours and fonts are defined as CSS custom properties in `:root` (line ~157). The theme is dark with blue/cyan accents:
- `--bg-primary: #0a0f1c`, `--accent-primary: #3b82f6`, `--accent-secondary: #06b6d4`
- CTA colour: `--accent-cta: #10b981` (green)
- Sections are commented with `/* ── SECTION NAME ── */` markers

### JavaScript Features

All JS lives at the bottom of `index.html` in two `<script>` blocks:
- **Cal.com loader** (~line 2176): lazy-loads the booking widget when the embed container scrolls into view
- **Main JS** (~line 2200+): IIFE containing mobile nav, IntersectionObserver-based scroll reveal (`.reveal` → `.visible`), waveform animation bars, FAQ accordion, counter animation with ease-out cubic, and contact form POST

### Contact Form

The form POSTs JSON to an **n8n webhook** endpoint. Fields: name, email, phone, business, message, source, industry (set to "Electrician"). Includes a honeypot field (`website`) for spam filtering.

Webhook URL: `https://antekauto.app.n8n.cloud/webhook/29e3a09b-5b23-489b-a800-a07262afb4cb`

### Other Pages

- `privacy-policy.html` and `terms.html` — standalone pages with duplicated CSS (same design system, self-contained), updated for AI for Electricians branding

## SEO Considerations

- Semantic HTML5 with proper heading hierarchy
- Three JSON-LD blocks in `<head>`: **ProfessionalService** (not LocalBusiness — UK-wide, not location-specific), Organization, FAQPage with 12 electrician-focused FAQs
- Open Graph + Twitter Card meta tags on every page
- `robots.txt` allows all crawlers; `sitemap.xml` lists the homepage
- Target keywords are woven into copy — preserve keyword density when editing text:
  - **Primary:** "ai for electricians", "ai voice agents for electricians", "ai answering service for electricians"
  - **Services:** EICR, EV charger, consumer unit, rewire, PAT testing, fixed wire testing, emergency callout
  - **Certifications:** NICEIC, NAPIT, Part P, BS 7671, 18th Edition
  - **Business types:** sole trader electrician, domestic electrician, commercial electrical contractor, emergency electrician, EV charger installer, testing & inspection specialist, solar installer, multi-van electrical firm
- The about micro-section before the footer is specifically optimised for LLM/GEO visibility with dense electrician-specific semantic keywords
- **UK English spelling** throughout (specialise, organised, colour, labour, centre)

## Industry Vertical Focus

This site targets the UK electrical trade nationwide. It is **not** a location satellite. Content references:
- Electrician business types (sole traders, domestic, commercial, emergency, EV, testing, solar, multi-van)
- Electrical services (rewires, consumer units, EICRs, PAT testing, EV chargers, fire alarms, solar PV, emergency callouts)
- Electrical scenarios ("up a ladder", "working in a live panel", "mid-first-fix", "11pm emergency callout")
- Industry certifications (NICEIC, NAPIT, Part P, BS 7671, 18th Edition)

The footer includes links to location-specific satellite sites (Hampshire, Portsmouth, Andover, Southampton, Basingstoke, Winchester, Farnborough) but the main content is UK-wide.

## Key Conventions

- All CSS and JS are inline — there are no external `.css` or `.js` files
- CSS sections are delimited by `/* ── SECTION NAME ── */` comment blocks
- HTML sections are delimited by `<!-- ═══ SECTION NAME ═══ -->` comment blocks
- The `.reveal` class + IntersectionObserver pattern is used for scroll animations — add `class="reveal"` to any new element that should animate in
- Responsive breakpoints are handled via `@media` queries within the single `<style>` block
- FAQ section contains exactly **12 items** (not 16 or 18) — all electrician-focused, matching the JSON-LD FAQPage schema

## Demo Case Study

The site features **Bolt Electrical** (Hampshire NICEIC-approved electrician) as a live demo:
- Demo phone number: +44 7782 214455 (AI voice agent)
- Website: boltelectrical.uk (chatbot demo)
- This is a real client, not fictional

## Content Principles

- **100% electrician-specific copy** — no generic "Portsmouth business" language
- Use **UK English spelling** (specialise, organised, colour, labour, centre)
- Reference real electrical scenarios ("hands full of cable", "working in a ceiling void", "up a ladder")
- Mention specific electrical services by name (EICR, consumer unit, EV charger, PAT testing, rewire)
- Include industry certifications naturally (NICEIC, Part P, BS 7671, 18th Edition)
- Focus on pain points specific to electricians (can't answer phone when working, emergency callouts, sole trader challenges)
