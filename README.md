# AI for Electricians

Marketing website for **AI for Electricians** — a UK-wide industry vertical site from Antek Automation, specialising in AI voice agents, chatbots, and workflow automation specifically for electricians and electrical contractors across the United Kingdom.

**Live site:** [aiforelectricians.co.uk](https://aiforelectricians.co.uk)

## Tech Stack

- Single `index.html` with inline CSS and JavaScript
- No build step, no frameworks, no dependencies
- Vanilla JS (IntersectionObserver for animations, accordion, contact form)
- Google Fonts (Sora + DM Sans)

## Features

- Dark premium theme with animated gradient orb hero
- Responsive design (320px to 1440px+)
- Interactive demo section with live Bolt Electrical AI voice agent demo
- Bolt Electrical case study strip
- Contact form (POST to n8n webhook)
- Cal.com embedded booking widget
- FAQ accordion (12 electrician-focused questions)
- Animated stat counters
- Smooth scroll navigation

## SEO

- Semantic HTML5 with proper heading hierarchy
- JSON-LD structured data (ProfessionalService, Organization, FAQPage)
- Open Graph and Twitter Card meta tags
- `robots.txt` and `sitemap.xml` included
- Electrician-specific keywords: EICR, EV charger, consumer unit, rewire, PAT testing, NICEIC, Part P, BS 7671
- UK-wide focus (not location-specific)

## Deployment

No build step required. Deploy the root directory to any static hosting provider:

- **GitHub Pages** — push to `main`, enable Pages in repo settings
- **Netlify** — connect the repo, publish directory: `/`
- **Vercel** — import the repo, framework preset: Other
- **Any web server** — upload `index.html`, `robots.txt`, `sitemap.xml`, `privacy-policy.html`, `terms.html`, `images/` and `favicon_io/` folders

## Project Structure

```
.
├── index.html                  # Complete single-page website
├── privacy-policy.html         # Privacy policy page
├── terms.html                  # Terms of business page
├── robots.txt                  # Search engine crawl rules
├── sitemap.xml                 # Sitemap for search engines
├── images/
│   └── bolt.webp               # Bolt Electrical case study screenshot
├── favicon_io/                 # Favicon files
├── CLAUDE.md                   # Claude Code project guidance
└── README.md                   # This file
```

## Demo

Live AI voice agent demo: **+44 7782 214455** (Bolt Electrical)

## Contact

**Email:** hello@aiforelectricians.co.uk
**Parent company:** [Antek Automation](https://www.antekautomation.com)
**AI Partner:** Certified Retell AI Partner
