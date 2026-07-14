# Website Publishing Options — Review & Recommendation

**For:** Otago Orienteering Club committee
**Prepared:** July 2026
**Status:** For decision

---

## Executive summary

The club needs a website that several non-technical volunteers can update themselves, without hiring anyone and without depending on a single person forever. We reviewed seven realistic options and grouped them into two families: free "static site + admin panel" builds hosted on GitHub, and paid all-in-one hosted builders like WordPress and Squarespace.

**Recommendation: continue with the draft already built — a Jekyll static site on GitHub Pages with the Sveltia CMS admin panel at `/admin`.** It costs nothing per year (only a domain name, ~NZD $20–40/yr), never locks the club in, and gives several volunteers a simple web-form editor. The one condition is that the club has, or can borrow, one technical helper for the initial setup. If that condition ever fails, the clear fallback is **WordPress.com Premium (~NZD $160/yr)**.

---

## The key requirement

Everything below is judged against one thing the committee agreed matters most:

> **Several non-technical volunteers must be able to add and change content — events, results and news — through a simple admin interface, without touching code, and without breaking the site.**

Nice design, low cost and no lock-in all matter, but multi-person, safe, non-technical editing is the deciding factor.

---

## The core trade-off

Every option falls into one of two families. The real decision is which family fits the club.

**Family A — Git-based static site + a friendly CMS admin layer** (the draft's approach: Jekyll + GitHub Pages + Sveltia CMS)
- Near-zero cost (~NZD $0/yr plus a domain), no lock-in, fast and secure.
- Editors log in and use simple web forms; content is saved as plain files the club fully owns.
- **The catch:** one technical person must set it up once, and each editor needs a free GitHub account.

**Family B — All-in-one hosted builder** (WordPress.com, Squarespace, Wix, Google Sites)
- No technical setup; editors log into a friendly managed dashboard.
- **The catch:** an ongoing annual fee, more lock-in, and — for self-hosted WordPress — a real maintenance burden.
- This is the safer family for a club with no technical volunteer at all.

In short: Family A trades a bit of upfront technical help for zero cost and full ownership. Family B trades money and some lock-in for "it just works" with no technical help needed.

---

## Comparison table

Costs are ballpark annual figures in NZD (USD prices converted at ~1 USD = 1.65 NZD, GST usually added). A domain name (~NZD $20–40/yr) is an extra cost on every option and is the one thing the club should own itself regardless of platform.

| Platform | Non-tech admin | Multi-user & roles | Cost (NZD/yr) | Setup | Maintenance | Events / Results / Galleries | Lock-in |
|---|---|---|---|---|---|---|---|
| **Sveltia CMS** + GitHub/Cloudflare Pages | Very good | Yes — via GitHub login, no identity server | ~$0 + domain | Technical, one-off | Low | Good / Good / **Very good** | **None** |
| **Decap CMS** + GitHub Pages/Netlify | Good | Yes but coarse; Netlify login now deprecated | ~$0 + domain | Technical, one-off (fiddly) | Low | Good / Good / Good | **None** |
| **TinaCMS** | Good (visual) | Paid beyond ~2 users | $0 free tier → ~$575+ | High (needs a backend server) | Medium | Good / Good / Good | Low content / cloud tie-in |
| **WordPress.com** (managed) | Excellent | **Excellent** — 5 built-in roles | ~$80–500 | Easy | Low (managed) | Good / Good / Very good | Low–Moderate |
| **WordPress self-hosted** | Excellent | **Excellent** — 5 built-in roles | ~$80–240 | Moderate | **High** (you patch it) | Good / Good / Very good | **Low** (own export) |
| **Wix** | Very easy | Yes (roles) | ~$265–500 | Very easy | None (managed) | Good / OK / Good | **High** |
| **Squarespace** | Very easy (guardrails) | Yes (contributor roles) | ~$300–500 | Very easy | None (managed) | **Very good** / OK / **Very good** | Moderate |
| **Google Sites** | **Simplest** | Editor/Viewer sharing (no fine roles) | **Free** + domain | Trivial | None (managed) | OK (embed Calendar) / Basic / Basic | Moderate |

---

## Top 3 recommendations

### 1. Sveltia CMS + GitHub Pages (or Cloudflare Pages) — recommended

**What it is:** A modern, friendly admin panel bolted onto a free static website. Volunteers go to `/admin`, log in with a free GitHub account, and edit events, results and news through simple web forms. Their changes save as plain text files in the club's own GitHub repository. This is exactly what the draft site already does.

**Who it suits:** A club that has — or can borrow — one technical volunteer for the one-off setup, and wants zero ongoing cost with full ownership of its content.

**Pros:**
- Free: ~NZD $0/yr for software and hosting (domain is the only cost).
- No lock-in — content is plain files the club owns and can move anywhere.
- Best media/gallery experience of the free options, which suits a photo-heavy orienteering club.
- Each editor logs in with their own GitHub account; the repo's collaborator list is the access control. Draft → review → publish workflow is supported.
- Avoids the deprecated "Netlify Identity" login problem that now hurts the older Decap option.

**Cons:**
- Needs one technical person to do the initial wiring (config file plus a lightweight login handler).
- Each editor needs a free GitHub login (a minor hurdle for non-technical volunteers).
- Younger project with a smaller community than WordPress.

**Rough annual cost:** ~NZD $0 plus domain (~$20–40/yr).

### 2. WordPress.com Premium — safest fallback

**What it is:** The mainstream, fully managed website platform. Volunteers log into a familiar dashboard and edit with no code. WordPress.com hosts and patches everything.

**Who it suits:** A club with no reliable technical volunteer that will happily pay a modest annual fee for a resilient, familiar system that depends least on any one person.

**Pros:**
- Best-in-class multi-editor roles: Administrator, Editor, Author, Contributor, Subscriber — so a news volunteer can publish while a results volunteer only edits their section, all without seeing anything technical. This nails the club's key requirement directly.
- Managed hosting means the platform handles updates, backups and security.
- Events (via The Events Calendar plugin), results tables and galleries are all well supported.

**Cons:**
- Ongoing annual cost.
- Full plugin freedom needs the pricier Business tier (~NZD $500/yr); Premium is enough for most club needs.

**Rough annual cost:** ~NZD $160/yr (Premium). Personal tier ~$80/yr; Business ~$500/yr.

### 3. Squarespace — prettiest with least effort

**What it is:** A polished, template-driven hosted builder. Clean, guided editing with guardrails so volunteers are unlikely to break the design.

**Who it suits:** A club that wants the best-looking site for the least effort, has no technical volunteer, and accepts an annual fee plus some lock-in.

**Pros:**
- Professional look out of the box with minimal effort.
- More editing guardrails than Wix, so volunteers won't wreck the layout.
- Contributor roles, a built-in Events collection, and excellent galleries. Fully managed, near-zero maintenance.

**Cons:**
- Ongoing cost.
- Limited data portability — design and structured content don't transfer out cleanly.

**Rough annual cost:** ~NZD $300–500/yr (Basic ~$370/yr, billed annually in NZD with GST).

**Honourable mention — Google Sites (free):** the simplest multi-editor experience of all — sharing works exactly like a Google Doc. Genuinely free. Choose this only if the budget is zero *and* the club accepts a basic, generic look (embed a Google Calendar for events, Google Sheets for results). Unbeatable on simplicity and cost, weakest on features.

---

## Why the draft was built the way it was

The draft site is a **Jekyll static site on GitHub Pages with a Sveltia CMS admin panel at `/admin`**. Several non-technical committee members can log in with GitHub and edit events, results and pages through web forms. This was a deliberate choice, not an accident:

- It is the **free, no-lock-in** option — no annual platform fee, and all content stays in the club's own repository as plain files.
- Sveltia was chosen over the older Decap CMS because Sveltia logs in **directly against GitHub** and needs no separate identity server. The alternative, Decap, historically relied on Netlify's login service, which has been **deprecated for new sites (2025–26)** — a genuine headache to build on today.
- Static sites on GitHub Pages are fast, secure and effectively maintenance-free — well suited to a small volunteer club with turnover.

**The "no techie available" path:** the entire value of Family A rests on one technical volunteer doing the initial setup. If that person is unavailable now, or leaves and can't be replaced, editing still works but any structural change becomes hard. In that situation the club should move to Family B — realistically **WordPress.com Premium** — where the platform provider handles all the technical work in exchange for the annual fee.

---

## What to avoid, and why

- **TinaCMS** — needs a backend server (won't run on plain GitHub Pages), has the highest technical bar of the free options, and charges once you exceed ~2 editors (~NZD $575+/yr). Overkill for a simple club site.
- **Self-hosted WordPress (WordPress.org)** — carries a **high ongoing maintenance burden**: updates, backups, security and spam are the club's problem. That is a real risk for a volunteer group with turnover. If WordPress is chosen, use managed **WordPress.com** instead.
- **Wix** — ongoing cost, prices that creep up after year one, **heavy lock-in** (no meaningful content export), and a free-form drag-and-drop canvas that makes it easy for a well-meaning volunteer to break the layout.
- **Weebly** — stagnant and declining, no advantage over the options above.
- **Free tiers with ads/subdomains** (Wix free, WordPress.com free) — not suitable for a real club site.

---

## Recommendation for Otago Orienteering Club, and next steps

**Continue with the draft: Jekyll + GitHub Pages + Sveltia CMS.** It meets the key requirement — several non-technical volunteers editing events, results and news through simple forms — at ~NZD $0/yr with no lock-in, and the work is already underway. The single dependency is having one technical helper for setup and occasional structural changes.

**Decision guide:**
- Keep the GitHub Pages site and have a technical helper → **Sveltia CMS** (recommended).
- No technical helper, want it to "just work" for years → **WordPress.com Premium (~$160/yr)**.
- Want the prettiest site for least effort and don't mind paying → **Squarespace (~$300–500/yr)**.
- Zero budget, keep it dead simple → **Google Sites (free)**.

**Next steps:**
1. Confirm the club has a technical volunteer willing to own the Sveltia/GitHub Pages setup and be available for occasional help. If yes, proceed with the draft.
2. Register and own a club domain name (~NZD $20–40/yr) — do this regardless of platform.
3. Add 3–4 committee editors as GitHub collaborators and have each create a free GitHub account.
4. Run a short hands-on session so editors can add a test event, a results entry and a news post through `/admin`.
5. Write a one-page "how to edit the website" guide so the club is not reliant on any single person's memory.
6. If step 1 fails now or in future, switch to **WordPress.com Premium** as the pre-agreed fallback.
