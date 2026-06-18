# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Workshop website for **"Oops, I Erred" — Collecting, Curating and Using Imperfect Data for Realistic Scenarios**, a CoRL 2026 workshop by the Oopsie-Data team. The workshop focuses on collecting, curating, and using imperfect robotic data (failures, near-misses, noisy demonstrations) for improving robot learning.

## Build & Develop

This is a Jekyll site (GitHub Pages compatible). Use Docker for local development:

```bash
docker compose build          # first time / after Gemfile changes
docker compose up -d          # start dev server at http://localhost:4000
docker compose logs -f        # watch build output
docker compose down           # stop
```

The site auto-rebuilds on file changes via LiveReload (port 35729).

## Architecture

- **Jekyll + GitHub Pages**: static site using `github-pages` gem, Bootstrap 4 for layout
- **`_layouts/default.html`**: single layout — page title, navbar, header block with workshop name/conference/link
- **`_data/`**: YAML data files drive all people sections (no hardcoded names in HTML)
  - `organizers.yml` — 3 core organizers (photo cards on index)
  - `speakers.yml` — invited speakers with `role` field (Keynote/Panelist/tentative/requested)
  - `team.yml` — Oopsie-Data team members (inline list on index)
  - `advisors.yml` — faculty advisors (inline list on index)
- **Pages**: `index.html` (about + organizers), `speakers.html`, `schedule.html`, `submit.html`
- **`css/style.css`**: single stylesheet, uses `.person` cards and `.speakers-grid` responsive grid

## Key conventions

- Speaker/organizer images are hotlinked from their personal websites (no local copies)
- Dates marked "TBD" in `submit.html` need updating once the submission timeline is set
- The `repository` field in `_config.yml` is set to `oopsie-workshop/oopsie-workshop.github.io` — update if the GitHub org/repo name differs
