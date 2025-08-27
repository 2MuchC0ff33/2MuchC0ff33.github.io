# Copilot instructions for 2MuchC0ff33.github.io

Purpose: help an AI coding agent become productive quickly in this small, static GitHub Pages site.
```
Quick summary
- Static site: plain HTML and XML at the repo root and `docs/` (no build system or package manifest present).
- Primary focus: SEO, OpenSearch, and search-engine verification (Bing, Yandex).

Key files and why they matter
- `index.html` — main entry; heavy on SEO meta tags and a JSON-LD block. (See notes below: there are small syntax/typo issues to watch for.)
- `sitemap.xml` — canonical URLs for crawlers (uses absolute https://2MuchC0ff33.github.io).
- `opensearch.xml` — site search descriptor consumed by browsers/search clients.

- `BingSiteAuth.xml` and `yandex_610ec68818526181.html` — verification artifacts; values must match meta tags in `index.html`.
- `docs/` — content notes and templates (tone, phrasing, and examples live here).

Concrete repo examples (issues an agent will encounter)
- JSON-LD in `index.html` is malformed: missing a comma after `"@type": "Individual"`. Fix that before modifying schema content.
- `index.html` includes a typo meta `applicantion-name` — keep metadata consistent and correct it when editing.
- `sitemap.xml` uses absolute URLs — when adding pages, follow the same absolute URL pattern.

Developer workflows & quick checks
- No build step detected: GitHub Pages serves the repository root; deployment = push to the repo's default branch.
- After edits, perform these fast smoke checks:
	- Open `index.html` locally in a browser and view source to verify the `<head>` and JSON-LD are syntactically valid.

PowerShell examples for basic checks (optional)
```powershell
# quick raw fetch of index.html from the repo (adjust URL to your branch/user)
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/<your-user>/<repo>/main/index.html" -UseBasicParsing | Select-Object -ExpandProperty Content | Out-File -Encoding utf8 index.html
```
Conventions and patterns to follow
- Language: Australian English used across `docs/` and site metadata.
- Metadata-first edits: preserve meta tags and structured data when updating copy. Update verification files at the same time.
- File naming: keep verification filenames unchanged (e.g., `yandex_610ec68818526181.html`).

Integration points & external expectations
- Search engines (Bing/Yandex): rely on exact meta tokens in `index.html` and the corresponding verification files at site root.
- OpenSearch: `/opensearch.xml` must be present and valid UTF-8 XML for search clients.

Typical small tasks an agent will be asked to do
- Repair the JSON-LD in `index.html` and revalidate structured data.
- Correct small meta typos (e.g., `applicantion-name` -> `application-name`).
- Add a simple content page: create an HTML file, add metadata, and add an entry to `sitemap.xml` using the absolute https://2MuchC0ff33.github.io URL.

When to ask the human
- Changing Pages deployment branch or repository settings.
- Introducing a build tool (npm, Jekyll, Hugo) or server-side components — confirm before adding.

Commit and verification checklist
1. Commit with a clear message describing the change.
2. Run the smoke checks above (open in browser / validate JSON-LD / confirm verification tokens).
3. Ask for human review if the change affects deployment, verification, or introduces a build system.