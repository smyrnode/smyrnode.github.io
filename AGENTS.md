# AGENTS.md

Jekyll 4.x personal portfolio site (retro early-web aesthetic), deployed to GitHub Pages as `smyrnode.github.io`. No JavaScript, no tests, no CI.

## Commands

```bash
bundle install                      # install deps
bundle exec jekyll serve --livereload   # dev server on :4000
bundle exec jekyll build            # output to _site/
```

Ruby via `mise` (currently Ruby 4.0.5, Jekyll 4.4.1). No Makefile, no npm, no linters configured despite commit messages mentioning eslint/stylelint (those belong to the site's previous incarnation; ignore them).

## KNOWN BREAKAGE (fix first)

`_config.yml:10` contains a stray Cyrillic character `ё` on its own line (leftover typo). This makes `Psych::SyntaxError` and **any** `jekyll` command fail. Delete that line before doing anything else.

## Architecture

Single-page site. There is exactly one content page (`index.md`) and one layout (`_layouts/default.html`).

- `_config.yml` — site metadata, minima theme, `jekyll-seo-tag` plugin. `header_pages` is intentionally empty.
- `_layouts/default.html` — **overrides the minima theme layout**. It strips everything: renders only `{%- include head.html -%}` (from the minima gem, brings in SEO tags + stylesheet link) plus `{{ content }}`. No theme header/footer/sidebar. Any layout change must preserve the `head.html` include or SEO/CSS breaks.
- `index.md` — front matter is just `layout: default`; the body is **raw HTML**, not Markdown. All content (About/Skills/Projects/Contact) is hand-written HTML with custom classes.
- `assets/main.scss` — all styling lives here (~215 lines). Front matter `---\n---` at the top is **required** for Jekyll to process the SCSS. The design is intentionally retro: fixed 760px `.retro-wrapper`, system font stack (Verdana/Georgia), hex colors only (`#d4d0c8` background, `#0000cc` links), no CSS variables, no media queries.

## Conventions / gotchas

- **Do not** add minima's default `home`/`page`/`post` layouts or re-enable theme chrome — the whole point is the bare layout.
- Content edits go in `index.md` as HTML; keep using the existing class hooks (`.section`, `.skills-table`, `.projects`, `.retro-nav`, `.retro-footer`) since `main.scss` styles exactly those.
- `_site/` and `.jekyll-cache/` are build artifacts but **there is no `.gitignore`** — never commit them. Check `git status` before staging.
- Contact email in `index.md` is a placeholder (`dmitry@example.com`); real email is in `_config.yml` (`smyrnovd@gmail.com`). Unify when touching contact info.
- Footer says "© 2004" on purpose (retro joke). Don't "fix" the year.
- Deployment: push to `main` of the `smyrnode.github.io` repo; GitHub Pages builds from root. Jekyll version used by Pages may differ from local — keep the site plugin-light (only `jekyll-seo-tag`, which Pages whitelists; `jekyll-feed` is in the Gemfile but not in `plugins:`).
- No test suite. Verification = `bundle exec jekyll build` succeeds + eyeball `_site/index.html`.
