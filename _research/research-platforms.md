# Website Platform Research — Otago Orienteering Club

**Prepared:** July 2026
**Context:** Small, volunteer-run sports club (Otago Orienteering Club, NZ). A draft site is being built as a **GitHub Pages static site**.
**Key requirement:** a simple admin interface so **several non-technical volunteers** can add and change events, results and news **without touching code**. Multi-user content editing is essential.

> **Currency note:** figures are ballpark annual costs in **NZD**. Where a platform prices in USD, converted at ~1 USD = 1.65 NZD (mid-2026), GST usually added. A domain name (~NZD $20–40/yr) is an extra cost on every option, and is the one thing you should own yourself regardless of platform.

---

## The core trade-off

There are two families of solution, and the club's decision really comes down to which family:

1. **Git-based static site + a friendly CMS admin layer** (Decap, Sveltia, TinaCMS on GitHub Pages / Netlify / Cloudflare Pages). Near-zero cost, no lock-in, fast and secure — but needs **one technical person to set it up once**, and each editor needs a (free) GitHub account. Great fit because the club has already started down the GitHub Pages path.

2. **All-in-one hosted builders** (WordPress, Wix, Squarespace, Google Sites). No technical setup, editors log into a friendly dashboard — but ongoing cost, more lock-in, and (for WordPress self-hosted) maintenance. This is the "safest" family for a group with no technical volunteer at all.

The single most important criterion — *several non-technical people editing safely* — is met best by **WordPress-style role-based dashboards** and, among the git options, by **Sveltia CMS** (a modern, friendly editor that fits the club's existing static site).

---

## Platform evaluations

### 1. Decap CMS (+ GitHub Pages / Netlify)

Formerly Netlify CMS. MIT open-source, git-based CMS. Content is stored as Markdown/YAML in the repo; the CMS is a single-page admin at `/admin` that commits to Git for the editor.

- **Admin interface:** Clean form-based editor with an **Editorial Workflow** (drafts → review → publish via Git branches/PRs). Genuinely usable by non-technical editors once configured. Field types cover events, results tables (repeatable list fields) and image/gallery uploads.
- **Multi-user / roles:** Multiple editors supported. Auth is the catch: on **Netlify** it historically used Netlify Identity + Git Gateway so editors log in with email/password and never see GitHub — but **Netlify Identity is now deprecated / discouraged for new sites** (2025–26). On **GitHub Pages** you must run your own OAuth provider (a small Cloudflare Worker or similar) and editors log in with a GitHub account. No fine-grained roles beyond "can commit / can approve"; permissions inherit from the Git host.
- **Cost:** Software free. Hosting free (GitHub Pages / Netlify free tier / Cloudflare Pages). **~NZD $0/yr** plus domain.
- **Setup / maintenance:** One-off technical setup (config file + OAuth). Low ongoing maintenance. Netlify Identity deprecation is a real headache for new builds — the reason Sveltia now wins.
- **Suitability:** Good for events (collections), results-by-year (folder/collection per year), galleries (media library). Tables are entered as structured lists, not free-form spreadsheets.
- **Lock-in / portability:** Excellent — content is plain Markdown in your own Git repo. Zero lock-in.
- **Pros:** Free, no lock-in, mature, works with the club's existing GitHub Pages plan.
- **Cons:** OAuth setup is fiddly; Netlify Identity deprecation; UI feels dated next to Sveltia; needs a technical champion.

### 2. Sveltia CMS (+ GitHub Pages / Cloudflare Pages)

A modern, **drop-in replacement for Decap** (same config format) rebuilt in Svelte. This is the current best-in-class git CMS for new static-site builds.

- **Admin interface:** Noticeably faster and friendlier than Decap — better media library (with folder support, image optimisation), dark mode, i18n, mobile-friendly. Same form-based editing model, easy for non-technical volunteers.
- **Multi-user / roles:** Authenticates **directly against GitHub/GitLab OAuth** — no separate identity server needed, which sidesteps the Netlify Identity problem entirely. Each editor uses their own free GitHub account; the repo's collaborator list *is* your access control. Editorial workflow (draft/review/publish) supported.
- **Cost:** Free, open-source. Host on GitHub Pages or Cloudflare Pages free. **~NZD $0/yr** plus domain.
- **Setup / maintenance:** Slightly simpler than Decap because no Identity/Git Gateway plumbing. Still a one-off technical setup (config + a lightweight OAuth handler, or use its built-in options). Very low ongoing maintenance.
- **Suitability:** Same strengths as Decap for events / annual results collections / galleries, with a materially better media/gallery experience — relevant for a photo-heavy club site.
- **Lock-in / portability:** Excellent — plain Markdown in your Git repo, and it's config-compatible with Decap so you can switch back.
- **Pros:** Free, no lock-in, best modern git-CMS UX, no dependency on deprecated Netlify Identity, fits the existing GitHub Pages/Cloudflare plan.
- **Cons:** Younger project (smaller community than Decap/WordPress); still needs a technical person for initial setup and each editor needs a GitHub login.

### 3. TinaCMS

Open-source git-backed CMS with optional hosted backend (**Tina Cloud**). Known for live visual/inline editing.

- **Admin interface:** Powerful — inline "edit on the live page" experience plus a structured sidebar. Polished, but the mental model (and setup) is more developer-oriented than Decap/Sveltia.
- **Multi-user / roles:** Real user management and roles come via **Tina Cloud**. Free tier covers ~2 users; more editors/features require a paid plan.
- **Cost:** Self-hosted backend is free but requires a Node server (not compatible with pure GitHub Pages static hosting). Tina Cloud free tier (~2 users), paid tiers roughly **USD $29+/mo (~NZD $575+/yr)** once you exceed it.
- **Setup / maintenance:** Highest technical bar of the three git options — needs a build/backend integration. Best suited to sites already using a JS framework (Next.js, Astro).
- **Suitability:** Fine for events/results/galleries, but overkill for a simple club site.
- **Lock-in / portability:** Content stays in Git (good), but the nicer multi-user features tie you to Tina Cloud.
- **Pros:** Excellent visual editing; content in Git.
- **Cons:** More complex; multi-user costs money; a pure GitHub Pages static site can't host the free self-hosted backend easily. **Not recommended for this club.**

### 4. WordPress (WordPress.com hosted, or self-hosted WordPress.org)

The mainstream CMS. Two flavours: managed **WordPress.com** (they host it) or **self-hosted WordPress.org** (you rent hosting).

- **Admin interface:** The gold standard for non-technical multi-editor sites. Familiar dashboard, block editor, no code. **This is what most volunteer clubs end up using.**
- **Multi-user / roles:** Best-in-class built-in roles — **Administrator, Editor, Author, Contributor, Subscriber**. You can let a news volunteer publish posts while a results volunteer only edits their section, all without them seeing anything technical. This directly nails the "several non-technical people" requirement.
- **Cost:**
  - WordPress.com: Free tier (ads, WP subdomain); **Personal ~NZD $80/yr**; **Premium ~NZD $160/yr**; **Business ~NZD $500/yr** (Business needed for arbitrary plugins).
  - Self-hosted: software free; shared hosting **~NZD $60–200/yr** + domain. Plugins like *The Events Calendar* and gallery plugins are free/freemium.
- **Setup / maintenance:** WordPress.com = low maintenance (they patch it). Self-hosted = **ongoing maintenance burden** (updates, backups, security, spam) — real risk for a volunteer club with turnover. Techsoup NZ / non-profit discounts sometimes available.
- **Suitability:** Excellent. Events calendar (plugin), results tables by year (pages/posts or table plugin), photo galleries (native). Huge theme/plugin ecosystem.
- **Lock-in / portability:** Good — full content export (WXR/XML), and self-hosted means you own everything. WordPress.com Business+ needed for full plugin freedom.
- **Pros:** Best multi-user roles, non-technical friendly, mature, everything available.
- **Cons:** Self-hosted maintenance/security overhead; WordPress.com plugin freedom costs more (Business tier); more moving parts than a static site.

### 5. Wix

Proprietary drag-and-drop hosted builder.

- **Admin interface:** Very easy visual drag-and-drop; great for a single designer. Multi-contributor **Roles & Permissions** exist (Admin, Website Manager, Blog/Store roles, custom roles) but the drag-drop canvas can be *too* free-form — easy for a well-meaning volunteer to break the layout.
- **Multi-user / roles:** Supported with named roles, adequate for a club.
- **Cost:** No usable free tier for a real site (free = Wix ads + subdomain). Paid **~NZD $265–500+/yr**; renewal prices often rise after year one.
- **Setup / maintenance:** Very easy setup, fully managed (no maintenance).
- **Suitability:** Events, galleries and tables all doable via built-in apps; polished results.
- **Lock-in / portability:** **Poor** — no meaningful content export, you cannot move a Wix site elsewhere. Strong lock-in.
- **Pros:** Easiest visual builder; zero maintenance.
- **Cons:** Ongoing cost, price creep, heavy lock-in, free-form editing risks layout breakage.

### 6. Squarespace

Proprietary hosted builder known for polished, template-driven design.

- **Admin interface:** Clean, structured editor — more guardrails than Wix, so non-technical editors are less likely to break the design. Easy to learn.
- **Multi-user / roles:** **Contributor permissions** with roles (Owner, Administrator, Website Editor, etc.). Solid for a club.
- **Cost:** No free tier. Plans **~NZD $300–500/yr** (Basic ~NZD $370/yr billed annually); now bills NZ customers in NZD with GST on invoices.
- **Setup / maintenance:** Easy setup, fully managed, minimal maintenance. Best-looking results with least effort.
- **Suitability:** Built-in **Events** collection, image galleries are excellent, results tables via markdown/table blocks. Well-suited to an events-and-photos club site.
- **Lock-in / portability:** Limited — some export (blog/pages to WordPress XML) but design and structured content don't transfer. Moderate-to-strong lock-in.
- **Pros:** Polished design out of the box, good editing guardrails, decent roles, low maintenance.
- **Cons:** Ongoing cost, some lock-in, less flexible than WordPress.

### 7. Google Sites

Free site builder tied to a Google account / Google Workspace.

- **Admin interface:** The **simplest possible** multi-editor experience — sharing works exactly like a Google Doc: add a Google account as an editor and they can edit immediately. Truly zero learning curve for volunteers who already use Gmail.
- **Multi-user / roles:** Editor/Viewer sharing (and Publisher control). Simple but effective; no granular content roles.
- **Cost:** **Free** with any Google account. Custom domain works but you need to own the domain (~NZD $20–40/yr); Workspace (~NZD $12/user/mo) only if the club wants managed accounts — not required.
- **Setup / maintenance:** Trivial setup, zero maintenance, Google handles everything.
- **Suitability:** **Weakest on features.** Fine for news and embedding a Google Calendar for events; results tables are basic; galleries are simple. You can embed Google Sheets for results-by-year, which is actually a neat low-effort pattern. Design is generic and limited.
- **Lock-in / portability:** Poor export, but content is trivial and easy to recreate; you're tied to Google.
- **Pros:** Free, dead simple, effortless multi-editor sharing, zero maintenance.
- **Cons:** Limited design and features; looks generic; weak for rich results tables and galleries.

### Also noted (briefly)

- **Netlify / Cloudflare Pages / GitHub Pages** — these are **hosts**, not CMSs. All have free tiers ample for a club static site. Cloudflare Pages (free, generous) pairs especially well with **Sveltia**. Netlify's 2025 move to a credit model and Identity deprecation makes **GitHub Pages or Cloudflare Pages the better free host** for the git-CMS route now.
- **Weebly** — simple Square-owned builder, similar to Wix but now stagnant/declining; no advantage over the options above. Not recommended.

---

## Comparison table

| Platform | Non-tech admin | Multi-user & roles | Cost (NZD/yr) | Setup | Maintenance | Events / Results / Galleries | Lock-in |
|---|---|---|---|---|---|---|---|
| **Decap CMS** + GH Pages/Netlify | Good | Yes; coarse (via Git host); Netlify Identity deprecated | ~$0 + domain | Technical, one-off (fiddly) | Low | Good / Good / Good | **None** |
| **Sveltia CMS** + GH/Cloudflare Pages | Very good | Yes; via GitHub OAuth, no identity server | ~$0 + domain | Technical, one-off | Low | Good / Good / **Very good** | **None** |
| **TinaCMS** | Good (visual) | Paid (Tina Cloud) beyond ~2 users | $0 free tier → ~$575+ | High (needs backend) | Medium | Good / Good / Good | Low (content) / Cloud tie-in |
| **WordPress.com** | Excellent | **Excellent** (5 built-in roles) | ~$80–500 | Easy | Low (managed) | Good / Good / Very good | Low–Moderate |
| **WordPress self-hosted** | Excellent | **Excellent** (5 built-in roles) | ~$80–240 | Moderate | **High** (you patch it) | Good / Good / Very good | **Low** (own export) |
| **Wix** | Very easy | Yes (roles) | ~$265–500 | Very easy | None (managed) | Good / OK / Good | **High** |
| **Squarespace** | Very easy (guardrails) | Yes (contributor roles) | ~$300–500 | Very easy | None (managed) | Very good / OK / **Very good** | Moderate |
| **Google Sites** | **Simplest** | Editor/Viewer sharing (no granular roles) | **Free** + domain | Trivial | None (managed) | OK (embed Calendar) / Basic / Basic | Moderate |

---

## Ranking & recommendation — top 3 for "simple admin, several non-technical editors"

### 🥇 1. Sveltia CMS + GitHub Pages (or Cloudflare Pages)
**Best fit for the path the club is already on.** It keeps the free, no-lock-in, own-your-content static site the club is building, and adds a genuinely friendly `/admin` where several volunteers each log in with a free GitHub account and edit events, results and news through simple forms — no code. It avoids the deprecated Netlify Identity trap that hurts Decap, and its media library is the best of the git CMSs (good for a photo-heavy orienteering club).
- **Suits:** a club that has (or can borrow) **one technical volunteer** to do the one-off setup, and wants zero ongoing cost and full ownership of its content.
- **Caveat:** each editor needs a GitHub login, and someone technical must do the initial wiring. If that person disappears, changes are still possible but harder.

### 🥈 2. WordPress (start with WordPress.com Premium, ~NZD $160/yr)
**The safest choice if there is no reliable technical volunteer.** Nothing beats WordPress for letting several non-technical people edit safely: mature dashboard, and true **roles** (Editor, Author, Contributor) so you can hand out exactly the right level of access. Events (The Events Calendar plugin), annual results tables and galleries are all well supported. Choosing **WordPress.com** avoids the security/patching burden of self-hosting; upgrade to Business only if you need specific plugins.
- **Suits:** a club that will happily pay a modest annual fee for a fully managed, familiar, resilient multi-editor system with the least dependence on any one person.
- **Caveat:** ongoing cost; self-hosted WordPress adds real maintenance risk — prefer managed WordPress.com.

### 🥉 3. Squarespace (~NZD $300–500/yr)
**Best of the polished all-in-one builders.** Easier and safer for non-technical editors than Wix (more guardrails, so volunteers won't wreck the layout), with contributor roles, a built-in Events collection and excellent galleries — all fully managed with near-zero maintenance and a professional look straight away.
- **Suits:** a club that wants the **nicest-looking site for the least effort**, has no technical volunteer, and accepts an annual fee plus some lock-in.
- **Caveat:** ongoing cost and limited data portability.

**Honourable mention — Google Sites (free):** the simplest multi-editor experience of all (share like a Google Doc) and genuinely free. Drop to this if budget is zero *and* the club can live with a basic, generic-looking site (embed a Google Calendar for events and Google Sheets for results). Feature-limited but unbeatable on simplicity and cost.

### Bottom line
- **Keep the GitHub Pages static site and have a technical helper?** → **Sveltia CMS.**
- **No technical helper, want it to "just work" for years?** → **WordPress.com.**
- **Want the prettiest site with least effort and don't mind paying?** → **Squarespace.**
- **Zero budget, keep it dead simple?** → **Google Sites.**

---

### Sources
- [Netlify pricing & plans](https://www.netlify.com/pricing/) · [Netlify Identity plans](https://docs.netlify.com/manage/security/secure-access-to-sites/identity/plans-and-pricing/) · [Git Gateway (Decap docs)](https://decapcms.org/docs/git-gateway-backend/) · [Decap + Netlify setup / Identity deprecation note](https://dylanbochman.com/blog/2026-01-15-decap-cms-netlify-setup-guide)
- [WordPress.com pricing 2026](https://wppoland.com/en/wordpress-com-pricing-plans-2026/) · [WordPress.com vs .org](https://wordpress.com/support/com-vs-org/)
- [Squarespace pricing (NZ)](https://www.madebymarkham.co.nz/blog/how-much-does-a-squarespace-website-cost-in-new-zealand-in-2026) · [Squarespace official pricing](https://www.squarespace.com/pricing)
- [Wix premium plan pricing](https://support.wix.com/en/article/wix-premium-plan-pricing) · [Wix pricing breakdown 2026](https://www.websitebuilderexpert.com/website-builders/wix-pricing/) · [Wix via Techsoup NZ](https://www.techsoup.net.nz/products/brand/Wix)
