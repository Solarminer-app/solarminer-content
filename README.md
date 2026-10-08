# SolarMiner Blog Content

Public blog content for [solarminer.app](https://solarminer.app). This repository is the
**primary source** for blog posts: the landing page frontend fetches posts from here at
runtime (5-minute cache). The bundled copies inside
`landing_page_full_stack/landing-page-frontend/app/content/blog/` are only a fallback
used when GitHub is unreachable.

## Structure

```
blog/
  de/   <slug>.mdx     German posts
  en/   <slug>.mdx     English posts
```

- One file per post, filename (minus `.mdx`) is the URL slug: `/{lang}/blog/<slug>`.
- Slugs must be lowercase, hyphen-separated, ASCII.
- A post needs a frontmatter block:

```mdx
---
title: "Titel des Artikels"
date: "2026-10-08"
updated: "2026-10-08"
description: "Kurze Beschreibung für Listing, Meta-Description und Social Cards."
---

MDX body (Markdown + JSX). Internal links use absolute site paths, e.g.
`/de/pv-mining-calculator`.
```

`date` is required for sorting; `updated` is optional and shown as "Überarbeitet/Updated".

## Workflow

- Posts are normally committed by the SolarMiner content agent (monthly data posts).
- Humans may fix typos via PRs.
- `main` is deployed automatically (runtime fetch); no build or deploy step is needed.
- To take a post offline: delete or rename the file on `main` — it disappears within
  ~5 minutes.
- Never commit secrets, credentials or non-MDX content here.

## Fallback note

When this repository or GitHub is unreachable, the site serves the bundled snapshot
from the landing page image instead. Keep the bundled copies updated occasionally
(they also keep the site's own build/tests green), but `main` in this repo wins.
