# Signal-based outbound: companies that look like the 192

Drafted 19 Nov 2026. Companion files: [`signals.csv`](signals.csv) (139 signals, one row each, with detection method, outreach hook and persona) and [`companies.csv`](companies.csv) (the 192 seed companies).

Items marked **[ASSUMED]** are my working assumptions. Please correct them before this goes to the SDR team.

## 1. What we are selling and to whom

**Offer [ASSUMED]:** Anakin's website-to-action layer. That is Wire (typed read and write actions on sites with no public API; 112 catalogs and 746 live actions per the latest internal numbers, please verify before quoting), browser tasks for the cases that really need a browser, scrape, and MCP delivery.

**Two buyer segments, taken from the research:**

| Segment | Buys today from | Typical buyer |
|---|---|---|
| 1. Uses browsers for web actions | Browserbase, Browserless, Browser Use, Kernel, Steel, Anchor, Skyvern, Airtop, Notte | Engineering lead at an AI-agent or automation company |
| 2. Needs websites as API endpoints | Deck, Integuru, TinyFish, Anon, Parse.bot | Founder or integrations lead at a vertical-AI product |

**What the 117 strong-evidence companies in the seed list have in common** (rough keyword bucketing; a company can sit in more than one bucket, and 37 had no usable industry text):

| Bucket | Count |
|---|---|
| AI-agent, developer and infra platforms | 40 |
| Fintech, finance, tax, insurance | 17 |
| GTM, sales and data products | 16 |
| Healthcare | 11 |
| Retail, e-commerce, CPG, delivery | 9 |
| Real estate and utilities | 6 |
| Logistics and freight | 5 |
| Legal, government, civic | 4 |

So the lookalike is: **a young, engineering-led company whose product depends on logging into or reading sites that have no API, in a portal-heavy vertical.** Retail, CPG, food delivery and mobility are a smaller share of the seed list but are Anakin's strongest proof points, so they get their own trigger set (V7, V8).

## 2. How the signals are organised

Every outbound decision needs four things answered. Each signal in the catalogue answers one of them.

| Layer | Question | Signal types | Behaviour |
|---|---|---|---|
| **Fit** | Is this the kind of company that buys? | F (Gate) | Static. Must pass before anything else counts. |
| **Need** | Do they have the problem? | H, T, G, P, X | Slow-moving evidence of pain or architecture. |
| **Trigger** | Why now? | Trigger-strength signals in any category | Decays fast. Starts the clock. |
| **Intent** | Are they looking at us? | E | Decays fastest. Overrides sequence timing. |
| **Suppress** | Should we stay away? | N | Blocks or downgrades regardless of score. |

Strength classes:

- **Gate:** fit criterion. Required, not scored on timing.
- **Trigger:** act within 1-3 business days. Usually a public statement of pain, a competitor event, a new leader, or a visit to our pricing or docs.
- **Strong:** meaningful evidence; needs one more signal or a Trigger to justify outreach.
- **Support:** context that sharpens the message or breaks ties.
- **Suppress:** blocks or downgrades.

Each signal has a **half-life** in days. A signal 45 days old with a 45-day half-life counts half.

## 3. Scoring and routing [ASSUMED weights, calibrate after about 50 outcomes per signal]

```
Score = Fit (0-40) + Signals (0-60, capped)

Fit:     core workload gate (F1, F6, F7, F8, F9 or F11)  = 20
         engineering-led, young, right size (F2 + F3)    = 10
         portal-heavy vertical or lookalike (F4 or F5)   = 10
         A company with no core-workload gate is out.

Signals: Trigger = 30, Strong = 12, Support = 5
         each multiplied by 0.5 ^ (age_days / half_life_days)
         sum capped at 60

Suppress (N-series): N1, N2, N3, N6, N10 block outright.
                     N4, N5, N8 cut the score by half.
```

| Tier | Score | Action | Time to first touch |
|---|---|---|---|
| **Hot** | 65 and above | AE plus solutions consultant, personal message, offer to build one Wire on their named site | 1 business day |
| **Warm** | 45-64 | SDR sequence led by the signal | 3 business days |
| **Watch** | 30-44 | No outreach; re-score weekly | n/a |
| **Ignore** | under 30 | Leave out | n/a |

**Stacking rule:** a company needs either one Trigger in the last 30 days, or three Strong signals from at least two different categories, before it enters outbound.

**Worked examples**

- Seed-stage agent startup (Fit 40: F7 + F2/F3 + F5) that posted a Playwright engineer role 10 days ago (H1: 30 x 0.5^(10/45) = 25.7). Score 65.7: **Hot**.
- Series B vertical-AI company (Fit 30) with a new CTO 30 days ago (L2: 12 x 0.5^(30/90) = 9.5). Score 39.5: **Watch** until a second signal appears.
- Company on Browserbase (T3, Trigger) whose vendor posted a security notice (M1, Trigger): two Triggers, **Hot** if Fit is 30 or more.

## 4. Signal catalogue

139 signals in 12 categories: Fit 12, Hiring 17, Tech stack 11, GitHub 8, Product and website 11, Pain 10, Market events 10, Capital events 11, People 9, Engagement 12, Vertical triggers 18, Suppression 10. By strength: 12 Gate, 30 Trigger, 60 Strong, 27 Support, 10 Suppress.

The appendix at the end of this file lists every signal with its strength, half-life and where to detect it. `signals.csv` adds how to run each one, the outreach hook and the target persona.

**The 30 Trigger signals** are the ones to automate first, because each one justifies outreach on its own:

| Category | Triggers |
|---|---|
| Hiring | H1 browser-automation role, H2 scraping engineer, H8 reverse-engineering in the JD, H9 anti-bot or proxy in the JD, H15 competitor named in the JD |
| Tech | T3 uses a cloud-browser vendor, T4 uses a website-to-API vendor |
| GitHub | G3 engineers filing issues about stealth, concurrency or breakage |
| Product | P2 asks users for portal credentials, P8 launched an agent feature |
| Pain | X1 posts about scrapers breaking, X2 GitHub issues about selector breakage, X3 negative vendor review, X6 maintenance postmortem, X8 asks for recommendations, X10 vendor logo removed |
| Market | M1 competitor outage or incident, M3 competitor acquired or shut down |
| Capital | C1 fresh funding in agents or vertical AI |
| People | L1 vendor champion changed jobs, L9 known HubSpot contact moved to a Fit company |
| Engagement | E1 pricing or docs visit, E2 comparison-page visit, E3 signup, E4 usage threshold, E9 alternatives search, E10 technical evaluation, E11 existing-customer expansion |
| Vertical | V7 retail and CPG pricing trigger, V8 delivery and mobility trigger |

## 5. Plays: which signals trigger which motion

| Play | Signals that start it | Opening angle | Buyer | Proof to bring |
|---|---|---|---|---|
| **A. Displacement** | T3, T4, H15, X3, X10, M1, M2, M3, E2, E9 | Not 'switch'. 'Use typed actions where a browser is overkill and keep browsers where they are needed.' | Engineering lead | A Wire built on one of their own target sites |
| **B. Build pain** | H1, H2, H8, H9, X1, X2, X6, T10, G3 | 'You are paying engineers to maintain this. We maintain it.' | CTO or founding engineer | Cost per site maintained vs. their hiring plan |
| **C. Integration gap** | P1, P2, P3, P11, T6, T7, H3, H12, X5 | 'Your next integration should not cost what your last one did.' | Integrations lead or founder | Time to first endpoint on a long-tail portal |
| **D. Agent launch** | C1, P8, H4, H5, F7, G5, T9 | 'Give the agent a reliable web layer through one MCP tool.' | Head of AI or founder | MCP demo against their use case |
| **E. Vertical event** | V1-V18, M6, M10 | Name the vertical workload and the date pressure | Operations or pricing lead | Vertical-specific build |
| **F. Product-qualified** | E1-E5, E10 | Respond to what they did, within hours | Whoever signed up | Offer to extend limits and build their named site |
| **G. Champion move** | L1, L8, L9 | 'You ran <workload> at <prior company>. At <new company> you will hit it again.' | The mover | Reference past conversation if it exists |
| **H. Expansion** | E11 | New team at an existing customer | Existing champion | Internal reference |

**Message rules**

1. First line states one public, observable fact. Never quote private or inferred data. Never cite L5 (follows or likes).
2. One offer: a working Wire or scrape on a site they name, built in 24 hours.
3. One ask: which site matters most.
4. Match the hook column of `signals.csv`, then edit.
5. Do not name a competitor as unreliable. State a difference and let them test it.

## 6. How to detect the signals

| Source | Signals | Tool |
|---|---|---|
| Apollo company and people search | F2-F4, F11, F12, H2, H3, H5-H7, H10, H11, H14, H17, C1, C6, C7, L1-L3, L8, T1, T5-T7, T9, E1, E2 | `apollo_mixed_companies_search`, `apollo_mixed_people_api_search`. Job-title filters match titles only, not descriptions. Each company search costs 1 credit, so I will confirm the total before running a batch. |
| Careers pages and ATS (Greenhouse, Lever, Ashby) | H1, H4, H8, H9, H15, H16 | Anakin `scrape` with `generateJson` on each Fit company's careers page; keyword match in descriptions |
| Page and blog watchers | M1-M3, X7, X10, P3, P5, P8, P10, V-series | Anakin `monitor_create` / `monitor_changes` on competitor blogs, status and pricing pages, target changelogs and customer-logo pages |
| GitHub | G1-G5, G8, T1, T9-T11, X2 | GitHub code and issue search on package manifests, Dockerfiles and issues, joined to company by organisation |
| HubSpot | E3-E8, E11, L9, N1-N3, N9, N10 | `search_intent_signals` (aggregate by company), contact job-change data, deal stages for suppression |
| Public communities and review sites | X1, X3, X4, X5, X8, G6, C3 | Anakin `search`; G2, Reddit, Hacker News, Product Hunt |
| Filings and news | C11, M6, C5, C6, M3, M8 | SEC EDGAR full-text search, news search |
| Anakin product analytics | E3, E4, E5, E10 | Event feed to HubSpot properties |

Anakin's own scraping and monitoring does most of the detection, so the system doubles as a product demo.

**Weekly refresh [ASSUMED cadence]:**

1. Run page monitors and pull changes.
2. Run Apollo searches for H2, C1, L1, L2 (credit-gated).
3. Run GitHub searches for G1-G3, T10.
4. Pull HubSpot intent and product events.
5. Re-score every Fit company; write Score, Tier and Top Signals to HubSpot.
6. Post Hot accounts to a Slack channel; create AE tasks.

## 7. Rollout

| When | What |
|---|---|
| Week 1 | Expand the 192 seeds into a Fit list of about 1,000 lookalikes (Apollo filters F2-F4, F11, F12 plus lookalike research for F5). Size the list first and confirm the credit cost. Create HubSpot properties. Load suppression lists (N1-N3). |
| Week 2 | Automate the first 11 signals: H1, H2, H9, H15, C1, L1, L2, L9, E1, E2, M1. |
| Weeks 3-4 | Launch Hot and Warm sequences. Weekly signal review with Rakesh and Moumita. |
| Days 30-60 | Add GitHub (G-series), pain (X-series) and product (P-series) signals. |
| Days 60-90 | Calibrate weights using outcomes. Retire signals that never convert. |

**Measure per signal:** accounts flagged, contacted, replied, meeting held, opportunity created. Also track time from signal to first touch, and Hot-tier share of pipeline. Compare against current outbound from HubSpot as the baseline; I have not pulled that baseline yet.

**Retire rule [ASSUMED]:** after 50 contacted accounts, drop any signal with no meetings.

## 8. Risks and compliance

- **Privacy and email law:** GDPR and PECR apply to EU and UK contacts; CAN-SPAM to US. Honour unsubscribes (N10).
- **LinkedIn:** do not scrape logged-in LinkedIn pages. Use Apollo and approved alerts for job changes (L1, L2, L9).
- **Job boards and communities:** follow each site's terms and robots rules when scraping.
- **Evidence quality:** the 192 seed companies come from vendor-published pages, not from the customers themselves. Re-check before quoting someone as a customer of a rival.
- **Signal freshness:** weights decay; refresh weekly or the tiers go stale.
- **Fairness to competitors:** claims in outreach must be defensible and testable.

## 9. Assumptions and decisions needed

1. **Offer [ASSUMED]:** Wire, browser tasks, scrape and MCP. Confirm the exact product and the claims we can make (112 catalogs, 746 live actions).
2. **Geography [ASSUMED]:** US first, then UK and EU.
3. **Segment 1 enterprise (RPA back office):** I recommend excluding it from v1 because the cycles are long; start with startups and mid-market.
4. **Apollo credits:** set a budget for list-building and weekly refresh.
5. **Owner:** I assumed the SDR leads (Rakesh, Moumita) own the weekly signal review.
6. **Retail and delivery:** keep V7 and V8 on the existing price-intelligence motion, or fold them into this one.

## Appendix: signal catalogue (shortlist view)

### F. Fit (who looks like the 192) (12)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| F1 | Core workflow depends on logging into third-party sites that have no public API (payer, carrier, tax, utility, supplier portals) | Both | Gate | n/a | Company site, docs, G2/Product Hunt copy |
| F2 | AI-native company, founded 2022 or later, 5-200 staff | Both | Gate | n/a | Apollo |
| F3 | Engineering-led team (3+ engineers, product shipped by engineers) | Both | Gate | n/a | Apollo |
| F4 | Sells into a portal-heavy vertical: healthcare, insurance, logistics, fintech/tax/payroll, legal, real estate/utilities, government, travel | Both | Gate | n/a | Apollo |
| F5 | Lookalike of a named customer in the 192 (same vertical and same workload, e.g. price scraping like Takeoff Copenhagen) | Both | Gate | n/a | companies.csv + web |
| F6 | Data-product company whose revenue depends on fresh web data (pricing, listings, reviews, filings, AI-search visibility) | Both | Gate | n/a | Company site, Product Hunt, G2 |
| F7 | Agent or workflow platform that needs a 'browser tool' or 'web actions' capability (agent builders, assistants, vibe-coding, automation SaaS) | 1 | Gate | n/a | Company site, docs, GitHub |
| F8 | Marketplace or aggregator that normalises supply from many supplier sites (travel inventory, insurance quotes, menus, rates) | 2 | Gate | n/a | Company site |
| F9 | Enterprise back office running RPA or BPO on web portals (shared services, claims, AP, onboarding) | 1 | Gate | n/a | Apollo, job posts, 10-K |
| F10 | QA, testing or monitoring company running browser fleets for customers | 1 | Gate | n/a | Company site |
| F11 | Retail, CPG, e-commerce, food-delivery or mobility company that tracks competitor price, availability or fees | Both | Gate | n/a | Apollo |
| F12 | US, UK or EU headquartered [ASSUMED priority order] | Both | Gate | n/a | Apollo |

### H. Hiring (17)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| H1 | Job post for browser automation, Playwright, Puppeteer or Selenium in a non-QA role | 1 | Trigger | 45 | ATS pages (Greenhouse, Lever, Ashby), LinkedIn Jobs |
| H2 | Job post for web scraping, crawler or data-acquisition engineer | Both | Trigger | 45 | Apollo, ATS pages |
| H3 | Job post for integrations engineer or integration platform engineer at a portal-heavy product | 2 | Strong | 45 | Apollo, ATS pages |
| H4 | Founding or early engineer role at an AI-agent startup that mentions computer use, browser or web agents | 1 | Strong | 45 | ATS pages, YC Work at a Startup |
| H5 | Roles titled AI agent engineer, agent infrastructure or computer-use | 1 | Strong | 45 | Apollo, ATS pages |
| H6 | RPA developer, UiPath, Automation Anywhere or Blue Prism roles | 1 | Strong | 60 | Apollo, job boards |
| H7 | Roles for prior authorization, eligibility verification or claims-status automation | Both | Strong | 60 | Apollo, job boards |
| H8 | JD mentions reverse engineering, network traffic, HAR files or undocumented APIs | 2 | Trigger | 45 | ATS pages |
| H9 | JD mentions proxies, CAPTCHA, anti-bot, Cloudflare, fingerprinting or residential IPs | 1 | Trigger | 45 | ATS pages |
| H10 | Three or more open data-engineering or web-data roles in the last 30 days | Both | Strong | 30 | Apollo |
| H11 | Hiring a Head of Data, VP Data or data-acquisition lead | Both | Strong | 60 | Apollo, LinkedIn |
| H12 | Roles for solutions or implementation engineers focused on connecting customer systems | 2 | Support | 60 | Apollo, ATS pages |
| H13 | Freelance or contract postings for scrapers or portal automation (Upwork, Freelancer) | Both | Strong | 30 | Upwork, Freelancer |
| H14 | Bulk hiring for manual portal work: data entry, claims processing, benefits verification, portal specialists | 1 | Strong | 60 | Apollo, job boards |
| H15 | JD names a competing tool: Browserbase, Browserless, Browser Use, Stagehand, Skyvern, Steel, Kernel, Airtop, Hyperbrowser, Bright Data, Apify | Both | Trigger | 60 | ATS pages, job boards |
| H16 | JD mentions MCP, tool use or function calling combined with web actions | 1 | Support | 45 | ATS pages |
| H17 | Engineering headcount up 25%+ in 6 months | Both | Support | 90 | Apollo |

### T. Tech stack and vendor footprint (11)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| T1 | Uses Playwright, Puppeteer or Selenium in production code | 1 | Strong | 180 | GitHub, job posts, Apollo tech |
| T2 | Uses a scraping or proxy provider: Bright Data, Oxylabs, Apify, ScraperAPI, Zyte, ScrapingBee, Decodo | Both | Strong | 180 | Job posts, docs, G2 reviews, case studies |
| T3 | Uses a cloud-browser vendor (Browserbase, Browserless, Kernel, Steel, Anchor, Hyperbrowser, Notte, Skyvern, Airtop) | 1 | Trigger | 90 | Case studies, logo walls, public repo deps, JD, partner pages |
| T4 | Uses a website-to-API vendor (Parse.bot, Integuru, Deck, Rindler, TinyFish, Anon, Vectorly, Pomerado) | 2 | Trigger | 90 | Logo walls, case studies, GitHub, JD |
| T5 | Heavy RPA or iPaaS use (UiPath, Power Automate, Zapier, Make, n8n, Workato) | 1 | Support | 180 | Apollo tech, job posts |
| T6 | Uses bank aggregators (Plaid, MX, Finicity, Yodlee, Akoya) | 2 | Strong | 180 | Apollo tech, docs |
| T7 | Uses unified-API or integration platforms (Merge, Nango, Paragon, Apideck, Finch, Pinwheel, Argyle) | 2 | Strong | 180 | Apollo tech, docs |
| T8 | Uses healthcare connectivity (Availity, Waystar, Redox, Particle) and still has portal workflows | Both | Support | 180 | Docs, job posts |
| T9 | Uses agent frameworks (LangChain, CrewAI, Mastra, AI SDK, LlamaIndex, OpenAI Agents SDK) | 1 | Support | 180 | GitHub, Apollo tech |
| T10 | Runs self-hosted headless Chrome (Dockerfiles, Selenium Grid, Kubernetes browser pods) | 1 | Strong | 180 | GitHub, JD, engineering blog |
| T11 | Builds on Anthropic or OpenAI computer-use APIs | 1 | Support | 120 | GitHub, blog |

### G. GitHub and developer ecosystem (8)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| G1 | Org repos depend on playwright, puppeteer, selenium, browser-use, stagehand or skyvern in non-test code | 1 | Strong | 120 | GitHub code search |
| G2 | Org members starred or forked browser-use, stagehand, skyvern, steel-browser, notte or Integuru | Both | Strong | 60 | GitHub stargazers API |
| G3 | Org engineers open issues or PRs in those repos about stealth, concurrency, auth or breakage | 1 | Trigger | 45 | GitHub issues API |
| G4 | Org publishes scrapers, connectors or portal clients (names like -scraper, -connector, -portal) | 2 | Strong | 120 | GitHub |
| G5 | Org publishes an MCP server wrapping web or portal tasks | 1 | Support | 90 | GitHub, MCP registries |
| G6 | Show HN or Launch HN for an agent or portal-automation product | Both | Strong | 45 | Hacker News |
| G7 | Datasets or models trained on scraped web data (Hugging Face, Kaggle) | 1 | Support | 180 | Hugging Face |
| G8 | Contributions to reverse-engineering or HAR-to-API open-source projects | 2 | Strong | 90 | GitHub |

### P. Product and website footprint (11)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| P1 | Integrations page lists many long-tail portals, payers, carriers or utilities | 2 | Strong | 90 | Company site |
| P2 | Product asks end users to connect an account or enter portal credentials | 2 | Trigger | 90 | Product demo, docs, help center |
| P3 | Integrations marked 'coming soon' or customers voting for new portals on a roadmap | 2 | Strong | 60 | Roadmap pages, Canny, public changelog |
| P4 | Docs mention browser automation, RPA, screen scraping or 'we log in on your behalf' | Both | Strong | 180 | Docs |
| P5 | Changelog or blog announces N new integrations or connectors per month | 2 | Support | 60 | Changelog |
| P6 | Pricing charges per connection or per integration | 2 | Support | 180 | Pricing page |
| P7 | Data-heavy product with no public API ('request API access' form) | 2 | Support | 180 | Company site |
| P8 | Launched an agent, copilot or assistant feature in the last 90 days that acts on third-party sites | 1 | Trigger | 45 | Blog, changelog, Product Hunt |
| P9 | Site discusses MFA, 2FA or a credential vault in the context of connecting customer accounts | 2 | Strong | 180 | Security page, docs |
| P10 | Homepage repositioned toward 'agentic' or 'AI-native' | Both | Support | 60 | Homepage |
| P11 | Customer-facing 'reconnect your account' prompts or help articles | 2 | Strong | 60 | Help center, app reviews |

### X. Pain and friction (public) (10)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| X1 | Employee posts about scrapers breaking, bot blocks or CAPTCHAs (Reddit r/webscraping, HN, X, Stack Overflow, Discords) | 1 | Trigger | 21 | Reddit, HN, X, Stack Overflow |
| X2 | GitHub issues in their own repos about selector changes, 403s, Cloudflare or CAPTCHA | 1 | Trigger | 45 | GitHub |
| X3 | Negative review of their current vendor (G2, Capterra, Reddit) from the target company | Both | Trigger | 60 | G2, Capterra, Reddit |
| X4 | Complaints about proxy cost, rate limits, concurrency caps or session timeouts | 1 | Strong | 45 | Reddit, HN, X |
| X5 | Customer reviews of the target say integrations are flaky or connections drop (App Store, Trustpilot, G2) | 2 | Strong | 60 | App Store, Trustpilot, G2 |
| X6 | Engineering blog or postmortem about scraper or automation maintenance burden | Both | Trigger | 90 | Company blog, Medium, HN |
| X7 | Status-page incidents tied to upstream site changes | 2 | Strong | 30 | Status pages |
| X8 | Public request for recommendations: 'what do you use for browser automation or scraping at scale?' | Both | Trigger | 14 | X, LinkedIn, Slack communities, Reddit |
| X9 | Roadmap items blocked by 'no API from <platform>' | 2 | Strong | 90 | Blog, interviews, podcasts |
| X10 | Vendor logo disappears from their site, or they publish a migration post | Both | Trigger | 30 | Company site (monitored), blog |

### M. Market and competitor events (10)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| M1 | Competitor outage or security incident (e.g. Kernel posted a public security-incident notice on 4 Nov 2026; contents not read) | 1 | Trigger | 60 | Vendor blogs and status pages |
| M2 | Competitor pricing or plan change (e.g. Steel's June 2026 pricing update) | 1 | Strong | 60 | Vendor pricing pages and blogs |
| M3 | Competitor acquired, pivoted or shut down (e.g. Convergence moved to Salesforce) | Both | Trigger | 90 | News, vendor blogs |
| M4 | Platform API deprecation or price hike (social, marketplaces, listings, maps) | 2 | Strong | 90 | Developer changelogs, news |
| M5 | Target site redesign or new anti-bot rollout (Cloudflare, Akamai, DataDome, PerimeterX) in a sector | 1 | Support | 30 | Industry forums |
| M6 | Regulatory or mandate change that creates or removes data access (e.g. prior-auth, open-banking, e-invoicing; verify current dates) | Both | Support | 180 | Regulator sites, trade press |
| M7 | Agent-access standards shift (Web Bot Auth, MCP, agent payments) | 1 | Support | 120 | Vendor and standards blogs |
| M8 | Scraping lawsuit, ruling or ToS crackdown | Both | Support | 90 | Legal news |
| M9 | New computer-use model release from a major lab | 1 | Support | 30 | Lab blogs |
| M10 | Seasonal peaks: tax season, open enrolment, Black Friday and holiday price wars, quarter-end close, summer travel | Both | Strong | 45 | Calendar |

### C. Capital and company events (11)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| C1 | Raised seed, Series A or B in the last 6 months in agents or vertical AI | Both | Trigger | 90 | Apollo, news |
| C2 | YC company, batch W25 or later, in agents, vertical AI, fintech or health | Both | Strong | 180 | YC directory, Launch YC |
| C3 | Product Hunt or Launch HN launch of an agent or integration product | Both | Strong | 30 | Product Hunt |
| C4 | Announced partnership that requires connecting to the partner's systems | 2 | Support | 60 | Press releases |
| C5 | Closed an acquisition and must integrate the acquired company's portals and systems | Both | Strong | 90 | News, press |
| C6 | Expanded to a new country or market | Both | Strong | 90 | News, careers pages |
| C7 | Sales or CS headcount up sharply | 2 | Support | 90 | Apollo |
| C8 | Announced enterprise customer wins that run on legacy systems | 2 | Strong | 60 | Press, LinkedIn |
| C9 | Moving up-market and starting SOC 2 or HIPAA work | Both | Support | 90 | Trust page, job posts |
| C10 | Layoffs or an engineering hiring freeze | Both | Support | 60 | News, layoffs trackers |
| C11 | 10-K, earnings call or investor letter mentions manual processes, legacy portals, automation or agentic AI (public companies) | 1 | Strong | 120 | SEC EDGAR full-text search, transcripts |

### L. People and leadership moves (9)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| L1 | A person who used a vendor from the 192 joins a new company in an engineering or leadership role | Both | Trigger | 90 | LinkedIn, Apollo |
| L2 | New CTO, VP Engineering, Head of AI, Head of Data or Head of Platform in the last 90 days at a Fit company | Both | Strong | 90 | Apollo |
| L3 | New VP Ops, Head of Revenue Cycle or Head of Automation at an enterprise | 1 | Strong | 90 | Apollo |
| L4 | Engineers who speak or write about browser agents or scraping at scale | Both | Strong | 120 | Conference programs, blogs |
| L5 | Employees follow or engage with Browserbase, Browser Use, Stagehand or Skyvern pages | Both | Support | 45 | LinkedIn engagement exports |
| L6 | Executives post that agents need web access or that APIs do not exist for key systems | Both | Strong | 60 | LinkedIn, X |
| L7 | Speakers and sponsors at agent-infrastructure events | Both | Support | 60 | Event sites |
| L8 | Alumni of the 192 founding new startups | Both | Strong | 120 | LinkedIn, Crunchbase, YC |
| L9 | A contact already in HubSpot (289K+) changes job into a Fit company | Both | Trigger | 60 | HubSpot, Apollo |

### E. Engagement and intent (12)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| E1 | Visit to Anakin pricing, docs, Wire or MCP pages by a Fit company | Both | Trigger | 14 | Apollo website visitors, HubSpot tracking |
| E2 | Visit to comparison pages (Anakin vs Browserbase, Browserless, Parse.bot, Firecrawl, Apify) | Both | Trigger | 14 | Apollo, HubSpot |
| E3 | Free-tier signup, API key created or first scrape, Wire or browser_task run | Both | Trigger | 7 | Anakin product analytics |
| E4 | Usage thresholds: rate-limit hits, credits near exhausted, repeated failures on one site, 3+ Wires built, concurrency ceiling | Both | Trigger | 7 | Anakin product analytics |
| E5 | MCP install, docs search for a specific site, or GitHub star on Anakin repos | Both | Strong | 21 | Product and GitHub analytics |
| E6 | Three or more opens plus a click on outbound, or a reply of 'not now' with a timeline | Both | Strong | 30 | HubSpot sequences |
| E7 | Webinar attendance or content download (e.g. a Websites-as-APIs guide) | Both | Strong | 30 | HubSpot forms |
| E8 | Third-party intent topics: web scraping, browser automation, RPA, data extraction (G2, Bombora, HubSpot intent) | Both | Strong | 30 | HubSpot intent signals, G2, Bombora |
| E9 | Searches for 'alternatives' to Browserbase, Parse.bot or Firecrawl | Both | Trigger | 21 | G2 alternatives pages, Search Console on own comparison content |
| E10 | Technical evaluation: asked for a sandbox or a Wire build for a named site | Both | Trigger | 14 | SC notes, HubSpot |
| E11 | Existing customer team asks for new sites or a different team at the same customer shows interest | Both | Trigger | 30 | CX notes, HubSpot |
| E12 | Partner or SI referral (e.g. Capgemini, Infosys, PwC) | Both | Strong | 60 | Partner channel |

### V. Vertical-specific triggers (18)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| V1 | Healthcare: new payer or state coverage added, prior-auth volume growth, RCM engineering hiring | Both | Strong | 60 | Job posts, press, docs |
| V2 | Insurance: new carrier appointments, embedded-insurance launch, quote-flow hiring | Both | Strong | 60 | Press, job posts |
| V3 | Logistics and freight: new carrier lanes, shipper portal onboarding, tracking-feature launch | Both | Strong | 60 | Press, job posts |
| V4 | Fintech, tax and payroll: new state filings, new payroll or bank connectors, compliance product launch | Both | Strong | 60 | Changelog, press |
| V5 | Legal: new court or e-filing integration, case-management launch | Both | Strong | 60 | Press, job posts |
| V6 | Real estate, proptech and utilities: new property-manager integrations, utility-bill features | 2 | Strong | 60 | Changelog, press |
| V7 | Retail, CPG and e-commerce: marketplace expansion, Q4 price-war prep, MAP issues, hiring pricing or e-commerce analysts | Both | Trigger | 45 | Apollo, press, job posts |
| V8 | Food delivery, quick commerce and mobility: new city or country launch, competitor promo wars | Both | Trigger | 45 | Press, app stores |
| V9 | Travel and hospitality: new supplier or OTA integrations, rate-parity hiring | Both | Strong | 60 | Press, job posts |
| V10 | HR, benefits and payroll: new carrier integrations, employment-verification launch | 2 | Strong | 60 | Changelog |
| V11 | Procurement and manufacturing: supplier-portal rollout, RFQ automation hiring | 1 | Support | 90 | Job posts, press |
| V12 | Government and civic: new jurisdictions, permit or meeting data products | Both | Strong | 90 | Press, job posts |
| V13 | AI-search visibility (GEO): new tracking of ChatGPT, Gemini, Perplexity or AI Overviews | 1 | Strong | 45 | Product pages, press |
| V14 | Sales and GTM tooling: new enrichment sources or logged-in data features | Both | Strong | 45 | Changelog |
| V15 | Agentic commerce and shopping agents: checkout or booking features | 1 | Strong | 45 | Press, changelog |
| V16 | Creator and influencer platforms: new platform data features | 1 | Support | 60 | Changelog |
| V17 | Education technology: new LMS or college-portal integrations | 2 | Support | 90 | Changelog |
| V18 | Alt-data and investment research: new web-data sources, alt-data hiring | Both | Strong | 60 | Job posts, press |

### N. Negative and suppression (10)

| ID | Signal | Seg | Strength | Half-life | Where to detect |
|---|---|---|---|---|---|
| N1 | Already a paying Anakin customer | Both | Suppress | n/a | HubSpot |
| N2 | Open deal in HubSpot (any active stage) | Both | Suppress | n/a | HubSpot |
| N3 | Cold/Lost in the last 90 days with no new Trigger | Both | Suppress | 90 | HubSpot |
| N4 | Large in-house team (10+ engineers) on scraping or browser infra | Both | Suppress | 180 | LinkedIn, JD, engineering blog |
| N5 | Signed or announced a deal with a competitor in the last 6 months | Both | Suppress | 180 | Press, case studies |
| N6 | Target sites or data are legally sensitive for Anakin (restricted credentials, restricted jurisdictions) | Both | Suppress | n/a | Company site |
| N7 | Pure-API business whose workflows use only documented APIs | Both | Suppress | n/a | Docs |
| N8 | Hobby or pre-funding solo project (2 people or fewer) without PLG qualification | Both | Suppress | n/a | Apollo |
| N9 | Channel conflict with a strategic customer or partner | Both | Suppress | n/a | HubSpot |
| N10 | Unsubscribed, do-not-contact or restricted by privacy law for the contact's region | Both | Suppress | n/a | HubSpot |
