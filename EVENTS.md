# How to add an event

Every event on the site is one small text file in the `_events/` folder. Adding
an event to the calendar means creating one of these files. You can do it two
ways:

1. **Through the CMS** — a web form, no code, recommended for most people.
2. **By hand** — editing a text file directly, if you prefer or are already in
   the repo.

Both do exactly the same thing: they create a file in `_events/`. When it's
saved, the site rebuilds and the event appears within a minute or two.

---

## Option 1 — the easy way (CMS)

1. Go to **`/admin/`** on the site (`https://mattbixley.github.io/otago_orienteering/admin/`)
   and log in.
2. Choose **Events → New Event**.
3. Fill in the form (each field is explained below) and **Save / Publish**.

That's it — the CMS writes the file, names it correctly, and commits it for you.
Skip to [What the fields mean](#what-the-fields-mean).

---

## Option 2 — by hand

### 1. Name the file

Create a new file in `_events/` named:

```
YYYY-MM-DD-short-slug.md
```

- `YYYY-MM-DD` is the event date (this is how events sort).
- `short-slug` is a few lowercase words with hyphens, e.g. `oy-classic-signal-hill`.

Example: `_events/2026-08-16-central-otago-rogaine.md`

### 2. Fill in the top block, then the description

A file has two parts: the **front matter** (the settings between the two `---`
lines) and the **body** (the description, written in Markdown, below the second
`---`).

Copy this template and edit it:

```markdown
---
title: OY Classic #3 – Signal Hill
date: 2026-08-30
start_time: 10:00am start, register from 9:30am
event_type: OY Classic
location: Signal Hill, Dunedin
grade: White through to Long Red
cost: $10 members · $20 non-members · juniors half
registration: "https://forms.gle/your-google-form"
map_url: ""
image: ""
results: ""
---

Write the event description here in plain language. You can use normal
paragraphs, **bold**, and links like [this](https://example.com).

## Getting there

Add any extra sections you like — parking, what to bring, course notes.
```

---

## What the fields mean

| Field | Required | What it is |
|-------|----------|------------|
| `title` | ✅ | The event name shown everywhere. `#` and `–` are fine. |
| `date` | ✅ | Event date, `YYYY-MM-DD`. Controls sorting and when it moves to "past". |
| `start_time` | optional | Free text, e.g. `10:00am start, register from 9:30am`. |
| `event_type` | ✅ | One of the fixed types below. Sets the badge **and** the default photo. |
| `location` | ✅ | Where it is, e.g. `Signal Hill, Dunedin`. |
| `grade` | optional | Courses/grades offered, e.g. `White through to Long Red`. |
| `cost` | optional | Entry fees. A sensible default is pre-filled in the CMS. |
| `registration` | optional | A link (usually a Google Form) for entries. |
| `map_url` | optional | A link to the event map, if there is one. |
| `image` | optional | A specific photo for this event. **Leave blank** to use the default photo for the event type. |
| `results` | optional | Fill in **after** the event with the results page path, e.g. `/results/2026/oy-classic-3-signal-hill/`. |

> **Quote anything awkward.** If a value contains a colon `:`, a `#` at the
> start, or square brackets, wrap it in double quotes: `title: "Sprint #4: The Oval"`.

### Event types

Pick one exactly as written:

`OY Classic` · `Sprint` · `Summer/Schools Series` · `Rogaine` · `MTBO` ·
`Night` · `Championship` · `Ski` · `Other`

### Photos

Every event page automatically shows a photo:

- If you set `image`, that photo is used.
- If you leave `image` blank, the site picks a default photo that matches the
  `event_type` (e.g. MTBO events get the mountain-bike photo). So you never
  *have* to add one.

To use your own photo in the CMS, just click the **Photo** field and upload it.
By hand, put the file in `assets/img/` and set `image: /assets/img/your-photo.jpg`.

---

## After you save

- The event shows up automatically:
  - the **single next event** on the home page,
  - the **Upcoming** list on the [Events page](/events/).
- **Future dates are fine** — the site publishes upcoming events on purpose.
- Once the event date passes, it moves itself to **Recent past events** — you
  don't need to do anything.
- When results are ready, add a results file (see the CMS **Results** section)
  and set this event's `results:` field to the results page path so the two
  link together.

---

## A complete real example

`_events/2026-07-25-rogaine-twilight-signal.md`:

```markdown
---
title: Rogaine #2 – Twilight Signal
date: 2026-07-25
start_time: 5:30pm–7:00pm
event_type: Rogaine
location: Signal Hill, Dunedin
grade: 90-minute score rogaine — all levels
cost: $10 members · $20 non-members · juniors half
registration: "[Google Form — registrations close midnight Tuesday 21 July]"
---

Our second rogaine of the series: a 90-minute twilight/night score event on
Signal Hill. Collect as many controls as you can before the clock runs out.

## Register

Entries are via a Google Form and **close midnight Tuesday 21 July**. Bring a
headtorch — the light will be going.
```

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Event doesn't appear | Check the file is in `_events/` and the filename starts with the date `YYYY-MM-DD-`. |
| Build failed after saving | Usually a front-matter typo — a missing `---`, or a value with a `:` that isn't in quotes. |
| Wrong or no badge | `event_type` must match one of the types above exactly (capitalisation matters). |
| It shows as a past event | Check the `date` — the site compares it to today's date (Pacific/Auckland). |
