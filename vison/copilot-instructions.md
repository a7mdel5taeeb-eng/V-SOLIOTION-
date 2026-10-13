<!-- Copilot / AI agent instructions for the Vision project -->

This repository is a very small static website (Arabic, RTL). The goal of these instructions is to give AI coding agents just enough local, actionable context to be immediately productive editing, reviewing, or extending the site.

1. Project overview
- Type: Static HTML + CSS only (no JS, no backend present in repository).
- Entry file: `v.html` — the full single-page site (Arabic, `dir="rtl"`).
- Styling: `style.css` — global variables defined in `:root` (colors, spacing); responsive rules at bottom.

2. High-level architecture and design intent
- Single-page brochure for a vehicle-transport service (Vision & Solution). Content is RTL; preserve `lang="ar"` and `dir="rtl"` when editing HTML.
- Visual system: uses a Google Arabic font (`Cairo`) and Font Awesome icons via CDN. Follow the existing color tokens in `:root` when adding UI elements: `--primary-color` and `--secondary-color`.
- Layout hints: header is `position: fixed` (so content starts below it — `margin-top: 60px` on `.hero`). Keep that behavior unless intentionally changing header UX.

3. Project-specific conventions and patterns
- No JavaScript expected. Contact form in `v.html` is static HTML (no `action` attribute). Do not add invisible assumptions about a backend; if you add form submission behavior, note it clearly in PRs and include a minimal mock or instructions.
- Text direction: all new text must support RTL and use the `Cairo` font. Avoid introducing LTR-only patterns without explicit justification.
- CSS variables: prefer updating or reusing `--primary-color` and `--secondary-color` rather than hardcoded colors.
- Responsive rule: small-screen nav is intentionally hidden (`nav ul { display: none; }` in the media query). If adding a hamburger menu, add both the markup and an accessible toggle; document the behaviour and test visually.

4. Developer workflows (how to preview and test changes)
- Quick preview (local file): open `v.html` in a browser. This is sufficient for most visual edits.
- Recommended: run a local static server for relative-URL correctness and fonts/CDNs. From repository root (PowerShell):

```powershell
# in project folder
python -m http.server 8000
# then open http://localhost:8000/v.html in your browser
```

- VS Code: using the Live Server extension is recommended for rapid development; it serves the same purpose as the `python -m http.server` command.

5. What to change and what to avoid
- Safe edits: copy/content updates, translations, color tweaks (use `:root`), typography changes (use `Cairo`), layout fixes respecting fixed header.
- Avoid: introducing a JS framework, adding server-side code, or changing directory structure without discussion. If you must add build tooling, create a small README and explain the choice in the PR.

6. Examples (concrete snippets to mirror)
- Add a new section: follow `.services` section structure — add a new `.card` inside `.cards` keeping the grid behavior.
- New CTA button: reuse `.btn-main` or `.btn-nav` to match spacing, colors, and hover treatment.

7. Commit & PR guidance for AI agents
- Keep commits small and focused (visual change + CSS update together). Example commit subject: `ui: add VIP insurance blurb to services section`.
- In PR descriptions, include: what you changed, one-sentence reason, and how to preview (e.g., `Open v.html or run python -m http.server 8000`).

8. Files to reference when making changes
- `v.html` — content, structure, RTL attributes.
- `style.css` — variables, layout rules, responsiveness.
- `New Text Document.txt` — currently empty; safe to ignore.

If any part of this guidance is unclear or you'd like more detail (for example, if you plan to add form handling or introduce JS), tell me which section to expand and I will iterate.
