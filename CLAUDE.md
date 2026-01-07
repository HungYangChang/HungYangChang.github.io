# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is James (Hung-Yang) Chang's personal portfolio website - a static single-page application built with vanilla HTML, CSS, and JavaScript. The site is hosted on GitHub Pages and showcases professional experience, publications, projects, skills, and personal interests.

## Architecture

### Core Structure
- **Single-page application**: All content is in `index.html` with client-side section navigation
- **No build process**: Pure HTML/CSS/JavaScript - edit and refresh
- **Static hosting**: Deployed via GitHub Pages (main branch)

### Key Files
- `index.html` - Complete application including embedded JavaScript (365 lines of inline script)
- `style.css` - All styling with CSS variables for theming
- `.nojekyll` - Disables Jekyll processing on GitHub Pages
- `attachment/` - Contains CV PDF and profile photo
- `picture/` - Contains university logos and pet photos

### Features Implementation

**Bilingual Support (EN/ZH)**
- All content uses `data-en` and `data-zh` attributes
- Language switching via inline JavaScript (lines 388-425 in index.html)
- State persisted in localStorage
- Some links have language-specific URLs via `data-zh-href` attribute

**Theme System (Light/Dark)**
- CSS variables defined in `:root` and `body[data-theme="dark"]` (style.css:2-30)
- Toggle functionality in inline JavaScript (lines 366-385 in index.html)
- Preference stored in localStorage

**Matrix Rain Animation**
- Canvas-based falling character effect (lines 519-568 in index.html)
- Background decoration, rendered at z-index: -1
- Uses random characters from: "ABCDEFGHIJKLMNOPQRSTUVWXYZ123456789@#$%^&*()*&^%+-/~{[|`]}"

**Section Minimization**
- Each section has minimize/maximize button (− / +)
- State persisted in localStorage as JSON array of section IDs
- Toggle logic in inline JavaScript (lines 439-517 in index.html)

## Development Workflow

### Local Development
```bash
# Simply open the file in a browser
open index.html

# Or use a local server (recommended for testing)
python3 -m http.server 8000
# Then visit: http://localhost:8000
```

### Deployment
- Push changes to `main` branch - GitHub Pages automatically deploys
- No build step required
- Changes are live immediately (may take 1-2 minutes)

### Testing
When making changes, verify:
1. Both light and dark themes render correctly
2. Both EN and ZH languages display properly
3. All interactive features work (language toggle, theme toggle, section minimize)
4. Matrix rain animation doesn't interfere with content readability
5. Responsive design works on mobile/tablet/desktop
6. All internal links (CV, profile photo, pet photos, university logos) resolve correctly

## Content Management

### Adding Experience/Publications/Projects
- Locate the relevant `<section>` in index.html
- Copy an existing item structure (e.g., `<div class="experience-item">`)
- Add both `data-en` and `data-zh` attributes for all translatable text
- Maintain consistent date formatting

### Updating CV
- Replace `attachment/CV_HungYang.pdf`
- Update the CV link date in the subtitle (line 27 of index.html) in both languages

### Adding Images
- Place in `picture/` (for content) or `attachment/` (for documents)
- Reference with relative paths: `picture/filename.ext` or `attachment/filename.ext`
- Optimize images before adding (this site has no build optimization)

## Important Conventions

### HTML Structure
- All user-facing text must have `data-en` and `data-zh` attributes
- Links that need language-specific URLs use `data-zh-href` for Chinese variant
- Section IDs must match the `data-section` attribute on minimize buttons
- Maintain semantic HTML structure (proper heading hierarchy)

### CSS
- Use CSS variables for all colors and theme-dependent values
- Define light mode in `:root`, dark mode in `body[data-theme="dark"]`
- All theme-dependent styles must use `var(--variable-name)`

### JavaScript
- All JavaScript is inline in index.html (no external .js files)
- localStorage keys: `preferredTheme`, `preferredLanguage`, `minimizedSections`
- The matrix rain canvas resizes on window resize events

## Common Gotchas

1. **Don't add build tools** - This is intentionally a zero-dependency static site
2. **Cache busting** - GitHub Pages caches aggressively; use Ctrl+Shift+R to hard refresh
3. **innerHTML vs textContent** - Language switcher uses innerHTML for content with HTML tags (check for `<` or `>` in data attributes)
4. **Section state persistence** - The experience section is explicitly excluded from auto-minimization on page load (line 511 in index.html)
5. **Matrix animation performance** - Running at 25ms interval (40fps); adjust if performance issues arise
