# Critical Review: Dunedin / Otago Orienteering Club Website

**URL reviewed:** https://www.dunedinorienteering.org/
**Date of review:** 2026-07-15
**Method:** WebFetch of homepage + ~13 sub-pages, WebSearch, raw-HTML inspection via curl.

> **Naming note:** The club has voted to rename itself from **Dunedin Orienteering Club** to **Otago Orienteering Club**, to reflect a membership now spread across the wider Otago region. The site sits mid-transition: the domain, page URLs, email addresses (`@dunedinorienteering.org`) and bank account name ("Dunedin Orienteering Club") still say Dunedin, while page titles and body copy increasingly say "Otago Orienteering." Search results indicate the site "will be moving to https://otagoorienteering.org.nz soon." This split branding is itself a UX/trust weakness (see below).

---

## 1. Platform / Tech Stack

**The site is built on Google Sites** (the modern, post-2016 version). Confirmed from raw HTML of `/home`:

- `WIZ_global_data` bootstrap object (the Google Sites/Wiz framework fingerprint)
- 6 references to `sites.google.com`
- 11 references to `googleusercontent.com`, 5 to `gstatic.com` (Google asset CDNs)
- Single `viewport` meta tag; no custom `generator` tag; ~164 KB of framework-heavy HTML for a mostly-text page

Corroborating signals across pages: Google Calendar embed, Google Forms for event registration, and Google Drive links used for all downloadable content (results files, permanent-course maps). This is a classic volunteer-run, zero-hosting-cost Google Sites setup.

**Implications of the Google Sites choice:**
- No control over URL structure, meta/SEO, custom design, or analytics beyond what Google Sites exposes.
- Heavy reliance on Google Drive means content lives in a mix of embedded pages and external Drive folders — inconsistent, and dependent on individual Drive share permissions staying correct.
- Migration to a real `.org.nz` domain + CMS is clearly on the club's radar (this is presumably why this review exists).

---

## 2. Site Structure / Navigation / Information Architecture

The site uses the standard Google Sites left/top navigation. Menu items and observed URLs:

| Menu item | URL | Notes |
|---|---|---|
| Home | `/home` | Landing page, upcoming events + name-change news |
| About Orienteering | `/about-orienteering` | What the sport is; beginner intro |
| — Age Groups | `/about-orienteering/age-groups` | |
| — Information for Schools | `/about-orienteering/information-for-schools` | |
| — — School's League Points Calculation | `/about-orienteering/information-for-schools/school-s-league-courses-points` | Deeply nested (3 levels) |
| — Permanent Courses | `/about-orienteering/permanent-courses` | Ross Creek, Chingford Park, Naseby Sandpit |
| Events | `/events` | Descriptive overview only, no dated list |
| — OY Events | `/events/oy-events` | Format + points rules |
| — Event Fees | `/events/fees` | Hire fees; base fees not clearly shown |
| — Out of Town Maps | `/events/out-of-town-maps` | (not fetched) |
| Results | `/2026-results` | Current year; historical 2010–2025 as sub-pages |
| MapRun Events | `/maprun-events` | Virtual/GPS courses |
| Membership | `/membership` | Links out to RevolutioniseSPORT |
| Committee & Contacts | `/committee` | Officers + roles |
| Club eMail Group | `/club-email-group` | (not fetched) |
| Resources | `/resources` | Event-organising guides + downloads |
| Training and/or Coaching | `/training` | Historical coaching write-ups |
| Club History | `/club-history` | 1984–2024 event history |

**IA weaknesses:**
- **Results uses year-numbered top-level URLs** (`/2026-results`, `/2025-results`, `/2024-results` …). This means the "current results" URL changes every year, breaking bookmarks and inbound links, and forcing a menu edit each January. `/2024-results` is even nested oddly under `/2025-results/2024-results` in one search hit — inconsistent hierarchy.
- **Deep nesting** under About Orienteering (3 levels to the schools points calc page) buries content.
- **Overlapping/ambiguous menus:** "Events" vs "OY Events" vs "MapRun Events" vs "Results" — a newcomer must already understand club jargon (OY, MapRun, rogaine) to navigate. Nothing labelled simply "What's on / Upcoming."
- Menu label "Training and/or Coaching" is awkward phrasing.

---

## 3. How Events Are Presented

**Weak — this is the site's biggest functional gap.**

- The **`/events` page contains NO dated event list and NO embedded calendar.** It is purely a *descriptive taxonomy* of event *types*: Foot Orienteering (Club Classic OY, Summer/Schools Series, Sprint, Championships), Mountain Bike Orienteering (Alexandra, Naseby), Rogaines (4–5 event series), and Ski Orienteering (Snow Farm, Wanaka).
- A **calendar-subscription link** ("add the club calendar to your personal calendar app") is offered, but the calendar is **not embedded on the Events page** — the user has to subscribe externally to see actual dates. A Google Calendar embed apparently lives on the **Home** page instead, which is the wrong place for someone browsing "Events."
- **The only concrete dated events are on the Home page**, e.g.:
  - "School series prizegiving — Sat 25th July 4pm"
  - "Rogaine #2 – Twilight Signal — Sat 25th July" (5:30–7pm, 90-min night event)
  - "Central Otago Rogaine — Sun 16th August"
- **Registration:** handled via Google Forms links, but these are not surfaced on the Events overview page. A user cannot go from "Events" → see a date → register in one flow.

**Pain point:** the single most common visitor question — *"What's the next event, when and where, and how do I enter?"* — is not answered on the page called "Events." Dates, calendar, and registration are scattered across Home, an external calendar subscription, and Google Forms.

---

## 4. How Results Are Presented

- **Organised by year**, one page per year, `/2010-results` through `/2026-results`, reachable via sidebar links.
- Within a year, grouped by category: "2026 School Series," "Other Events" (e.g. Halloween event, Queens Drive trial), "Rogaines," "Central Otago events," "Waitangi Weekend" (a multi-day jubilee event, Feb 6–8), and "OY Events."
- **No native HTML result tables.** Every result is an **external link**:
  - **Google Drive** links to downloadable result files (format not standardised — likely PDF/HTML/spreadsheet per event)
  - **WinSplits** (splits analysis) links
  - **Livelox** (route/GPS visualisation) links
- This is reasonably current (2026 events present) and functional for enthusiasts, but:
  - **Inconsistent** — each event exposes a different mix of Drive/WinSplits/Livelox depending on what the organiser uploaded.
  - **No at-a-glance results** — every result is a click-out and often a file download rather than a readable web page.
  - Dependent on Google Drive share settings remaining public.

---

## 5. Membership / About / Policy / Resources Coverage

### Membership (`/membership`)
- Fees listed: **Senior $40, Junior $20** (aged 20 or under at 31 Dec — the page says **"31st December 2024," a stale year reference**), **Tertiary $30** (full-time, under 21), **Community Services Card holder $30**, **Family max $100** (two adults + juniors, same address). Under-7s free.
- Three 50% discounts (only one applies): never previously a club member; joining after 30 June; Dunedin residents with ancillary membership elsewhere.
- Join via **RevolutioniseSPORT** (external) — "REGISTER" for new, "RENEW"/"MEMBER LOGIN" for returning. Good that it's a real membership platform; the handoff is a clean external link.
- **Staleness flag:** "31st December 2024" and "2025 funding" references suggest the page wasn't refreshed for the 2026 membership year.

### About Orienteering (`/about-orienteering`)
- Solid beginner intro: "a map based sport where runners try to be the fastest around a marked course… using only a map and compass," "suitable for all fitness and experience levels and for ages from 3 to 83." Notes club founded **1976**, ~200 members, affiliated to NZ Orienteering Federation. Explains course choice ("half a dozen courses," 2 km easy to 13 km hilly, 20–120 min) and low barrier to entry ("No special equipment… Compasses are not necessary for beginners"). This is the strongest, most welcoming page.

### Committee & Contacts (`/committee`)
- President **Ann Bixley**, Secretary **Jeni Pelvin**, Treasurer **Tim Webb** with role-based emails (`president@`, `secretary@`, `treasurer@dunedinorienteering.org`). General `committee@` address, plus **P.O. Box 969, Dunedin**. ~11 committee members and ~15 club roles named (Webmaster Fraser Stephens, Membership coordinator Megan Hall, etc.) — mostly names only, no individual emails. Monthly meetings, "All club members are welcome to attend." Publishing personal names is fine; emails are role-based (good practice).

### Resources (`/resources`)
- A hub aimed at **members organising events**: "Running an Event" → Planning, Controlling, Organising, SportIdent; plus "Downloads" → "DOCument" and "Orienteering stuff for sale."
- **Thin/unclear:** the fetched page showed the *framework* (headings) but little substantive linked content. No visible club policies (safety, health-and-safety, privacy, child-protection/safeguarding, constitution) — a notable governance gap for a ~200-member incorporated club.

### Permanent Courses (`/about-orienteering/permanent-courses`)
- Three public permanent courses: **Ross Creek** (two entrances, Burma Rd & Cannington Rd, PDF maps), **Chingford Park** Dunedin (JPG map, board at North Rd entrance), **Sandpit** Naseby (most complete — Foot-O normal + rogaine, MTBO normal + rogaine, all JPG via Google Drive). Also mentions supported courses at Berwick Lodge, Tirohanga Camp, Sutton Camp (institutional).
- **Inconsistent formats** (some PDF, some JPG) and all gated behind Google Drive links.

### Event Fees (`/events/fees`)
- Clearly lists **hire fees**: SI stick $3/course ($50 replacement), SIAC chip $5/event ($150 replacement), thumb compass $3/course ($25 replacement). Bank transfer preferred to "Dunedin Orienteering Club, 12-3150-0152097-00."
- **Gap:** the actual **base entry fees** (member vs non-member, adult vs junior) were not clearly presented on the page — it references "Championship and Special Events fees set separately" and a bundle discount but not the core price a first-timer needs.

### MapRun Events (`/maprun-events`)
- Genuinely useful: explains the MapRun smartphone app ("uses the GPS on your smartphone… your phone beeps and vibrates" near a control). Courses grouped into **Line**, **Score/Rogaine** (45–180 min), and **Scatter** courses across Dunedin/Central Otago locations (Anderson's Bay, Calton Hill, Maori Hill, Ross Creek, Octagon, Alexandra, Mosgiel, etc.). Setup instructions, a safety note ("Please shadow kids younger than about high school age…"), and troubleshooting. Maps via Google Drive; admin contact "Moss."

### Club History (`/club-history`)
- Covers 1984–2024: 1984 Asia Pacific Carnival (Naseby), 1989 Moro South Island 7 Day Festival, 1998 & 2010 National Champs, through to 2024 South Island Champs 3-day (school sprints + peninsula memorial event). Reasonably current, event-list style with limited narrative/context.

### Training and/or Coaching (`/training`)
- **Stale.** Content documents coaching sessions **2012–2018** (Jeni Pelvin, Antonia Wood; compass bearings, map folding, route choice). Good evergreen tip quoted ("Where Am I? Where Am I Going? What Will I See Along The Way? How Will I Know When I've Gone Too Far?") and references Jean Cory-Wright's guide — but nothing after 2018, no videos, no downloadable drills. Reads like an archived blog rather than a current coaching resource.

---

## 6. Content Currency Summary

| Page | Currency | Evidence |
|---|---|---|
| Home | Current | July/Aug 2026 events, name-change news |
| Results | Current | 2026 results present |
| Club History | Fairly current | Through 2024 |
| About Orienteering | Evergreen/OK | No dated content |
| Membership | **Stale** | "31st December 2024," "2025" funding refs |
| Training/Coaching | **Very stale** | Newest content 2018 |
| Events | **Undated/generic** | No dated list at all |
| Resources | Thin/unclear | Framework only, no policies |

---

## 7. Design / UX / Mobile / Visual Appeal

- **Visual design:** default Google Sites — generic, template-driven, minimal branding personality. Functional but bland; no distinctive club identity, limited photography beyond the coaching page.
- **Mobile:** Google Sites is responsive by default, so it will reflow acceptably on phones, but heavy Google Calendar/Forms/Drive embeds can be awkward on small screens, and the deep multi-level menu collapses into a hamburger that hides the (already confusing) hierarchy.
- **Performance:** ~164 KB framework-heavy HTML for what is largely text; Wiz/Google Sites adds JS overhead disproportionate to the content.
- **SEO/branding:** no custom generator/meta control; the Dunedin-vs-Otago naming split will fragment search results and confuse users about which is the "real" name.

---

## 8. Specific Weaknesses & User Pain Points (prioritised)

1. **No upcoming-events list or embedded calendar on the Events page.** The #1 visitor need — next event, date, location, entry — is not answered where expected. Dates live on Home; the calendar must be subscribed to externally.
2. **No clear "how do I enter my first event" path.** Registration (Google Forms) and base entry fees are not surfaced together; a beginner can't go event → date → fee → register in one flow.
3. **Year-numbered result URLs** (`/2026-results`) break bookmarks annually and require manual menu maintenance each year.
4. **Everything downloadable is a Google Drive click-out** (results, maps) with inconsistent formats (PDF vs JPG) and fragile share-permission dependency. No inline result tables.
5. **Split Dunedin/Otago branding** across domain, URLs, emails, bank account, and body text erodes trust and clarity mid-rebrand.
6. **Stale pages:** Training/Coaching frozen at 2018; Membership year references stuck at 2024.
7. **Missing governance/policy content:** no visible safety, privacy, safeguarding/child-protection, or constitution documents on Resources — expected for a ~200-member affiliated club.
8. **Jargon-first navigation** (OY, MapRun, rogaine, SI) with no plain-language "Beginners start here / What's on" entry point.
9. **Deep nesting** (3 levels) buries schools content.
10. **Base event fees not clearly stated** — only equipment-hire fees are explicit.

---

## 9. Notes / Limitations of This Review

- Pages fetched and reviewed: Home, About Orienteering, Permanent Courses, Events, OY Events, Event Fees, Results (2026), MapRun Events, Membership, Committee & Contacts, Resources, Club History, Training.
- **Not directly fetched:** `/events/out-of-town-maps`, `/club-email-group`, `/about-orienteering/age-groups`, `/about-orienteering/information-for-schools`, and individual historical results year pages (2010–2025) — inferred from navigation/search only.
- Content was read via WebFetch's markdown conversion, so exact on-page layout, images, and embed behaviour (esp. the Google Calendar embed's placement) are described from extracted text, not pixel inspection. A live browser/mobile pass would confirm responsive behaviour and embed rendering.
- Fee "base rate" absence may reflect WebFetch truncation rather than a true omission — worth a manual check.

## Sources
- [Otago Orienteering – Home](https://www.dunedinorienteering.org/home)
- [Events](https://www.dunedinorienteering.org/events) · [OY Events](https://www.dunedinorienteering.org/events/oy-events) · [Event Fees](https://www.dunedinorienteering.org/events/fees)
- [2026 Results](https://www.dunedinorienteering.org/2026-results) · [2025 Results](https://www.dunedinorienteering.org/2025-results) · [2024 Results](https://www.dunedinorienteering.org/2025-results/2024-results)
- [About Orienteering](https://www.dunedinorienteering.org/about-orienteering) · [Permanent Courses](https://www.dunedinorienteering.org/about-orienteering/permanent-courses)
- [Membership](https://www.dunedinorienteering.org/membership) · [Committee & Contacts](https://www.dunedinorienteering.org/committee)
- [MapRun Events](https://www.dunedinorienteering.org/maprun-events) · [Resources](https://www.dunedinorienteering.org/resources) · [Training](https://www.dunedinorienteering.org/training) · [Club History](https://www.dunedinorienteering.org/club-history)
