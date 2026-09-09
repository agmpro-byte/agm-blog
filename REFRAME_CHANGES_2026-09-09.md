# Reframe 2026-09-09 — agm-blog (branch `reframe-2026-09-09`, NOT pushed)

Brief: `docs/alden_briefs/2026-09-09_alden_website_messaging_update_handoff.md` (main repo). Editorial rule applied (stated assumption, not a ruling): dated posts keep their thesis and wording; only index/nav/description copy gets the sales-copy treatment; the Jobber bridge post gets a dated context note at its top.

**Render-pipeline fact that shaped the edits:** `execution/render_agm_blog.py` (main repo) regenerates `index.html` and every `post/<slug>/index.html` from `posts.json`. A hand-only edit to a rendered page is wiped on the next render. So every change here was made in `posts.json` (source) AND mirrored byte-identically into the rendered files, so a re-render is a no-op.

## posts.json (4 excerpts + 1 body prefix; titles, tags, dates, bodies otherwise untouched)
- `agentic-ai-moves-from-experiment-to-standard-operating-procedure` excerpt: "Agentic AI stopped being an experiment…" → "AI that takes action is no longer an experiment…".
- `the-agentic-shift-skipped-the-trades-so-we-built-it` excerpt: "What the agentic shift means…" → "What that shift means…".
- `agentic-ai-hits-field-service-in-2026-…` excerpt: "ship with agentic AI" → "ship with AI that acts on its own".
- `jobber-to-agm-bridge` excerpt: "Texas Turf runs on Jobber… So we built a bridge that syncs jobs…" → "A March 2026 deployment: how Texas Turf kept Jobber and added follow-up, review requests, and reactivation alongside it. The Jobber-specific bridge is no longer offered; the approach is now CRM-agnostic."
- `jobber-to-agm-bridge` body: a dated context paragraph is PREPENDED (`<p><em><strong>Context note, September 9, 2026:</strong> …</em></p>`) — the original post text is unchanged after it. The note says the Jobber-specific bridge is no longer offered and the approach is CRM-agnostic, names the Contractor Automation Score as the entry point, and mentions no review, listing, or dispute.

## index.html
- The same 4 excerpts, html-escaped exactly as the renderer's `esc()` produces. Tag histogram 674 → 674, ids/hrefs/style/script byte-identical to `main`.
- NOT changed (renderer hardcodes them at `render_agm_blog.py:483` and `:513`): `<meta name="description">`/OG/Twitter "Insights, case studies, and field-tested growth systems…" and the hero blurb. Change them in the renderer or they revert. Neither contains "agentic" or "Jobber".
- NOT changed: post titles on cards (they are the posts' own headlines), hero-image `alt` (= the post title), the tag taxonomy (`agentic`, `agentic-strategy` filter buttons and card badges are rendered from `data-tag` keys — renaming is a data-key change, i.e. code).

## post/jobber-to-agm-bridge/index.html
- Context note inserted as the first child of `.article-body` (adds 3 tags: `p`, `em`, `strong`). Everything else in the body untouched.
- The new excerpt mirrored into `<meta name="description">`, `og:description`, `twitter:description`, and `.article-excerpt` (description copy, per the rule). `<title>`, `<h1>`, canonical, JSON-LD, hero image, related posts untouched.

## Remaining "Jobber" / "agentic" mentions
- `index.html`: **11 in copy** — 2 tag-filter labels, 2 card badges, 3 post titles, 3 image alts, 1 FSM-blind-spots excerpt listing "Jobber, Housecall Pro, FieldRoutes, ServiceTitan" (post's own thesis, not a Jobber-centered AGM story); **16 in code** (hrefs, `data-tags`, image `src`).
- `post/jobber-to-agm-bridge/index.html`: **30 in copy** (the post body, deliberately unchanged, plus title/h1/alt) + **17 in code**.
- `posts.json`: bodies of 9 posts still mention Jobber as an FSM example; 3 post titles/bodies say "agentic". All are dated editorial content, left per the rule.

## Needs Troy
1. **Ruling on the editorial rule itself** — this run assumed dated posts keep their wording. If the three "agentic" post TITLES should also change, that is a slug/URL/redirect decision, not a copy edit.
2. **Tag taxonomy** — rename or keep the `agentic` / `agentic-strategy` tags (data keys; affects filter URLs).
3. **Renderer strings** — index meta description + hero blurb live in `execution/render_agm_blog.py:483,513`; decide whether they should carry the Executive Intelligence line.
4. **Publish** — this branch is not pushed. Pushing `main` publishes live on GitHub Pages.
