# Lovable prompt — Jeff Rolling PM portfolio

Paste everything below the line into a new Lovable project as the first message. It is long on
purpose: Lovable invents copy when it is not given copy, and nothing on this site may be invented.
After the first build, use the follow-up prompts at the bottom one at a time.

---

Build a six-page personal portfolio website for a Product Manager. Use React + Tailwind, static
(no backend, no auth, no database, no forms that need a server). It must be mobile responsive and
fast. Use exactly the copy I give you below — do not paraphrase, embellish, or add metrics, and do
not add sections, testimonials, or stats that I have not written. Where I say "placeholder", use
a clearly marked placeholder.

## Design system

**Tone:** minimalist, editorial, calm. No flashy animations, no parallax, no gradients, no
emoji, no icons as decoration. Subtle hover states only. Respect prefers-reduced-motion.

**Palette (use these exact values as Tailwind theme colors):**
- `navy` #0F2440 — headings, nav text, footer background, primary button hover
- `forest` #1E4D3B — accent: links, result numbers, primary button, left rules on callouts
- `oak` #4A3222 — small uppercase labels ("eyebrows"), dates, secondary rules
- `oak-soft` #B89A82 — quote rules, footer muted text
- `ink` #141414 — body text; `ink-2` #4B4F57 — secondary body text
- `paper` #F4F1EA — page background (warm off-white); `paper-2` #ECE8DF — subtle surface fill
- `line` #D6D0C4 — all hairline borders
Never use pure white sections or pure grey. Never use a blue-to-purple gradient.

**Typography (Google Fonts):**
- Display / headings: **Fraunces**, weight 500, tight line-height (1.12), `text-wrap: balance`
- Body: **Source Sans 3**, 17px, line-height 1.55, max line width ~66 characters
- Labels, dates, metric captions: **IBM Plex Mono**, 0.72–0.8rem, uppercase, letter-spacing 0.1em
- Metric numbers: Fraunces in `forest`, tabular numerals

**Layout:** left-aligned throughout (never center whole sections), max content width 1120px,
side gutters ≥16px at every width, generous vertical section padding, sections separated by a 1px
`line` hairline rather than by cards or background changes. Do not put everything in rounded
cards; use square corners and hairlines. Buttons are rectangular, mono uppercase text, 1.5px border.

**Header (every page):** left: "Jeff Rolling" in Fraunces with a small mono line underneath
"PRODUCT MANAGER · AMSTERDAM". Right: nav "Work / About / Contact" in mono uppercase; the current
page gets a 2px `forest` underline.

**Footer (every page):** navy background, paper text. Left: "Jeff Rolling · Product Manager" and
a muted mono line "Amsterdam · Open to Senior PM roles in travel, payments, and expense". Right:
"jeff.rolling@gmail.com · LinkedIn" (LinkedIn links to https://www.linkedin.com/in/JeffRolling).

**Headshot:** a 4:5 portrait slot (260px wide on desktop, 180px on mobile) that shows the image
`/headshot.jpg` if present; if the image fails to load, show a navy block with "JR" in Fraunces
in `oak-soft`. I will upload the real photo later.

## Routes

- `/` — Home
- `/work/time-to-first-booking` — Case study 1
- `/work/checkout-reliability` — Case study 2
- `/work/expense-from-zero` — Case study 3
- `/about` — About
- `/contact` — Contact

Case-study pages share one layout: eyebrow → H1 → lede → a four-cell "At a glance" strip
(Problem / My role / Result / Source) in `paper-2` with hairline borders → body sections → a
"What I'd do differently" section → prev/next links in mono.

Use a `Callout` component (3px `forest` left rule, `forest-soft` #DCE7E0 fill, navy text, mono
eyebrow) and a `Note` component (3px `oak` left rule, `paper-2` fill, `ink-2` text). Use a
`BeforeAfter` component: two bordered cells with a mono label, a large Fraunces number (the
"after" number in `forest`), and a small caption, joined by an arrow; stacks vertically on mobile.

---

## PAGE: Home (`/`)

**Eyebrow:** TRAVEL TECH · PAYMENTS · EXPENSE · B2B SAAS

**H1:** I turn messy problems into simple, valuable products — by connecting customers, business teams, and engineering.

**Lede:** Product Manager at GetGoing Travel & Expense, a BCD Travel company. Five years in product; four of them as the sole PM across a booking, checkout, and expense platform that serves 76 client companies and 8,000+ travelers in six countries.

**Buttons:** "See the work" (primary, scrolls to #work) · "LinkedIn" (secondary, external)

**Headshot slot** to the right of the hero with caption (mono): "Amsterdam, NL · US / EU work rights"

**Metric strip** (three cells, hairline top and bottom, hairline between cells; stack on mobile):
1. `39%` — Faster time to first booking — 49 days to under 30 — after redesigning onboarding and activation. — caption: `2024 → 2025 · performance review`
2. `9.4%` — Checkout failure rate today, down from an estimated ~30% when the stabilization program started. — caption: `2026 YTD · 250 of ~2,650 bookings`
3. `0 → 1` — Built the company's first expense product — discovery, vendor strategy, AI receipt capture, partner APIs, pricing. — caption: `Second product line · paid package Aug 2025`

**Section `#work`** — eyebrow "CASE STUDIES", H2 "Three problems, three outcomes", lede: "Each one covers the decision, the trade-off, what shipped, what the data said afterward — and what I'd do differently."

Three rows (each row is one link; hairline between rows; columns: mono tag / title + summary / result on the right with a 2px forest left rule):
- Tag ACTIVATION — **Cutting time-to-first-booking from 49 days to under 30** — "Mapped the full onboarding journey with Sales and Customer Success, found the one bottleneck that was costing weeks, and redesigned the flow around customer effort instead of internal process." — Result: `−39%` / time to first booking → `/work/time-to-first-booking`
- Tag PAYMENTS — **Making checkout reliable when a third of bookings were failing** — "Reframed “bugs vs. features” as the real trade-off — every customer vs. one prospect — and ran a four-month stabilization program on payment authorization at checkout." — Result: `~30% → 9.4%` / booking failures → `/work/checkout-reliability`
- Tag 0 → 1 — **Building the company's first expense product from zero** — "Build, buy, or partner. Changed vendors mid-build on evidence, recruited six pilot customers, and turned an MVP into a paid Travel & Expense package across six countries." — Result: `New line` / per-user pricing, 6 markets → `/work/expense-from-zero`

**Section "How I work"** — eyebrow "HOW I WORK", H2 "Three things I believe about product", three columns (stack on mobile):
- **Reliability is a feature** — New features create no lasting value if customers can't trust the core flow. I'll defend a stabilization sprint to a leadership team pushing for roadmap velocity, and I've done it with the numbers to back it.
- **Interest is not need** — Customers said yes to a mobile app; almost nobody used it. Since then I ground decisions in behavioral data and outcome-focused interviews, not “would you like this?”
- **Teach, don't direct** — I was a teacher before I was a PM. Most of my influence comes from helping Sales, Support, Ops and Engineering understand each other — not from owning the decision.

**Section "Also shipped"** — two columns: left column eyebrow "ALSO SHIPPED", H2 "The rest of the roadmap", text "Sole PM from 2022 to 2025 across five value streams: core platform and payments, travel, expense, corporate/B2B, and the support portal." Right column, a list with a mono date column and hairlines:
- `2025` — **Engineering vendor transition, 20 → 37 people.** Led a six-month handover between two global engineering partners as the only PM with no VP of Engineering, while delivering the items below. Delivery cadence slowed — and nothing shipped broken.
- `Aug 2025` — **Deutsche Bahn rail integration.** Accreditation, launch, and a rescued timeline: cut MVP scope to the highest-value capabilities to restore train booking before the vendor handover completed.
- `Dec 2025` — **Four new country launches with SAP BRIM invoicing.** UK, France, Belgium, and the Netherlands, on top of Germany and the US.
- `2023–24` — **Payment options at checkout.** Bring-your-own-card for Visa, Mastercard, Amex, AirPlus, and Amex BTA; virtual payment automation via Conferma; Worldline integrations.
- `2023–24` — **Unused ticket management, v1 → v2.** Chose the parent company's internal tracker over an external vendor, then shipped a deliberately manual v1 as a bridge to a self-serve v2 with expiry alerts.
- `2024` — **GetGoing mobile app, iOS and Android.** Shipped as a PWA on Engineering's proposal after I scoped native at far higher cost. The adoption lesson (link to `/about#lesson`) changed how the company runs discovery.

---

## PAGE: Case study 1 (`/work/time-to-first-booking`)

**Eyebrow:** CASE STUDY 1 OF 3 · ACTIVATION · GETGOING, 2024–2025
**H1:** Cutting time-to-first-booking from 49 days to under 30
**Lede:** GetGoing's pitch to small businesses is fast implementation. In early 2024, the average new customer took 49 days to make a first booking — and the single worst step took two months on its own.

**At a glance:**
- Problem — New customers were signed, but not booking. Revenue and the “fast to implement” promise were both slipping.
- My role — Sole PM. Owned the journey mapping, the redesign, the prioritization, and the Customer Success enablement.
- Result — (large, forest) 49 → <30 days
- Source — 2024 and 2025 performance reviews; T&C validation tracked quarterly.

**H2: The situation**
GetGoing is a self-serve travel and expense platform for SMBs. Customers are supposed to sign, set up, and book within days without a travel agent in the loop. In practice the 2024 average from contract to first booking was **49 days**, and Customer Success was spending a large share of its time walking customers through setup by hand.

That mattered twice over. Time to first booking is time to first revenue. And “implementation in days, not months” was one of the few genuine advantages we had against larger travel management companies — every week of delay made that claim weaker.

**H2: Finding the real bottleneck**
Rather than start from the UI, I partnered with Sales and Customer Success to **map the complete onboarding journey** from signed contract to first trip: every step, every hand-off, every email, and how long each actually took.

The map surfaced the usual friction — confusing account setup steps, unclear communications, usability issues in the admin flows. It also surfaced one step nobody had isolated before: **assigning the authorized signer for Terms & Conditions.** Customers routinely got stuck deciding who at their company could sign, and the platform gave them no help. In Q1 2024, T&C validation alone averaged **64.5 days**.

Callout (eyebrow "THE DECISION"): Treat onboarding as a product problem, not a Customer Success problem. Instead of fixing bugs one at a time, redesign the experience around *reducing customer effort* — and prioritize every fix by the number of days it would give back.

**H2: What shipped** (bulleted)
- **Simplified account setup and T&C flow.** Clarified who signs and made the step visible and trackable, instead of a back-and-forth over email.
- **Clearer UI and messaging.** Rewrote onboarding emails and in-product copy so a customer could self-serve the next step without a CS call.
- **Impact-ranked fixes.** Bundled the usability issues by how many days each was costing and sequenced them that way, rather than by how loudly they were reported.
- **Customer Success enablement.** Built documentation, ran hands-on workshops, and sat in on live onboarding sessions to watch customers use the platform. Those sessions fed a second round of fixes and a customer-facing knowledge base — the best research came from watching, not asking.

**H2: The result**
BeforeAfter: "Time to first booking" 49 days (2024 average) → <30 days (2025 · a 39% improvement)
BeforeAfter: "T&C validation" 64.5 days (Q1 2024) → 15.3 days (Q4 2024 · a 76% reduction)

Account activation itself became near-instant: a client who is ready can now book within minutes of setup. Customer Success spent far less time hand-holding, and fast implementation went from a claim to a measurable advantage.

Note: **The honest caveat.** Much of the remaining delay is customers who simply have no trip to book yet. Product can't compress that, and I'd rather say so than claim the last 30 days as friction. Separating “delay we removed” from “delay that isn't ours” is what let us stop optimizing the wrong thing.

**H2: What I'd do differently**
I would have instrumented the onboarding funnel step by step before starting. We measured the journey largely through CS records and quarterly reviews, which was enough to find the T&C bottleneck but too coarse to see which of the smaller fixes moved the number most. Starting from event-level data would have let me prove — not infer — where the remaining days go.

Prev/next: "← All work" (`/#work`) · "Next: Checkout reliability →"

---

## PAGE: Case study 2 (`/work/checkout-reliability`)

**Eyebrow:** CASE STUDY 2 OF 3 · PAYMENTS & PLATFORM RELIABILITY · GETGOING
**H1:** Making checkout reliable when a third of bookings were failing
**Lede:** Shortly after launch, payment authorization failures at checkout were turning confirmed itineraries into support tickets. Leadership still wanted new features for prospects. I had to make the case that reliability *was* the feature — and then run the program.

**At a glance:**
- Problem — The team estimated roughly 30% of bookings were failing, most at payment authorization. Sales couldn't demo with confidence.
- My role — Sole PM. Owned the booking flow end to end — shopping, selection, checkout, payment, confirmation — and the prioritization case to leadership.
- Result — (large, forest) ~30% → 9.4%
- Source — Failure rate: GetGoing database, 2026 YTD (250 of ~2,650 bookings). Starting point: team estimate, not a measurement.

**H2: The situation**
GetGoing processes corporate travel payments across Europe and North America: different rails, different card products, different failure modes. In year one, recurring platform issues were hitting customers at the worst possible moment — **checkout**. A traveler would pick a flight, submit a card, and the booking would fail to authorize. Tickets piled up, Sales struggled to get new customers to trust the platform, and the team's own estimate was that **roughly 30% of bookings were failing.**

The estimate wasn't precise — we didn't yet have clean failure instrumentation — but it was enough to make the case. For a booking platform, it was an existential number.

**H2: The trade-off nobody wanted to make**
Leadership was still pushing feature work to win sales opportunities. The default framing was “bugs versus features,” and under that framing bugs always lose: features have a named prospect attached and bug fixes don't.

Callout (eyebrow "THE REFRAME"): Stability improves the experience for **every** customer. Most requested features served one or two prospects with no guaranteed business. That's the actual trade-off — not bugs vs. features, but everyone vs. someone.

To make that concrete, I partnered with Engineering to gather every known issue, assess customer impact, and **size the work with RICE**. Instead of triaging bugs individually, we grouped related failures so root causes could be fixed once. Then I worked my manager, the VP of Engineering, and the commercial stakeholders through the prioritization — with the impact numbers, not with opinions.

We landed on a split: most capacity to stabilization for a fixed window, a small number of strategic features continuing so Sales still had news to share. I went deeper into sprint planning, backlog grooming, and stand-ups than a PM normally would, because holding that alignment for four months was the whole job.

**H2: What shipped** (bulleted)
- **A four-month stabilization program** targeting the authorization failures at checkout, sequenced by customer impact.
- **A daily bug check-in** with the GetGoing engineering lead and the vendor's project lead during the critical-bug spike, which became the standing triage practice.
- **A durable capacity policy.** The program ended, but the argument didn't: leadership adopted a planned split between platform health and feature work. Releases got faster once the platform stopped fighting back.
- **The checkout itself.** Alongside the reliability work, I launched the payment options travelers actually use: bring-your-own-card for Visa, Mastercard, Amex, AirPlus and Amex BTA; virtual payment automation via Conferma; and Worldline integrations. One deliberate decision: the surcharge is *always* shown, whatever the payment method, and the method order never changes by traveler or market. Transparent beats optimized.

**H2: The result**
BeforeAfter: "Bookings failing" ~30% (Team estimate at program start) → 9.4% (Measured · 2026 YTD · 250 of ~2,650)

Support tickets dropped, Sales had a product it could demo, and customer confidence — and sales — rose. In 2024 the team resolved **380+ bugs, averaging 32 a month**, while critical and major bug frequency fell.

The outcome I care about most is organizational: **leadership began trusting the product team to make roadmap decisions** instead of reacting to the loudest request. That trust is what made every later program on this site possible.

Note: **On the numbers.** The 30% is what we believed when we started; the 9.4% is what the database says now. I present them as estimate-then vs. measured-now on purpose. Compressing them into “a 69% improvement” would imply a precision the starting point never had.

**H2: What I'd do differently**
Instrument failures before arguing about them. We won the prioritization case on an estimate, and it took until 2026 to have a failure rate I fully trust. If I ran this again, the first two weeks would go to classifying every failed authorization by cause — issuer decline, 3DS, integration error, data — so the program could be sequenced by measured share rather than by engineering intuition, and so the “after” would have been available in month five instead of year three.

Prev/next: "← Previous: Time to first booking" · "Next: Expense from zero →"

---

## PAGE: Case study 3 (`/work/expense-from-zero`)

**Eyebrow:** CASE STUDY 3 OF 3 · 0 → 1 · GETGOING, NOV 2022 – DEC 2025
**H1:** Building the company's first expense product from zero
**Lede:** Customers wanted one place for travel and expenses. The company had never built an expense product, and I had to learn the domain, pick a strategy, change course when the first partner couldn't deliver, and design the commercial model — without overbuilding version one.

**At a glance:**
- Problem — SMB customers ran separate travel and expense tools. GetGoing had no expense capability and no expense expertise.
- My role — PM from first customer interview to paid launch: discovery, PRD, vendor selection and the mid-build switch, pilot program, pricing package.
- Result — (large, forest) A second product line
- Shipped — Expense MVP 2024 · paid Travel & Expense package with per-user pricing, Aug 2025 · four new countries, Dec 2025.

**H2: Build, buy, or partner**
The strategic question came first: build our own expense engine, integrate a third-party product, or something hybrid. Expense management was new to the organization, so I started by immersing myself in the domain — industry practice, internal experts across BCD, and interviews with the customers already asking for it.

The answer that fit a 33-person company with one PM was **partner**: own the customer experience and the travel-expense integration, and license the expense engine. In November 2022 we began weekly calls with a first partner, Numiga — customer stories, initial roadmap, technical architecture, wireframes.

**H2: Changing partners mid-build**
Several months in, it became clear the first partner could not deliver key capabilities on the timeline customers required. The tempting move was to push on: work was done, relationships were built, and switching meant an immediate delay.

Callout (eyebrow "THE DECISION"): Optimize for total time to market, not for avoiding short-term disruption. Switching cost us weeks now; staying would have cost us longer, because the functionality customers needed simply did not exist on the current path.

I evaluated the alternatives against the MVP requirements, consulted teams inside the parent company who had worked with the candidates, and recommended **Mobilexpense**. GetGoing became one of the earliest adopters of their Partner API — close enough to the build that we helped shape parts of the API itself, not just our implementation of it.

**H2: Scoping the MVP**
I wrote the Product Requirements Document: customer problems, user journeys, MVP scope, success criteria. It also became the template I later trained the business analysts on. With UX and Engineering we designed the core workflows and deliberately stopped there.

Table (two columns: Workflow / What v1 shipped):
- Expense capture — Log an expense from a trip or standalone, in the same platform as the booking
- Receipt scanning — AI receipt capture with OCR extraction
- Approvals — Approval workflow for submitted expenses
- Policies — Expense policy rules applied on submission
- Integration — Mobilexpense Partner API, so travel and expense data stay in sync

Before launch I **recruited six pilot customers** who agreed to give ongoing feedback through iteration; the group later grew to around ten, managed directly through customer interviews. Their feedback set the order of everything that came after v1.

**H2: From MVP to product line** (bulleted)
- **2024 — Expense MVP** launched to pilot customers, combining travel and expense in one platform for the first time.
- **Aug 2025 — Travel & Expense as a paid package** with **per-user pricing**. Designing the commercial model was part of the brief, not a hand-off to Sales.
- **Dec 2025 — four new countries** (UK, France, Belgium, Netherlands) with SAP BRIM invoicing, alongside Germany and the US.

Expense management is now GetGoing's second major product line and its subscription revenue model. All of it shipped while I was also running a full engineering vendor transition (link to `/#work`).

Note: **What I won't claim.** I don't publish attach rate or revenue for the expense line here. What I can say is that it went from a customer request to a priced, multi-country package in three years with a single PM on it — and that the pilot customers who shaped v1 are still shaping the roadmap.

**H2: What I'd do differently**
Run the vendor evaluation as a paid proof of concept before committing. The first partner's gaps were integration gaps, and integration gaps only show up when you integrate. A four-week technical spike against our real booking data would have surfaced them before we had months of joint design work to walk away from. The switch was the right call; needing to make it was avoidable.

Prev/next: "← Previous: Checkout reliability" · "About Jeff →" (`/about`)

---

## PAGE: About (`/about`)

Hero with headshot slot on the right (caption "Chicago → Amsterdam, 2022").
**Eyebrow:** ABOUT
**H1:** Every job I've had was the same job: understand what people actually need, then organize others to deliver it.
**Lede:** Business intelligence at Orbitz. A startup. Nonprofit fundraising. Two years teaching in Mongolia. Events technology. And for the last five years, product management — the role where all of it finally had a name.

**Section (two-column: left eyebrow "THE OBJECTION, ANSWERED" + H2 "Five years in product. Fifteen at the seam."; right column body):**
If you're hiring a Senior PM, five years is on the lighter side of the range. Here's why I think depth beats the calendar in my case.

**I've owned an entire product, not a surface of one.** From 2022 to 2025 I was the only Product Manager at GetGoing, responsible for five value streams — core platform and payments, travel, expense, corporate/B2B, and the support portal — on a platform doing 2,500 trips and €1.8M in transacted sales a year. A PM at a large company typically owns one of those. I've had to make the trade-offs *between* them.

**I've seen my own decisions play out.** Four years on one product means I lived with the consequences: the stabilization bet paid off over years, the mobile app didn't, the expense partner switch was right. PMs who move every 18 months rarely get that feedback.

**I was promoted into the title.** I joined BCD Travel in 2022 as Sr. Business Analyst, Product Planning, to build the product planning function; the company formalized the role as Product Manager in May 2024 as the function matured. The responsibilities were product management throughout — the title caught up.

**And the years before product were preparation, not a detour.** Coordinating a 35-person BI team at Orbitz. Co-founding a hotel-tech startup. Raising $250K a year for a nonprofit. Aligning local government, schools and NGOs in rural Mongolia with no authority and no shared first language. Launching a virtual events product line — pricing, staffing, operations, all of it — when live events stopped in 2020. Every one of those is a customer, a business team, and a delivery team that needed connecting.

**Section "The route here"** (eyebrow "PATH"; timeline list with mono date column, hairlines):
- `May 2024 – now` — **Product Manager, GetGoing Travel & Expense — BCD Travel, Amsterdam** — Promoted. Owns core platform and payments, expense, and corporate/B2B. Circle of Excellence award nominee for leadership, collaboration, and impact.
- `Aug 2022 – May 2024` — **Sr. Business Analyst, Product Planning — BCD Travel, Amsterdam** — Relocated from Chicago to build the product planning function for a newly launched SMB travel platform. Sole PM in practice from day one.
- `2019 – 2022` — **BCD Meetings & Events, Chicago** — Attendee Engagement Manager → Product Manager, Virtual Technology → Operations Manager, Technology. Launched and ran the virtual and hybrid events product line in 2020: discovery, pricing, service packages, staffing models. BCD Platinum Circle Award.
- `2020 – 2022` — **MBA, Business Analytics — DePaul University** — Concentrations in Digital Product Management and Analytics. GPA 4.0, earned while working full time. Beta Gamma Sigma.
- `2016 – 2019` — **Manager of Development & Communications — Genesys Works Chicago** — Raised over $250K annually through grants, campaigns, partnerships and donor engagement.
- `2014 – 2016` — **Teacher & Community Organizer — Peace Corps, Mongolia** — Organized the region's first Special Olympics for 50 children; raised over $16K for education initiatives.
- `2010 – 2013` — **Orbitz Worldwide · CogniJet Inc.** — Project coordinator for a 35-person global BI team at Orbitz, where I moved the editorial team to Agile. Then co-founded a startup building personalized hotel websites.

**Section id="lesson"** (two-column: left eyebrow "THE MISTAKE I LEARNED MOST FROM" + H2 "We validated an idea, not a problem"):
In year one, leadership wanted a mobile app — competitors had one, and customers said yes when asked. I wasn't convinced it should be the top priority, so I scoped it properly: native iOS and Android would cost far more than anyone expected, and Engineering proposed a Progressive Web App instead. I presented the estimates alongside the opportunity cost. Leadership chose mobile anyway. I backed the decision fully and we shipped a well-executed app in 2024.

Adoption stayed low no matter how we promoted it. App-store data showed no pattern, so I went to Sales and Customer Success, who talk to customers daily. The insight was uncomfortable: in discovery we'd asked customers *whether* a mobile app mattered — and never asked how they'd use it, or whether they'd rather manage business travel from a desktop. We had validated interest, not need.

The lasting change wasn't the app. It was that Sales and CS adopted outcome-focused interview techniques, and the company started putting real weight on validating a customer problem before committing engineering. That's also how I practice product now.

**Section "What colleagues say"** (eyebrow "WHAT COLLEAGUES SAY", H2 "From 360 feedback, September 2026", two blockquotes in Fraunces with a 2px oak-soft left rule and mono attribution):
- “You are not afraid of taking decisions.” — Peer Product Manager
- When a platform issue blocks bookings for multiple customers, he's the one who establishes the impact and defines what Ops and Support tell customers on behalf of the company. — Support agent, paraphrased
Below, small ink-2 text: The theme across five reviewers: reading across team boundaries, and speaking to the audience in the room. The area they flagged — sharing preliminary guidance before the picture is complete — is the one I'm actively working on.

**Section "What I work with"** (eyebrow "TOOLKIT"; two-column definition list, mono keys):
- Product & delivery — Jira, Jira Product Discovery, Confluence, Miro, Figma, Agile/Scrum
- Data — SQL, Amazon QuickSight
- Technical — REST APIs, Postman, Swagger, JSON, Auth0 — I read and test APIs myself
- Payments — Worldline, Conferma, SAP BRIM, Mobilexpense; BYOC, virtual cards, lodge cards
- Travel APIs — Sabre, Sabre NDC, Booking.com, Expedia, Trainline, Deutsche Bahn
- AI-assisted — OCR receipt capture in production; Copilot and ChatGPT daily; deliberately going deeper in 2026
- Certifications — Product School PMC · Scrum Alliance CSM · Pendo × MTP Product-Led
- Reading — *The Anatomy of the Swipe*, *The PAYTECH Book*, *Bank 4.0* — the 2026 payments list

---

## PAGE: Contact (`/contact`)

**Eyebrow:** CONTACT
**H1:** If you're building in travel, payments, or expense — let's talk.
**Lede:** I'm looking for a Senior Product Manager role where I can own a real product area and learn from product people more senior than me. Email is best; I reply within a day.

Two contact cards (white fill, hairline border):
- EMAIL — jeff.rolling@gmail.com (mailto link) — "For roles, referrals, or a second opinion on a checkout flow."
- LINKEDIN — linkedin.com/in/JeffRolling (external link) — "Where I write about payments and product."

Facts list (mono keys, hairlines):
- Based in — Amsterdam, Netherlands
- Open to — Amsterdam hybrid (2–3 days) or remote across the EU
- Work rights — Dual US / Luxembourg citizen — no sponsorship needed in the EU/EEA or the US
- Languages — English (native)
- Availability — Two months' notice

No contact form. No phone number anywhere on the site.

---

## Follow-up prompts (send one at a time after the first build)

1. "Compare every page against the copy in my first message and list any sentence you changed, added, or dropped. Then restore the original wording exactly."
2. "Check mobile at 390px: the metric strip, the case-study rows, the At-a-glance strip, and the BeforeAfter component must stack to one column with no horizontal scroll."
3. "Add `<title>` and meta descriptions per page: Home 'Jeff Rolling — Product Manager'; case studies '<H1> — Jeff Rolling'; About 'About — Jeff Rolling'; Contact 'Contact — Jeff Rolling'. Add Open Graph title/description using the same text."
4. "Make sure the headshot component shows the JR fallback when /headshot.jpg is missing, then I'll upload the photo to /public/headshot.jpg."
5. "Remove any animation longer than 150ms and any icon library you added. Keep hover underline states only."
