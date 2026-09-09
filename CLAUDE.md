# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal academic homepage for Nikita Lukhanin, served at https://lukhanin.net via GitHub Pages (`CNAME` + `_config.yml`). It is a single hand-written static page — no build step, no package manager, no tests, no JavaScript beyond the JSON-LD block and the Umami analytics tag. Pushing to `main` deploys.

**Always commit and push after every change.** There is no staging environment; the user expects each edit to land on the live site immediately, so finish every task with `git add`, `git commit`, and `git push origin main`.

`_config.yml` sets a Jekyll theme, but `index.html` is a plain HTML file with its own `stylesheet.css`, so the theme has no visible effect. Don't add Jekyll front matter or layouts unless intentionally migrating to Jekyll.

## Developing

Preview locally by opening `index.html` directly, or from the repo root:

```
python3 -m http.server 8000   # then http://localhost:8000
```

Verify changes in the browser at both desktop width and ≤640px (the mobile breakpoint in `stylesheet.css`).

## Files

- `index.html` — the whole site. Sections, top to bottom: `<head>` (meta description, canonical URL, Open Graph/Twitter cards, favicons, Person JSON-LD, analytics) → intro + photo → Research → News → Student Mentoring (Memories, then Undergraduate/other mentoring columns).
- `stylesheet.css` — Lato `@font-face` declarations (first ~100 lines), typography classes (`.name`, `.papertitle`), and the responsive block at the bottom.
- `images/` — photos referenced from the page; `images/favicon/` — the favicon set.
- `data/` — CV PDF linked from the page.

## Conventions when editing `index.html`

- Layout is nested `<table>` elements with inline styles (the classic academic-homepage template). Match that style rather than introducing a CSS framework; only `.head-text`, `.head-photo`, and `.mentor-col` classes drive the mobile stacking, so keep those on the intro and mentoring cells.
- **News** entries are `<tr><th scope="row" style="width: 20%">Mon, YYYY</th><td>…</td></tr>`, newest first.
- **Memories** entries use the same `th`/`td` row pattern with `MM/YY` dates and a `(photo)` link to `images/…`, newest first.
- **Mentoring** entries are `<li>` items: `<strong>Name (MM/YY - MM/YY|Current)</strong><br><em>Institution</em>`.
- When the profile photo, bio, or affiliations change, update the matching values in the meta description, Open Graph/Twitter tags, and the JSON-LD block in `<head>` as well — they duplicate content from the body.
