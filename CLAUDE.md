# Post Affiliate Pro Changelog

Jekyll-based changelog site for Post Affiliate Pro, published at `dev.postaffiliatepro.com`.

## Project Structure

- `_posts/` — Changelog entries as Markdown files, named `YYYY-MM-DD-{version}.md`
- `_drafts/template.md` — Post template with frontmatter structure
- `_layouts/` — Jekyll HTML layouts (`post.html`, `default.html`)
- `_includes/` — Reusable HTML partials
- `_sass/` / `css/` — Stylesheets
- `_config.yml` — Jekyll config (site metadata, authors, permalink structure)
- `.claude/commands/create-changelog.md` — Slash command for creating new changelog entries

## Changelog Post Format

Each post uses this frontmatter:
```yaml
---
layout: post
title: {version}
author: mkendera
tags: [pap,Post Affiliate Pro,{version}]
---
```

Content is organized into sections: `## New Features`, `## Improvements`, `## Bug Fixes`, with subsections by area (e.g., `### User Interface`, `### REST API v3`, `### Banners`).

Issues are referenced from the GitHub repo `QualityUnit/PostAffiliatePro`.

## Git
- Do not add Co-Authored-By or other signatures to commit messages
- Commit messages should be short, e.g. `changelog for {version}`