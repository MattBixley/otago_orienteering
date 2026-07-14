# NZ Orienteering Club Websites — Benchmark Research

Research date: 2026-07-15. Purpose: benchmark best-practice NZ club sites to inform a
rebuilt Otago Orienteering website.

Sites reviewed:

- **PAPO** — Peninsula and Plains Orienteers (Canterbury): https://papo.org.nz/
- **Auckland** — Auckland Orienteering Club Inc: https://orienteeringauckland.org.nz/
- **Central Otago** — COOrienteering (Facebook only): https://www.facebook.com/COOrienteering/

> Note: `papo.org.nz` blocks automated fetchers (HTTP 403 on WebFetch); its content was
> retrieved via `curl` with a browser user-agent and via web search. The Facebook page is
> login-walled, so its analysis is based on the page metadata and general knowledge of how
> small clubs use Facebook-only presences.

---

## Headline finding

**Both PAPO and Auckland run the same CMS — SilverStripe** (confirmed via
`<meta name="generator" content="SilverStripe">` in both sites' HTML). This is effectively
a de-facto shared platform among established NZ orienteering clubs. They differ mainly in
which third-party services they bolt on for entries, results, and membership. This matters:
a rebuilt Otago site does not have to reinvent the event/results/membership plumbing —
the ecosystem already has standard tools (Entero, WinSplits, RouteGadget, Revolutionise,
Orienteering NZ event feeds) that these clubs simply integrate.

---

## 1. PAPO (Peninsula and Plains Orienteers)

### Platform / tech
- **CMS: SilverStripe** (`<meta name="generator" content="SilverStripe - http://silverstripe.org">`).
- Fronted by **Cloudflare** (`server: cloudflare`).
- **Design credit** (footer): `katiebolt.com` — a professional web designer, i.e. this is a
  bespoke SilverStripe build, not an off-the-shelf template.
- Footer: `© Copyright Peninsula and Plains Orienteers 2026`.
- **Membership: Revolutionise Sport** (`revolutionise.com.au/papo/account/`) — an
  Australian club-management SaaS handling the member database and logins.
- **Results tooling: WinSplits Online + RouteGadget** (standard orienteering tools).
- **Helpers' documentation: a Notion site** (`papo-club.notion.site`) linked from the nav —
  volunteer/organiser wiki kept outside the CMS.
- **Custom event/series engine**: URLs like `/events/results/129/oy3-waikari` and
  `/series/view/47/Boyle-2026` are numeric/database-driven — PAPO has a real events+results
  data model, not just static pages.
- **Per-event microsites on subdomains**: `how.papo.org.nz` (Heights of Winter),
  `oypoints.papo.org.nz` (OY leaderboard app), historical ones like `qbw2017.papo.org.nz`
  and `mtbo2014.papo.org.nz`. Big events get their own site; the club site stays clean.

### Navigation structure (full menu)
```
Home
Events (/papo-events/)
  ├─ Upcoming Events
  ├─ Event Calendar
  ├─ Results
  ├─ OY Leaderboard        → oypoints.papo.org.nz/leagues/PAPO (external app)
  ├─ South Island major events
  ├─ Heights of Winter 2026 → how.papo.org.nz (microsite)
  ├─ NZ Secondary School Champs 2026 → external
  ├─ Boyle River weekend 2026 → /series/view/47/Boyle-2026
  └─ Other Events
News (/news/)
Getting Started (/faq/)
  ├─ About orienteering
  ├─ What are the costs
  └─ Help topics & resources
Club Info (/club-info/)
  ├─ Join Us
  ├─ Maps
  ├─ Orienteer of the Year
  ├─ Helping at an Event
  ├─ Organising an Event
  ├─ Helpers' Wiki        → Notion (external)
  ├─ PAPO Apparel
  ├─ VIP Points
  ├─ Change my membership details → Revolutionise (external)
  └─ Coach-in-Residence
Permanent Courses (/permanent-courses/)
Contact Us
```

### How they handle each area
- **About**: framed as **"Getting Started"** (newcomer-first) plus `/about-us/`. The FAQ
  doubles as the about/onboarding hub — "About orienteering", "What are the costs".
- **Events / calendar**: dedicated Events section with **Upcoming Events**, a full
  **Event Calendar** (HTML table: Date, Map/Location columns), and links out to major-event
  microsites and the national schools champs. Pre-entry model with electronic payment;
  entries close Wednesday before a weekend event.
- **Results**: **chronological list by event date**, each with "View results" (native
  results page) **plus "View results on Winsplits"** and RouteGadget route analysis.
  Season standings handled separately via the **OY Leaderboard** app (subdomain).
- **Resources / training**: under Getting Started ("Help topics & resources") and Club Info
  ("Coach-in-Residence", "Organising an Event", the Notion Helpers' Wiki).
- **Policies**: no prominent standalone policy/privacy/safeguarding pages found in nav.
- **Membership**: "Join Us" page + external **Revolutionise** member portal for
  self-service detail changes. Member benefits clearly stated (≈50% event discount, coaching,
  VIP volunteer points → free events, ONZ affiliation).
- **News**: a proper **`/news/` blog** with dated post slugs (e.g. results announcements,
  event bulletins, an in-memoriam post).

### Standout features
- Numeric, database-backed **events + results + series** model (not static pages).
- **OY (Orienteer of the Year) season leaderboard** as its own app.
- **VIP points** gamification rewarding volunteers with free events.
- **Notion Helpers' Wiki** for organisers — low-effort volunteer documentation.
- **Per-event microsites** for majors, keeping the core site uncluttered.
- Clear costs/FAQ funnel aimed squarely at newcomers.

---

## 2. Auckland Orienteering Club

### Platform / tech
- **CMS: SilverStripe** (`<meta name="generator" content="SilverStripe - https://www.silverstripe.org">`).
- **Server: Apache** (self/community-hosted, no Cloudflare).
- No visible design credit or footer copyright in the markup.
- **Entries: Entero** (`entero.co.nz`) — the NZ online entry/payment platform; every event
  in the calendar has an "Enter here" deep link (e.g. `entero.co.nz/evento.php?eventName=fc1-2026`).
- **Results: WinSplits Online** + **PDF** results files (`/assets/2026/...pdf`).
- **Training: MapRun / MapRunF** integration (`/resources/training/training-using-maprunf/`).

### Navigation structure (full menu)
```
Home
Events            → /events/summernav/  (SummerNav, Forest Cup, Night Street Series…)
Results (2026)    → /results/2026/
Club Members Pages (restricted)
About Us          → /about-us/about-the-club/  (+ News Archive)
Getting Started   → /getting-started/what-is-orienteering/  (+ "Need to Know")
Resources         → /resources/map-locations/  (+ Training / MapRunF)
Juniors & Schools → /juniors-and-schools/schools/
Contact Us
```

### How they handle each area
- **About**: `About Us → About the Club`, with a **News Archive** sub-page.
- **Events / calendar**: a single, well-structured **HTML table** — Date, start time, venue,
  series name, colour-coded series, **direct Entero "Enter here" links inline**. Series
  include SummerNav (evening), Forest Cup, Night Street Series.
- **Results**: **organised by year** (`/results/2026/`). Each event row offers a **PDF** of
  results **plus a WinSplits** link, and series offer cumulative **"Series Points"** PDFs.
  Simple, reliable, but PDF-centric (not queryable HTML tables).
- **Resources / training**: strong. A **Links** page curates skills training (control
  descriptions, map symbols, interactive quizzes, compass tutorials, RouteGadget), regional
  and national/international club links, coaching, and event software (OCAD, SportIdent).
  Separate **Training** section covering MapRun.
- **Getting Started / "Need to Know"**: an excellent, thorough newcomer page — event types,
  the five map colours explained, how to orient a map, step-by-step event procedure, safety
  (clothing, hydration, whistle, getting-lost protocol, fence crossing), and landowner
  etiquette ("no litter, no smoking, no fires").
- **Juniors & Schools**: a dedicated top-level section — signals a clear youth pathway.
- **Policies**: none prominent in nav.
- **Membership**: handled via a restricted **"Club Members Pages"** area; less self-service
  than PAPO's Revolutionise portal.
- **News**: "What's New?" on the homepage + a News Archive under About.

### Standout features
- **Inline "Enter here" (Entero) links directly in the events table** — one click from
  seeing an event to paying for it.
- **Results cleanly bucketed by year** with WinSplits + series-points rollups.
- **Best-in-class newcomer onboarding** ("Need to Know" + curated skills/training links).
- Dedicated **Juniors & Schools** pathway.
- **MapRun** self-directed training events (train any time, no event needed).

---

## 3. Central Otago Orienteering (Facebook only)

- **No website** — presence is a Facebook Page (`facebook.com/COOrienteering/`,
  "Central Otago Orienteering | Alexandra"). Page content is login-walled to automated
  access, so specifics couldn't be scraped.
- **Typical Facebook-only club pattern** (and its limitations):
  - Content is a reverse-chronological feed: event announcements, results-as-photos,
    map snapshots, casual updates. Good for reach and zero maintenance.
  - **No durable structure**: no browsable events calendar, no year-by-year results archive,
    no searchable resources, no membership/join flow, no permanent "getting started" page.
  - **Discoverability is poor** for non-Facebook users and for Google; old posts are
    effectively unfindable.
  - **No data model**: results live as images or comments, not tables or links to
    WinSplits/RouteGadget.
- This is exactly the gap a rebuilt Otago site should close: keep social for reach, but own
  a structured, searchable, linkable home for events, results, and onboarding.

---

## 4. Comparison — what PAPO & Auckland do better than a typical small club

| Capability | PAPO | Auckland | Typical small club (e.g. FB-only) |
|---|---|---|---|
| Real CMS (editable pages) | SilverStripe | SilverStripe | None / Facebook |
| Structured events calendar | Yes (table + microsites) | Yes (table) | Feed posts only |
| Online entry + payment | Pre-entry, electronic | **Entero inline links** | None |
| Results archive | By event/date + OY app | **By year** + WinSplits/PDF | Photos in feed |
| Split-time analysis | WinSplits + RouteGadget | WinSplits | None |
| Season standings | OY Leaderboard app | Series Points PDFs | None |
| Newcomer onboarding | FAQ / costs funnel | **"Need to Know" + curated links** | None |
| Membership self-service | **Revolutionise portal** | Members area | None |
| Volunteer/organiser docs | **Notion Helpers' Wiki** | Some | None |
| Juniors/schools pathway | In events | **Dedicated section** | None |
| Discoverability / SEO | Good (own domain) | Good | Poor |

**In short**, both benchmark clubs give members a durable, searchable, linkable home that a
Facebook page can't: a browsable calendar, a results archive you can cite years later, a
clear join/pay path, and onboarding that converts curious newcomers. They achieve this not
by building everything themselves but by **integrating the orienteering ecosystem's standard
services** around a light CMS.

---

## 5. Concrete recommendations for a rebuilt Otago Orienteering site

**Adopt these proven patterns:**

1. **Own domain + a light CMS.** Both benchmarks use SilverStripe, but the CMS choice is
   secondary — pick whatever the maintainer can edit (a modern static/JAMstack or
   WordPress/Astro is fine). The point is: own a real site, keep Facebook for reach only.
2. **Events as data, not prose.** A calendar table with Date, Time, Venue, Series, and an
   inline **"Enter here"** link. Use **Entero** (`entero.co.nz`) for online entry + payment —
   it's the NZ standard and Auckland deep-links straight into it.
3. **Results archived by year** (Auckland's model — simplest and most reliable), each event
   linking to **WinSplits Online** for splits and **RouteGadget** for route analysis. Prefer
   linkable HTML rows over PDF-only where feasible so results stay searchable.
4. **A strong "Getting Started / Need to Know" page** — copy Auckland's structure: event
   types, map colours, how to orient a map, step-by-step first-event walkthrough, safety, and
   landowner etiquette. This is the single highest-conversion page for a small club.
5. **A curated Resources/Links + Training page** — skills tutorials, control-description
   guides, plus **MapRun/MapRunF** permanent/self-directed courses so people can train any
   time without an event.
6. **A clear Join Us / membership page** with fees and benefits stated up front. Consider
   **Revolutionise Sport** (PAPO's choice) for member self-service if the club is large
   enough to warrant it; otherwise a simple form + Entero suffices.
7. **A dated News/blog** for bulletins and results announcements — feeds naturally to the
   Facebook page.
8. **Season standings** (an "Otago of the Year"-style leaderboard) if the club runs a series —
   even a simple points table adds stickiness.
9. **Pull in the national feed**: link to / embed the **Orienteering NZ events listing**
   (`orienteering.org.nz/events/`) so regional/national events appear without manual upkeep.
10. **Keep majors on microsites** (PAPO's subdomain pattern) only if Otago hosts a big event;
    otherwise unnecessary.

**Deliberately skip / keep minimal:** heavyweight membership systems, custom results engines,
and bespoke calendars are overkill for a small club — lean on Entero + WinSplits + RouteGadget +
MapRun and spend effort on the newcomer onboarding and the calendar/results plumbing instead.

### Standard ecosystem services to integrate
- **Entero** (`entero.co.nz`) — online entry + payment.
- **WinSplits Online** — split-time results.
- **RouteGadget** — route-drawing / comparison.
- **MapRun / MapRunF** — self-directed/permanent training courses.
- **Revolutionise Sport** — optional membership management.
- **Orienteering NZ** events/results feeds — national listings.

---

## Sources
- https://papo.org.nz/ and subpages (club-info, faq, papo-events, news) — via curl + search
- https://orienteeringauckland.org.nz/ and subpages (results, getting-started, resources)
- https://www.orienteering.org.nz/nz-orienteering-clubs/
- https://www.facebook.com/COOrienteering/ (metadata only; login-walled)
