# Otago Orienteering — draft website

A draft rebuild of the Otago Orienteering Club website (formerly Dunedin
Orienteering Club), built as a static [Jekyll](https://jekyllrb.com/) site for
free hosting on **GitHub Pages**, with a **[Sveltia CMS](https://github.com/sveltia/sveltia-cms)**
admin so several non-technical committee members can edit content through web
forms.

This is a **draft for review**, not the live site. Content in `[square
brackets]` is a placeholder for the club to complete.

## What's here

```
_config.yml            Site config + top navigation (edit nav here)
index.html             Home page (hero, next events, start-here cards)
about.md               About the club
events/                Events landing page (upcoming + recent past)
_events/               One file per event  → /events/<slug>/
results/               Results landing page (grouped by year, then type)
_results/<year>/       One file per result → /results/<year>/<slug>/
resources.md           Links out to Orienteering NZ training material
policy/                Club policies landing page
contact.md             Contact & join
admin/                 Sveltia CMS — the editor UI (config.yml defines forms)
assets/css/style.css   All styling (light + dark, mobile-first)
.github/workflows/     GitHub Pages build + deploy
_reviews/              The two review documents (see below)
_research/             Raw research notes behind the reviews
```

## The two review documents

- **`_reviews/website-review-and-suggestions.md`** — review of the current
  Google Sites site vs the best NZ club sites (PAPO, Auckland), with prioritised
  recommendations.
- **`_reviews/website-options-review.md`** — review of website publishing
  platforms with a simple multi-editor admin, and the top-3 recommendation.

## Run it locally

```bash
bundle install
bundle exec jekyll serve
# open http://localhost:4000/otago_orienteering/
```

## Editing content (non-technical)

1. Go to `https://<site>/otago_orienteering/admin/` and log in with GitHub.
2. Pick **Events**, **Results** or **Pages**, fill in the form, and save.
3. Changes commit to the repo and the site rebuilds automatically.

## Deploy

Push to `main`. The GitHub Actions workflow in `.github/workflows/pages.yml`
builds and deploys to GitHub Pages. Enable Pages → *Build and deployment* →
*GitHub Actions* in the repo settings once.

## How to add an event

Create a file in `_events/` named `YYYY-MM-DD-slug.md` (or use the CMS). Upcoming
vs past is decided automatically from the date. Set `results:` to the results
page path once results are up.

## Training material

The club deliberately does **not** maintain its own training pages. The
Resources page links out to Orienteering New Zealand's national coaching and
skills material instead.
