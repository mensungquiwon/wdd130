<!--
Repository: wdd130
Purpose: Short, actionable guidance for GitHub Copilot / AI agents to be immediately productive editing this static website.
--> 

# Copilot instructions — WDD130 static site

This is a small, static teaching website (WDD130). The site is primarily plain HTML, CSS and image assets organized by week. There is no build step or server framework. Edit conservatively: small, focused changes are preferred and always verify in a browser.

Key facts (big picture)
- Static site: HTML files at repository root and under `week01/`, `week02/` … and `wwr/`.
- Central stylesheet: `styles/styles.css` is linked from `index.html`. Several weeks have local `styles/` subfolders (e.g. `week02/styles/box-model.css`) — prefer editing the stylesheet already linked by the page you change.
- Assets: images live in `images/` and per-week `images/` folders. Pages use relative paths (e.g. `<link rel="stylesheet" href="styles/styles.css">`, `<img src="images/profile.webp">`).

When editing (rules & conventions)
- Preserve existing filenames and relative paths. Many pages link between folders using relative URLs — renaming files will break links unless updating all refs.
- Match each page with its intended stylesheet: check the page's `<link>` tag instead of moving global rules. Example: `week02/basic-layout.html` does not reference the top-level `styles/styles.css` — its styles are in `week02/styles/`.
- Prefer minimal, local edits. This repo is a student template: avoid large refactors unless requested.
- Keep HTML semantic structure (header, nav, main, aside, footer) already used across files.

Styling patterns to follow
- CSS variables are used in `styles/styles.css` (see `:root { --text-color: white; --bg-color: #00008b; }`) — follow this pattern when adding theme tokens.
- Images are sized with CSS variables (`--image-width`) and classes like `.box`. Reuse these classes where appropriate instead of creating many near-duplicate rules.

Preview / developer workflows
- There is no build system. To preview locally from the repository root, serve files with a simple HTTP server and open http://localhost:8000 in your browser.

  PowerShell (Windows):
  ```powershell
  python -m http.server 8000
  # or, if Node is available:
  npx http-server . -p 8000
  ```

- Use browser DevTools for layout/CSS debugging (site relies on margin/padding/grid/flex patterns across weekly examples).

Files and folders to inspect for examples
- `index.html` — top-level navigation and example of `styles/styles.css` linking and `images/profile.webp` usage.
- `styles/styles.css` — global variables, small grid layout and `.box` utility class.
- `week*/` folders — each week contains focused examples; copy patterns from the week that demonstrates the feature you need (e.g., `week03/overlay.html` and `week04/flexbox-layout.html`).
- `wwr/` — a small multi-page sub-site (rafting website). Use it as the pattern for small multi-page projects in the repo.

Integration & external dependencies
- External links/images are used occasionally (full URLs in `<img src="https://...">`). No external build or CI is required.

Commit & PR guidance
- Keep commits small and focused. In PR descriptions, reference which page(s) were previewed locally and which browser was used.

Common tasks with examples
- Change a page's layout: edit the page's linked stylesheet (example: `week02/styles/box-model.css`) and preview with the local server.
- Add an image: place the file in the appropriate `images/` folder and reference it with a relative path (example: `images/profile.webp` used by `index.html`).

If something is missing
- No test suites or CI configs are present. If you need build/test/CI, propose a minimal plan first (e.g., add a GH Pages deploy or a tiny HTML linter step) and list the exact files to modify.

Feedback
If any section is unclear or you want more examples (CSS patterns, navigation links, or a suggested local lint command), tell me which part to expand.
