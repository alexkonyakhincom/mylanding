# Landing update: production projects, Google Analytics, AI-readable profile

Date: 2026-08-06 · Site: alexkonyakhin.com (GitHub Pages, static, single `index.html`)

## Goal

1. Showcase the three products currently in production, built by Alexey.
2. Add Google Analytics (GA4) to see visitors.
3. Make the page legible to AI crawlers/answer engines: who Alexey is, his strengths, why work with him.

## Design

### 1. "Built & shipped" section

New section in `index.html`, placed directly after "By the numbers", before "Experience". Three linked rows styled to match the existing minimal aesthetic (bordered rounded rows, hover background):

- **NicePass** — nicepass.cc — Loyalty-card platform for restaurants: Apple/Google Wallet passes, AI-driven campaigns, iiko integration.
- **Stopwell** — stopwell.app — Flight concierge that plans the trip around arriving in shape for the event, not just price.
- **VPNKill** — vpnkill.com — macOS menu-bar kill switch that blocks any traffic not routed through the VPN.

Each row is an `<a>` opening the product site in a new tab.

### 2. Google Analytics

Standard GA4 `gtag.js` snippet in `<head>` with a `G-XXXXXXXXXX` placeholder Measurement ID (user will create the property and swap the ID; a marker comment points at both spots).

Known limitation (accepted): GA4 auto-filters known bots and requires JavaScript, so it shows human visitors only — crawlers/robots will not appear.

### 3. AI/robot-readable profile

- `llms.txt` (repo root, served at `/llms.txt`) — markdown profile for AI crawlers: who Alexey is, strengths, why work with him, products, experience highlights, contact.
- JSON-LD `Person` schema in `<head>` — name, job title, image, email, `sameAs` (LinkedIn, Telegram), `knowsAbout` skills, `owns` the three products with URLs.
- `robots.txt` — allow all crawlers, explicitly welcome AI bots (GPTBot, ClaudeBot, Google-Extended, PerplexityBot), comment pointing to `/llms.txt`.
- `<meta name="description">` (currently missing) + `<link rel="canonical">`.

### 4. Housekeeping

`<title>` still reads "Senior PM" — update to "Alexey Konyakhin — CPO/CTO/COO · Founder" to match the hero.

## Out of scope

Robot/crawler analytics (needs a proxy like Cloudflare in front of GitHub Pages), sitemap, Open Graph tags, any redesign.

## Delivery

All work on `feature/projects-ga-ai-info`. Merge/push to `main` (= production deploy) only with explicit user approval.
