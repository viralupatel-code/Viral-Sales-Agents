# Buyers of browser automation and website-to-API tools

Researched 19 Nov 2026 from vendor customer pages, case studies and logo walls. The full list is in [`companies.csv`](companies.csv): 192 companies, one row each, with vendor, use case, source URL and a confidence level. It can be imported into HubSpot or Apollo.

| Segment | High | Medium | Low | Total |
|---|---|---|---|---|
| 1. Use cloud browsers for web actions (Browserbase, Browser Use, Browserless, Kernel, Steel, Anchor, Skyvern, Airtop, Notte) | 48 | 25 | 75 | 148 |
| 2. Need websites turned into API endpoints (Parse.bot, Integuru, Deck, TinyFish, Anon) | 18 | 26 | 0 | 44 |

**What the confidence levels mean**
- **High:** the vendor published a case study or a named testimonial that describes the use case.
- **Medium:** the company's logo is on the vendor's own site, with no use case.
- **Low:** a third-party listing, or a vendor logo wall that probably reflects engineers using open-source tools, not a paid contract. Browser Use's wall of Google, Apple, Amazon, DHL and others falls here.

**Next step:** [`signal-playbook.md`](signal-playbook.md) defines the signals for finding more companies like these (139 signals, scoring, plays, rollout); [`signals.csv`](signals.csv) has them one per row.

## Where to start

These have the strongest public evidence and are closest to Anakin's retail, delivery and pricing-intelligence focus:

| Company | What they do with it | Vendor |
|---|---|---|
| ShopVision | Retail intelligence engine with 1.2B data points | Browserbase |
| Takeoff Copenhagen | Competitive price scraping; already moved off Bright Data once | Browserless |
| DoorDash | Web workflows at scale | TinyFish |
| Grubhub | Crowd-sourced sentiment for revenue analytics | TinyFish |
| Evive | Real-time retail sales data pulled from portals | Deck |
| Menards | Logo only | Deck |
| Huel | Logo only | Airtop |
| Vercel | Revenue/BI system crawling millions of sites | Browserbase + Kernel |
| PromptLoop | Crawls hundreds of thousands of sites a month | Browserbase |
| Clay | GTM data enrichment | Browserbase |
| The Prompting Company | 50,000+ browsers a month for AI-search visibility | Kernel |
| The Zebra | Insurance quotes from carrier sites in seconds | TinyFish |

**Companies on two vendors at once** (they are already evaluating options): Vercel and Coframe (Browserbase + Kernel), Composio (Browser Use + Anchor), Gumloop (Browser Use + Notte), Microsoft (Browserbase case study, also on Browser Use and Browserless lists).

**Segment-1 buyers that behave like Segment 2.** These companies' own products turn third-party sites into APIs: Atomic (payroll), Okra (banks), Rollee (payroll and gig platforms), Kompas and Deepki.

## Vendors (competitive map, not prospects)

| Vendor | Type | Public customer evidence |
|---|---|---|
| Browserbase | Cloud browsers + agents | Strongest: 18 case studies; claims 10,000+ companies and 35M+ sessions a month |
| Browserless | Headless browser hosting | 13 case studies; claims 10,000+ paying customers |
| Browser Use | Open-source agent + cloud | 7 case studies plus a large logo wall |
| Kernel | Cloud browsers | 7 customer stories plus logos; claims 11,000+ teams |
| Notte | Browsers + "Anything API" | Logo wall of about 100 mostly small companies |
| Skyvern, Airtop, Anchor | Browser agents | Logos and testimonials only |
| Steel, Hyperbrowser | Cloud browsers | Steel: only third-party names. Hyperbrowser: no named customers found |
| Deck | User-permissioned web agents (fetch, submit, pay) | 10 case studies plus logos (Brex, BILT, Capgemini) |
| Integuru | Reverse-engineers sites into APIs, no browser | 16 customer logos, mostly vertical-AI and healthcare |
| TinyFish | Enterprise web agents | 8 enterprise customers (Google, DoorDash, ClassPass) |
| Anon | Agent auth/integrations | 1 named customer (Homebase) |
| Parse.bot | Website-to-API marketplace (YC F25) | No named customers; 4,295 public APIs in its marketplace |
| Newer website-to-API startups | Rindler, Vectorly, Pomerado, Anysite, Browse AI, Kadoa | No named customers found |

## Caveats
- Every customer claim comes from the vendor or a directory, not from the customer. Confirm before you cite it in outreach.
- Anakin appears on Notte's logo wall, so it is left out of the list. Partner logos (Cloudflare, Zapier, n8n and others) and one church are also left out.
- Some logo names are ambiguous ("Pilot", "CTD", "Money"). They are flagged in the Notes column.
