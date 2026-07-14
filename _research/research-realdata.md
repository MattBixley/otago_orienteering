# Otago / Dunedin Orienteering Club — Real Data Extract

**Extracted:** 2026-07-15
**Primary source site:** https://www.dunedinorienteering.org/
**Note:** The club has renamed from "Dunedin Orienteering Club" to "Otago Orienteering Club". Per the committee page, the website will move to `https://otagoorienteering.org.nz` soon. At extraction time `otagoorienteering.org` did **not** resolve (DNS ENOTFOUND) and `.org.nz` was not tested/live.

**Site structure discovered (important for scraping):**
- Home: `/` (and `/home`)
- Events (descriptive only, no dated list): `/events`
- Event fees: `/events/fees`
- Calendar page: `/calendar` — **404, does not exist.** Calendar is offered only as a Google Calendar subscription link.
- Committee: `/committee` (NOT `/committee-contacts`)
- Membership: `/membership`
- Results: current year is `/2026-results`. **All prior years are nested under it**, e.g. `/2026-results/2025-results`, `/2026-results/2024-results`, `/2026-results/2023-results`, `/2026-results/2022-results`. Flat URLs like `/2025-results` return 404. Full year list linked from the 2026 page: 2010, 2011, 2012 (`/2026-results/results-2012`), 2013, 2014, 2015, 2016, 2017, 2018, 2019 (`/2026-results/results-2019`), 2020, 2021, 2022, 2023, 2024, 2025.

---

## 1. UPCOMING / RECENT EVENTS

Source: https://www.dunedinorienteering.org/ (home page). The home page is the only place with dated upcoming events; `/events` is descriptive only and `/calendar` does not exist.

| Date | Event | Location | Type | Start time | Cost | Registration / link |
|------|-------|----------|------|-----------|------|---------------------|
| 2026-07-25 | School Series Prizegiving | Signal Hill MTB carpark | Prizegiving | 4:00pm | — | (just prior to Twilight Signal map handout) |
| 2026-07-25 | Rogaine #2 – Twilight Signal | Signal Hill | 90-minute night rogaine | 5:30–7:00pm | — | Google Form; registrations close midnight Tue 21 July |
| 2026-08-16 | Central Otago Rogaine | 15 min from Alexandra, off Fraser Dam road | Rogaine, teams of 2–5 ("fun challenge for all levels") | — | — | http://www.journeys.org.nz/rogaine (closes midnight Sun 9 August) |

**Recently posted (home page note):** 2026 Dunedin Schools' series results and Otago Schools' Champs results posted to the results page.

**AMBIGUOUS / NOT FOUND:** Specific start times and costs for most upcoming events are not on the home page. The exact Google Form URL for Twilight Signal registration was not exposed in fetched text.

### Event types the club runs (from `/events`, descriptive, not dated)
- **Foot Orienteering – Club Classic "OY" Events:** up to ~5/year across Otago; six course lengths White→Long Red; winning times ~60 min for longer courses.
- **Summer / Schools Series:** Term 1; 4–5 events; three-course format for beginners.
- **Otago Schools' Champs:** first OY event after Summer Series.
- **Sprint Events:** 4–5/year, generally local to Dunedin; winning times ~15–20 min.
- **Mountain Bike Orienteering (MTBO):** Alexandra & Naseby.
- **Rogaines:** club series of 4–5 events; typically 3 hours or shorter.
- **Ski Orienteering:** Snow Farm, Wanaka.

---

## 2. RESULTS BY YEAR

Result-link services seen: **Google Drive** (result PDFs/sheets), **WinSplits** (`obasen.orientering.se`), **Livelox** (`livelox.com`), **RouteGadget** (`rg.orienteering.org.nz`), and occasionally **Google Docs folderview**.

### 2026 — `/2026-results`
Source: https://www.dunedinorienteering.org/2026-results

| Date | Event | Type | Result links (service) |
|------|-------|------|-------------------------|
| — | SS1 – Sprint1 – Tonga Park | School Series / Sprint | GDrive `1hYkvUVVxQE1TA3kB-W7IuQqug0OlzuYt`; WinSplits `id=112043`; Livelox `187492` |
| — | SS2 – Forest – Forrester Park | School Series | GDrive `1FkgvrtsPJuG13ZMB5Cci4WbT1tsWxxua`; WinSplits `id=113638` |
| — | SS3 – Sprint2 – Southern Cemetery | School Series / Sprint | GDrive `1EPNcAwTBhpK2OXLaJnSKx_Y6w1dRfAkn`; WinSplits `id=113254` |
| — | Rogaine – Waiora | Rogaine | GDrive `1WO02s8SGAJxHoV7T6IoaIkIb5LeJrZoO` |
| — | Chingford Have a Go Event | Have-a-go | GDrive `1ikPIUjCWxuyugcMtp29S8UpBLurylJYz` |
| — | Queens Drive Active Travel Trial Event | Trial/community | GDrive `11AhNKL7GzSXdi2hOTZCr0pDJdcirM7Kw`; Livelox `185040`; WinSplits `id=111411` |
| — | Waikouaiti Beach Sprint | Sprint | GDrive `1WAIeNDJXszFGffdSX-S1RRM1vsiz0_0M` |
| 2026-02-22 | Maryhill Metrogaine | Rogaine (metrogaine) | GDrive `1XtwkjBMSfIPbESm6MEVWak5K6iWQS2fl`; Livelox `180252` |
| — | Port Chalmers Rogain | Rogaine | GDrive `1gOhEuv-axQeH1f-FXUV8h8HePTzYN3FT`; Livelox `181273` |
| — | Lower Manorburn March Rogaine | Rogaine (Summer Series Rogaine 3) | GDrive overall `1xzm1BtZ6O7Ds2-U8i2xFnUcZEiGgNJa2`; GDrive by-grade `13_QCwZQIrOk9vBK2wieZZKfRWPWW_GAO`; Livelox `182806` |
| — | Waikouaiti Beach Rogaine | Rogaine | GDrive `196sRil8sv_C5YPapYiFtkClbSrn1WY_B` |
| 2026-06-20 | NightO Alexandra Airport | Night event (Central Otago) | GDrive `1lBIN2tFm1rYy5M73LRa_1G-bW_9fKFrn`; WinSplits `databaseId=113628`; Livelox `194149` |
| 2026-02-06 | Little Mt Ross Sprint (Waitangi Wknd, Fri) | Sprint | GDrive `18wYoN89W-pyuizYu5Mi6mpi47CduUC8q`; WinSplits `databaseId=110324` |
| 2026-02-06 | Mt Ross Night Sprint (Waitangi Wknd, Fri night) | Night sprint | GDrive `1zpamwZFtuSm3gs8HITR4YiYbHtWZgoZO`; WinSplits `id=110332` |
| 2026-02-07 | Gladbrook OY (Waitangi Wknd, Sat Long) | Classic/Long OY | GDrive `1mLf_M-GvzX229JKT6PW0Aflr5Me8vCKg`; WinSplits `id=110333`; Livelox `179322` (Dunedin 50th Middlemarch Long) |
| 2026-02-08 | Novelty Sprint Sutton (Waitangi Wknd, Sun Middle) | Middle/Novelty sprint | GDrive `1cGTAjP_UQ4KNLpWZe4prqtPodLhco5l2`; WinSplits `id=110355` |
| — | OYClassic 2 – Chatto Creek | Classic OY | GDrive `1l30U-UtI6_hwTQSttgOYFrmIWT_UCP5g`; WinSplits `databaseId=111622`; Livelox `186067` |
| — | OYClassic 3 – Otago Schools' Champs (Long) | Classic OY / Schools Champs | GDrive OY3 `1nHPcs9ph20-FC7IkQXabDel6hOokCt4C`; GDrive School Champs `1O-_1BBdpPwUasCrIKMbkxRUad5sNTyyF`; WinSplits `id=113775`; Livelox (org events index, not a specific event) |

Full WinSplits URL form: `https://obasen.orientering.se/winsplits/online/en/show_event.asp?id=<id>` or `.../default.asp?page=classes&databaseId=<id>`. Full Livelox form: `https://www.livelox.com/Events/Show/<id>/...`. Full GDrive form: `https://drive.google.com/file/d/<id>/view`.

### 2025 — `/2026-results/2025-results`
Source: https://www.dunedinorienteering.org/2026-results/2025-results (WebFetch summary; result files are Google Drive unless a WinSplits/Livelox id is shown)

| Event | Type | Result links |
|-------|------|--------------|
| SS Prelim – MazeO | Preliminary Summer Series | GDrive; WinSplits `databaseId=102852` |
| SS1 – Chingford Park | Summer Series | GDrive; WinSplits `databaseId=102961`; + Schools Points (GDrive) |
| SS2 – Taieri College | Summer Series | GDrive; WinSplits `databaseId=103183`; + Schools Points (GDrive) |
| SS3 – Bethunes/Forester Park | Summer Series | GDrive; WinSplits `databaseId=103325`; + Schools Points (GDrive) |
| Campus Scamper Night Event | Night | GDrive; WinSplits `databaseId=105188` |
| Vampire O | Specialty | GDrive |
| Campus Scamper XMAS Sprint & BBQ | Sprint | GDrive; WinSplits `id=109715` |
| Twilight Signal #1 | Rogaine | GDrive |
| Glow Worms VIII | Rogaine | GDrive |
| West Dunedin Metrogaine | Rogaine | GDrive |
| MTBO Nationals Sprint (1–2 Feb) | MTBO | GDrive; WinSplits `databaseId=102602` |
| MTBO Nationals Middle | MTBO | GDrive; WinSplits `databaseId=102603` |
| MTBO Nationals Long | MTBO | GDrive; WinSplits `databaseId=102630` |
| OY1 Classic – Pyramids | Classic OY | GDrive by-course; GDrive by-class; WinSplits `databaseId=103605` |
| OY1 Sprint – Green Island | Sprint OY | GDrive by-course; GDrive by-class; WinSplits `databaseId=103606` |
| OY1/Otago Schools' Champs Combined | Championship | GDrive Schools Championship; GDrive Schools Standard |
| OY2 Classic – Matangi | Classic OY | GDrive; WinSplits `databaseId=106480` |
| OY3 Classic – Sutton | Classic OY | GDrive; WinSplits `databaseId=107147` |
| OY4 Classic – Alexandra Airport | Classic OY | GDrive; WinSplits `id=109104`; Livelox `173365` |
| 2025 OY Series Points Totals | Series standings | GDrive |
| SI Schools/Otago Champs Sprint (ANZAC) | Sprint champs | GDrive; WinSplits `databaseId=104199` |
| SI Schools/Otago Champs Long (ANZAC) | Long champs | GDrive; WinSplits `databaseId=104211`; Livelox `154595` |
| SI Champs Long – Southland | Long | GDrive; WinSplits `databaseId=102714` |
| SI Champs Middle – Southland | Middle | GDrive; WinSplits `databaseId=102740` |

### 2024 — `/2026-results/2024-results`
Source: https://www.dunedinorienteering.org/2026-results/2024-results

Event structure (from WebFetch):

| Event | Type | Services present |
|-------|------|-----------------|
| SS1 – Kaikorai Valley College | Summer Series | GDrive + WinSplits |
| SS2 – Ross Creek | Summer Series | GDrive + WinSplits |
| SS3 – Ocean Grove | Summer Series | GDrive + WinSplits |
| SS4 – Waiora | Summer Series | GDrive + WinSplits |
| Rogaine 1 – Ross Creek | Rogaine | GDrive |
| Rogaine 2 – Glow Worms VII | Rogaine | GDrive |
| Rogaine 3 – Twilight Signal | Rogaine | GDrive |
| OY2 Poolburn | Classic OY (Central Otago) | GDrive (by course/class) + WinSplits |
| OY3 Matangi | Classic OY (Central Otago) | GDrive (by course/class) + WinSplits |
| OY1 Mt Ross Sprint/Prologue | Sprint/prologue | GDrive |
| OY1 Mt Ross (Schools' Champs / Club OY) | Classic OY / Schools | GDrive + WinSplits |
| Sprint OY1 – LPHS | Sprint OY | GDrive + WinSplits |
| Sprint OY2 – Woodhaugh | Sprint OY | GDrive + WinSplits |
| Sprint OY3 – Southern Cemetery | Sprint OY | GDrive + WinSplits |
| SI Champs Sprint (ANZAC) | Sprint champs | GDrive + WinSplits + RouteGadget |
| SI Champs Long (ANZAC) | Long champs | GDrive + WinSplits + RouteGadget + Livelox |
| SI Champs Middle (ANZAC) | Middle champs | GDrive + WinSplits + RouteGadget |

**AMBIGUOUS:** The 2024 WebFetch summary did not map each URL to its event. The complete set of external result URLs harvested from the raw page HTML is below (WinSplits ids: 95224, 95368, 95491, 95611, 95915, 95950, 96665, 96716, 96750, 97431, 100110, 100709, 101509; Livelox event 127687 "2024 NZ South Island Champs Long"; RouteGadget rg2 #891/#894/#895; plus ~27 Google Drive file links and one Google Docs folderview `1u-bVoTZYqVPuAu9Pdkih1P3kFy8aLSKf`). If precise per-event mapping is needed, re-scrape the page DOM in order.

### 2023 — `/2026-results/2023-results`
Source: https://www.dunedinorienteering.org/2026-results/2023-results

| Date | Event | Type | Result links |
|------|-------|------|--------------|
| — | SS0 – Woodhaugh Gardens (Training) | Summer Series (training) | GDrive; WinSplits `databaseId=87515`; RouteGadget `#869` |
| — | SS1 – Logan Park | Summer Series | GDrive; WinSplits `databaseId=87635` |
| — | SS2 – Jubilee Park | Summer Series | GDrive; WinSplits `databaseId=87747`; RouteGadget `#875` |
| — | SS3 – Forrester Park | Summer Series | GDrive; WinSplits `databaseId=87879`; RouteGadget `#877` |
| — | SS4 – Bathgate King's/Queen's | Summer Series | GDrive; WinSplits `databaseId=88170`; RouteGadget `#878` |
| — | Rogaine – Ross Creek | Rogaine | GDrive |
| — | Rogaine – Twilight Signal | Rogaine | GDrive |
| — | Rogaine – Glow Worms VI | Rogaine | GDrive |
| 2023-04-23 | Alexandra MTB Enduro | MTBO (Central Otago) | GDrive by-class; GDrive by-course |
| 2023-04-25 | Naseby MTBO Rogaine | MTBO rogaine | GDrive by-discipline; GDrive by-class |
| — | Boot Hill Night Event | Night | GDrive by-course; GDrive by-class; WinSplits `databaseId=90623` |
| — | OY1 – Andy Bay Cemetery | Classic OY | GDrive; WinSplits `databaseId=88311`; RouteGadget `#880` |
| — | OY1 – Warrington Okahau | Classic OY | GDrive; WinSplits `databaseId=88312`; RouteGadget `reitti.cgi?id=879` |
| — | OY2 – Mt Ross | Classic OY | GDrive; WinSplits `databaseId=89190`; RouteGadget `#883` |
| — | OY3 – Chatto Creek | Classic OY | GDrive by-class; GDrive by-course; WinSplits `databaseId=91574` |
| — | SOY1 – Otago Boys' | Sprint OY | GDrive; WinSplits `databaseId=92226`; RouteGadget `#885` |
| — | SOY2 – Balmac Columba | Sprint OY | GDrive; WinSplits `databaseId=92662`; RouteGadget `#886` |
| — | SOY3 – KVC | Sprint OY | GDrive; WinSplits `databaseId=93611`; RouteGadget `#887` |
| — | SOY4 – Cromwell | Sprint OY | GDrive by-class; GDrive by-course |
| — | Christmas – Chingford | Christmas event | GDrive; WinSplits `databaseId=94310` |

### 2022 — `/2026-results/2022-results`
Source: https://www.dunedinorienteering.org/2026-results/2022-results

| Date | Event | Type | Result links |
|------|-------|------|--------------|
| 2022-01-15 | Otago Epilogue Event 1 – Humpy Bumpy | Classic | GDrive; WinSplits `databaseId=79382`; RouteGadget (listed, no URL) |
| 2022-01-16 | Otago Epilogue Event 2 / Club OY4 – Kuriheka | Classic | GDrive; WinSplits `databaseId=79402`; RouteGadget (listed, no URL) |
| — | SISSOC Sprint – Balclutha Schools | Sprint | GDrive; WinSplits by-class `83516`, by-course `83517`; RouteGadget `reitti.cgi?id=863` |
| — | SISSOC Long – Dolamore Park, Gore | Long | GDrive; WinSplits by-class `83537`, by-course `83539`; RouteGadget `reitti.cgi?id=864` |
| — | OY5 – Otago Schools' Champ (Cedar Creek & Maori Hill) | Schools championship | GDrive overall; GDrive Cedar Creek; GDrive Maori Hill; WinSplits Cedar Creek `83032`, Maori Hill `83031`; RouteGadget Cedar Creek `id=855`, Maori Hill `id=857` |
| — | OY6 – Dolamore Park | Classic | Results listed, **no links provided** |
| — | OY7 – Sutton | Classic | GDrive; WinSplits `databaseId=84101`; RouteGadget `#865` |
| — | OY8 – Alexandra Airport | Classic | GDrive; WinSplits `databaseId=86595` |
| — | Sprint OY3 – Balmacewen & Columba | Sprint OY | GDrive |
| — | Sprint OY4 – Taieri College | Sprint OY | GDrive; WinSplits `databaseId=85876` |
| 2022-02-13 | Rogaine #1 – Glow Worms V | Rogaine | GDrive |
| 2022-04-03 | Rogaine #2 – Flagstaff Follies | Rogaine | GDrive |
| — | SS1 – Chingford Park | Summer Series | GDrive; WinSplits `databaseId=82103`; RouteGadget `reitti.cgi?id=848` |
| — | SS2 – Forrester Park | Summer Series | GDrive; WinSplits `databaseId=82338`; RouteGadget `reitti.cgi?id=849` |
| — | SS3 – Tomahawk | Summer Series | GDrive; WinSplits `databaseId=82788`; RouteGadget `reitti.cgi?id=854` |
| 2022-05-15 | Matangi MTBO/Foot Rogaine | MTBO/rogaine | GDrive by-course; GDrive by-class; RouteGadget `#845` |
| 2022-06-25 | Matariki Night O | Night | GDrive by-class; GDrive by-course |

**Years 2010–2021 and 2012/2019 (alternate slug):** exist as linked pages under `/2026-results/...` but were **not fetched** in this pass (out of the 2022–2026 scope requested). Slugs: `/2026-results/2021-results` … `/2026-results/2010-results`, plus `/2026-results/results-2012` and `/2026-results/results-2019`.

---

## 3. COMMITTEE / CONTACTS
Source: https://www.dunedinorienteering.org/committee

| Role | Person | Email |
|------|--------|-------|
| President | Ann Bixley | president@dunedinorienteering.org |
| Secretary | Jeni Pelvin (Luke Geddes assists when required) | secretary@dunedinorienteering.org |
| Treasurer | Tim Webb | treasurer@dunedinorienteering.org |

**Committee members:** Jim Cotter, Myles Thayer, Luke Geddes, Jen Hodgson, Daniel Johnston, Fraser Stephens, Darrell Thomson, Genevieve Webb, Sannah Aitcheson, Antonia Wood, Joe Sherriff (Penny Smale backup).

**Central Otago Branch (Alexandra):** Joe Sherriff, Jo Wilson, Penny Smale, Pete Dymock, Libby Whyte, Rachel Baxter.

**Roles / responsibilities:**
- Webmaster: Fraser Stephens
- Membership: Megan Hall
- Computer & Software Admin: Genevieve Webb
- School Series & Liaison: Ann Bixley
- Landowner Liaison: Darrell Thomson
- Coaching / ONZ Liaison: Antonia Wood
- Equipment Management: Fraser Stephens (SI boxes, entry tablets, power supply, start tablet & speaker, caravan/garage items)
- Trophies & Archives: Jeni Pelvin
- Certificates: Ann Bixley
- Statisticians: Otto & George Hyink
- MapRun Administrators: Moss Pelvin & Joe Sherriff
- Publicity / Social Media: Antonia Wood
- MTB Liaison: Jeni Pelvin
- Map Archives: Jim Cotter (jim.cotter at otago.ac.nz)

**Generic emails:** president@, secretary@, treasurer@, webmaster@, committee@, membership@ — all `@dunedinorienteering.org`.
**Postal:** P.O. Box 969, Dunedin, Otago 9054, New Zealand.
**Phone numbers:** none listed.

---

## 4. MEMBERSHIP FEES
Source: https://www.dunedinorienteering.org/membership

| Category | Fee |
|----------|-----|
| Senior | $40 |
| Junior (age ≤20 as of 31 Dec; under-7s born 2018+ free) | $20 |
| Tertiary Student (full-time, under 21) | $30 |
| Community Services Card Holder | $30 |
| Family maximum (up to two seniors same address + any juniors) | $100 |

**Discounts (50% off, one only):** new members never previously in a club; joining after 30 June; Dunedin residents who are ancillary members of another club.

**Join / renew (RevolutioniseSPORT):**
- Register: https://www.revolutionise.com.au/dunedinoc/registration/
- Login: https://www.revolutionise.com.au/dunedinoc/login/

**Payment:** Direct credit to "Dunedin Orienteering Club, 12-3150-0152097-00", Particulars "Membership", Reference = surname.

**Member benefits:** half-price event fees at Club & OY events; certificate eligibility (top 3); junior training camp subsidies; social events & coaching clinics; NZ Orienteering Federation affiliation.

**Note:** the Junior age cutoff text on the live page reads "age 20 or under as of December 31, 2024" — likely a not-yet-updated year on the site (verbatim as found).

## 4b. EVENT FEES
Source: https://www.dunedinorienteering.org/events/fees

Standard per-event entry fees (member vs non-member, adult/junior/family) were **NOT found** on this page. Only equipment hire is listed:
- SportIdent (SI) stick hire: $3 per course ($50 replacement charge).
- SIAC contactless chip hire: $5 per event ($150 replacement charge).
- Thumb compass hire: $3 per course ($25 replacement charge).
- Page states "Championship and Special Events fees are set separately" (no figures).
- Membership page states members get "half price event fees" (base fee amount not stated anywhere found).

---

## 5. SOCIAL / EXTERNAL LINKS
Source: home page and committee page.

- Central Otago Facebook: https://www.facebook.com/COOrienteering
- Queenstown club (ROC): http://www.roc.org.nz
- Club email group (Google Group): https://groups.google.com/g/otagoorienteering
- Google Calendar subscription for club events (subscribe URL offered on home/events pages; exact ICS URL not exposed in fetched text).
- Rogaining Association: rogaine.org.nz
- Central Otago Rogaine registration/host: http://www.journeys.org.nz/rogaine

**AMBIGUOUS / NOT FOUND:** A main Dunedin/Otago club Facebook page (only the Central Otago branch FB was found). No Instagram/Twitter/X links found.

---

## NOT FOUND / AMBIGUOUS — summary
- `/calendar` page: does not exist (404).
- Standard event entry-fee figures: not published on the fees page.
- Exact dates for most 2026-results events (dates only shown for some; results pages generally omit dates).
- Per-event URL mapping for 2024 (services identified, full URL list captured but not individually mapped).
- Results years 2010–2021 not fetched (outside requested 2022–2026 window; page slugs recorded above).
- `otagoorienteering.org` does not resolve yet (planned `.org.nz` migration).
