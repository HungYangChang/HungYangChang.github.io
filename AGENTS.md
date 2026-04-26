# Repository Guidelines

## Project Structure & Module Organization

This repository is a static personal website for GitHub Pages. The main application is `index.html`, with inline JavaScript for theme switching, language switching, section minimization, and the Matrix canvas effect. Global styling lives in `style.css`. Static assets are split between `picture/` for site images and logos, and `attachment/` for downloadable files such as the CV PDF. The `.nojekyll` file keeps GitHub Pages from running Jekyll processing.

## Build, Test, and Development Commands

There is no build step; edit the HTML, CSS, and assets directly.

```bash
python3 -m http.server 8000
```

Runs a local static server at `http://localhost:8000`.

```bash
open index.html
```

Opens the page directly in a browser for quick checks.

No automated test suite is configured for this static site.

## Coding Style & Naming Conventions

Use vanilla HTML, CSS, and JavaScript; avoid adding build tools or frameworks unless explicitly required. Keep user-facing text bilingual by adding both `data-en` and `data-zh` attributes. Use semantic section structure and keep minimize buttons aligned with their target section IDs through matching `data-section` values.

In CSS, use variables for colors and theme-dependent values. Define light theme values in `:root` and dark theme overrides in `body[data-theme="dark"]`. Use relative asset paths such as `picture/icon.png` or `attachment/CV_Hung_Yang_Chang_2026_03_04.pdf`.

## Testing Guidelines

Testing is manual. Before submitting changes, verify light and dark themes, English and Chinese language states, section minimize/restore behavior, Matrix animation readability, responsive layout on mobile and desktop widths, and all asset links. For CV updates, confirm the linked filename and visible date are both current.

## Commit & Pull Request Guidelines

Recent history uses short imperative messages, sometimes with Conventional Commit prefixes, for example `feat: improve mobile view aesthetics` or `fix: resolve version history hover display issue`. Prefer concise messages that describe the user-visible change.

Pull requests should include a brief summary, screenshots for visual changes, manual test notes, and any deployment or cache-refresh considerations. Link related issues when available.

## Agent-Specific Instructions

Keep changes scoped to the static site unless asked otherwise. Preserve existing bilingual, theme, and localStorage behavior when editing `index.html`.
