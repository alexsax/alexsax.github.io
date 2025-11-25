# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a personal academic website hosted on GitHub Pages (alexsax.github.io). It's a static website showcasing research papers, publications, and academic achievements. The site is based on Jon Barron's website template and uses vanilla HTML, CSS, and JavaScript with no build system or dependencies.

## Common Development Commands

### Git Operations
```bash
# Deploy changes to GitHub Pages
git add .
git commit -m "Update research papers/content"
git push origin main

# Check current modifications
git status
git diff
```

### Local Development
```bash
# Open site locally in browser (macOS)
open index.html

# Start a simple HTTP server for local preview (if Python installed)
python3 -m http.server 8000
# Then visit http://localhost:8000
```

There are no build, test, or lint commands as this is a static website without dependencies.

## Architecture and Code Patterns

### HTML Structure (index.html)
The site uses a table-based layout with a maximum width of 800px. Each research paper entry follows this pattern:

1. **Paper Container**: A table row with two cells - image/video cell and content cell
2. **Image Hover Effects**: JavaScript functions for each paper (e.g., `sam3d_start()`, `sam3d_stop()`) control opacity transitions
3. **Media Handling**:
   - Static image: `images/{project}_one.jpg`
   - Hover video/image: `images/{project}_two.mp4` or `.jpg`

### JavaScript Pattern for Paper Hover Effects
Each research paper with interactive media follows this template:
```javascript
function {project}_start() {
  document.getElementById('{project}_image').style.opacity = "1";
}
function {project}_stop() {
  document.getElementById('{project}_image').style.opacity = "0";
}
{project}_stop()  // Initialize to hidden state
```

### CSS Organization (stylesheet.css)
- Color scheme: Blue links (#1772d0), Orange hover (#f09228)
- Highlighted papers use background color #ffffd0
- Dark mode support via `@media (prefers-color-scheme: dark)`
- Smooth transitions: `transition: opacity 0.2s ease-in-out`

### Adding New Research Papers
To add a new paper to the site, insert the following structure in index.html:

1. For papers with hover effects, add in the appropriate chronological position
2. Include both thumbnail and hover media in `images/` directory
3. Follow the existing naming convention: `{project}_one.jpg` and `{project}_two.{mp4|jpg}`
4. Add corresponding JavaScript functions if using hover effects

### File Organization
- `index.html`: All content and structure
- `stylesheet.css`: All styling
- `images/`: All media assets (use descriptive project names)
- `data/`: PDF documents (CV, etc.)
- No JavaScript files - all scripts are inline in index.html

## Important Conventions

### Image Optimization
- Thumbnail images should be reasonably sized (typically under 500KB)
- Videos for hover effects should be short (2-5 seconds) and compressed
- Use MP4 format for videos, JPG for photos, PNG for graphics with transparency

### Content Updates
- Research papers are ordered chronologically (newest first)
- Maintain consistent formatting for author lists and venue information
- Use the "Spotlight" or "Oral" tags sparingly for notable acceptances
- Keep descriptions concise (2-3 lines maximum)

### Deployment
Changes pushed to the main branch are automatically deployed to GitHub Pages. The site is available at https://alexsax.github.io/