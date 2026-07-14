# Current Website Review & Recommendations

*Prepared for the Otago Orienteering Club committee — 15 July 2026*

## Executive summary

The club's current site (dunedinorienteering.org) is a functional, volunteer-run Google Sites build that keeps enthusiasts served but does the newcomer few favours. Its biggest weakness is that the page called "Events" carries no dated event list and no embedded calendar, so the most common visitor question — what's on next, when, where, and how do I enter? — goes unanswered. Results work but are scattered across year-numbered URLs and Google Drive downloads, several pages are stale, key governance policies are missing, and the half-finished Dunedin-to-Otago rebrand shows everywhere. The best NZ club sites (PAPO and Orienteering Auckland) point the way: a real events calendar with inline entry, a results archive by year, strong newcomer onboarding, and integration with the standard orienteering tools rather than reinventing them. This document assesses the current site, distils what the benchmarks do well, and gives a prioritised plan for the rebuilt Otago Orienteering site — much of which the accompanying draft site already delivers.

## 1. Where the current site stands

The existing site is built on Google Sites, with Google Calendar, Google Forms, and Google Drive doing the heavy lifting behind the scenes. It is a classic zero-cost, volunteer-maintained setup. It works, but it shows its limits.

**Structure and navigation.** The menu mixes plain and jargon-heavy labels — "Events", "OY Events", "MapRun Events", and "Results" sit side by side, so a newcomer must already know club shorthand (OY, MapRun, rogaine, SI) to find their way. Nothing is labelled simply "What's on" or "Beginners start here". Some content is buried three levels deep (the schools league points page under About Orienteering), and the menu label "Training and/or Coaching" is awkward.

**Events handling — the biggest gap.** The `/events` page is a descriptive taxonomy of event *types* (Foot, MTBO, Rogaine, Ski) with no dated list and no embedded calendar. The only concrete dates live on the Home page (for example "Rogaine #2 – Twilight Signal, Sat 25 July" and "Central Otago Rogaine, Sun 16 August"). A calendar-subscription link is offered, but the calendar itself is not shown on the Events page. Registration runs through Google Forms links that are not surfaced alongside the events. The result: a visitor cannot go event → date → fee → register in one flow.

**Results handling.** Results are organised by year, one page per year, but each year is a *separate top-level URL* (`/2026-results`, `/2025-results`, and so on). That means the "current results" address changes every January, breaking bookmarks and inbound links and forcing a manual menu edit each year — and the hierarchy is already inconsistent (2024 appears nested under 2025). There are no native HTML result tables; every result is an external click-out to Google Drive, WinSplits, or Livelox, with the mix varying event to event and formats inconsistent (PDF vs JPG). It is current and fine for enthusiasts, but there is no at-a-glance readable result, and everything depends on Drive share permissions staying public.

**Content freshness.** Home and Results are current (July/August 2026 events present). But the Training/Coaching page is frozen at 2012–2018 content and reads like an archived blog, and the Membership page still references "31st December 2024" and 2025 funding — it was not refreshed for the 2026 year. Base entry fees are not clearly stated anywhere; only equipment-hire fees (SI stick $3, SIAC $5, compass $3) are explicit.

**Design and UX.** The look is default Google Sites — generic, template-driven, little club identity or photography. It reflows acceptably on mobile, but heavy Calendar/Forms/Drive embeds are awkward on small screens and the deep menu collapses into a hamburger that hides an already-confusing hierarchy. The page is framework-heavy (~164 KB of HTML for mostly text).

**The Dunedin / Otago branding split.** The club has voted to rename from Dunedin Orienteering Club to Otago Orienteering Club, but the site sits mid-transition. The domain, page URLs, role emails (`@dunedinorienteering.org`), and the bank account name still say Dunedin, while page titles and body copy increasingly say Otago. This split fragments search results and undermines trust — a visitor cannot tell which name is the real one.

**Missing policies.** For a ~200-member incorporated club affiliated to the national federation, there is a notable governance gap: no visible safety, privacy, safeguarding/child-protection, or constitution documents. The Resources page shows only a framework of headings ("Running an Event", "Downloads") with little substantive linked content.

## 2. How the best NZ club sites do it

PAPO (Peninsula and Plains, Canterbury) and Orienteering Auckland are the NZ benchmarks. Both run the same CMS (SilverStripe) and — more importantly — both integrate the standard orienteering ecosystem rather than building bespoke tooling. Patterns worth copying:

**A real events calendar with inline entry.** Auckland presents events as a single structured HTML table — Date, start time, venue, series (colour-coded) — with a direct **"Enter here" link inline** to Entero (entero.co.nz), the NZ online entry-and-payment platform. One click takes a visitor from seeing an event to paying for it. PAPO runs a dedicated Events section with Upcoming Events plus a full Event Calendar, and spins up per-event microsites for majors so the core site stays clean.

**Results archived by year.** Auckland buckets results cleanly by year (`/results/2026/`), each event offering a results file plus a WinSplits link, and series offering cumulative "Series Points" rollups. PAPO adds a database-backed results model and a standalone OY (Orienteer of the Year) season leaderboard app. The simple, reliable pattern to copy is Auckland's: results by year, each event linking out to WinSplits (splits) and RouteGadget (route analysis).

**Newcomer onboarding.** Auckland's "Need to Know" page is best-in-class: event types, the five map colours explained, how to orient a map, a step-by-step first-event walkthrough, safety (clothing, whistle, getting-lost protocol), and landowner etiquette. PAPO frames its About section as "Getting Started" with an explicit "What are the costs" page. This is the single highest-conversion page for a small club.

**Membership.** PAPO uses the Revolutionise Sport portal for member self-service and states benefits up front (roughly 50% event discount, coaching, volunteer VIP points, national affiliation). Auckland uses a restricted members area. Either way, the join path and the fees/benefits are clear.

**Resources and training done cheaply.** Auckland curates a Links page of skills tutorials, control-description guides, and event software, plus a Training section covering MapRun self-directed courses. PAPO keeps its volunteer/organiser documentation in a linked Notion wiki, outside the CMS. Neither club builds and maintains heavy in-house training content — they curate and link.

**Own a durable, linkable home.** Both give members a browsable calendar, a results archive citable years later, a clear join/pay path, and onboarding that converts newcomers — the exact things a Facebook-only presence (like Central Otago's) cannot provide.

## 3. Recommendations for the rebuilt Otago Orienteering site

Prioritised as **must-do**, **should-do**, and **nice-to-have**.

### Must-do

1. **Fix the branding to Otago Orienteering throughout.** Move to the `otagoorienteering.org.nz` domain and make the name consistent across the site, page titles, role emails, and (with the bank) the account name. A half-rebrand costs trust and splits search results.
2. **Give the site a clear information architecture:** About, Events, Results, Resources, Policy, and Contact as the top-level spine. Use plain language and add a "Getting Started / Beginners" entry point so newcomers are not forced to learn club jargon to navigate.
3. **Build a clear "next event → date → fee → register" path.** Present events as a dated calendar/list (Date, time, venue, series), each linking straight to online entry — use **Entero**, the NZ standard, as Auckland does. State the base entry fees (member vs non-member, adult vs junior) plainly, not just equipment-hire fees.
4. **Organise results by year, then by event type,** with stable URLs that do not change annually. Each event links out to WinSplits (splits) and RouteGadget/Livelox (route analysis). Prefer readable HTML rows over PDF/Drive-only downloads so results stay searchable and don't depend on Drive permissions.
5. **Add the missing policies.** Publish safety/health-and-safety, privacy, safeguarding/child-protection, and the constitution on a dedicated Policy page — expected governance for an incorporated, affiliated club.

### Should-do

6. **Point all training and coaching material at Orienteering New Zealand.** Rather than rebuilding and maintaining club training pages (which went stale by 2018 on the current site), the Resources page should link out to ONZ's national training material and skills resources. This is low-maintenance and always current — the same "curate, don't build" approach the benchmark clubs take.
7. **Write a strong Getting Started / Need to Know page** on the Auckland model: event types, map colours, orienting a map, a first-event walkthrough, safety, and landowner etiquette.
8. **Keep the Membership page current and up front:** 2026 fees, discounts, and benefits stated clearly, with a clean handoff to the existing Revolutionise Sport portal.
9. **Adopt a modern, mobile-friendly design** with real club identity and photography, replacing the generic Google Sites template look.

### Nice-to-have

10. **A dated News/blog** for bulletins and results announcements that can feed the Facebook page.
11. **A season standings / "Otago of the Year" leaderboard** if the club runs a points series — even a simple table adds stickiness.
12. **Pull in the Orienteering NZ national events feed** so regional/national events appear without manual upkeep, and keep majors on microsites only if Otago hosts a big event.

## 4. What the draft site already implements

A draft site has been built alongside this review (Jekyll on GitHub Pages) and already addresses much of the plan above:

- **Events as a calendar list with per-event detail pages** — closing the current site's biggest gap and putting dates where visitors expect them.
- **Results grouped by year and then by event type** — the recommended archive structure, on stable URLs.
- **A Resources page that links out to Orienteering New Zealand** for training material — the low-maintenance, always-current approach, rather than club pages that go stale.
- **Policy, About, and Contact pages** — giving the missing governance content a home.
- **A modern, mobile-friendly design** replacing the generic template look.
- **A Sveltia CMS admin** so non-technical committee members can edit content, with multi-user editing and no need to touch code.

The main items still to layer in from the recommendations are the inline online-entry path (Entero), plainly stated base entry fees, and a full Getting Started / Need to Know onboarding page — the highest-value remaining work once the structure is in place.
