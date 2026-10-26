# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a personal portfolio website for Meghanath Macha built as a static Jekyll site. The site showcases professional work, research papers, and includes interactive data visualizations using pyLDAvis for topic modeling results.

## Technology Stack

- **Static Site Generator**: Jekyll (kramdown), built by GitHub Pages; no Gemfile
- **Homepage and Notes**: plain HTML on `_layouts/default.html` + `css/site.css`. No Tailwind, jQuery or JS libraries; the only scripts are GA4, the pre-paint theme script and the theme button handler
- **Fonts**: Newsreader (SIL OFL, self-hosted variable woff2, latin subset) for display serif; system sans stack for body
- **Legacy pages** (`investing.html`, `lifestyle.html`, topic pages) still use the old `css/` and `js/` assets (jQuery, FlexSlider, Magnific Popup, Modernizr, etc.)
- **Data Visualization**: pyLDAvis for interactive topic modeling visualization
- **Analytics**: GA4 (`G-8M2DJ91XGL`) in the default layout

## File Structure

```
/
├── index.html              # Homepage (layout: default)
├── _layouts/default.html   # Shared head/meta/JSON-LD, header, theme button, footer
├── _layouts/note.html      # Notes wrapper (680px measure) on default
├── _layouts/post.html      # Single note (on note.html)
├── _posts/                 # Notes posts (permalink /notes/:year/:month/:day/:title/)
├── notes/                  # Notes index + RSS feed
├── css/site.css            # All homepage + Notes styles, light/dark tokens
├── investing.html          # Technical diligence services page
├── lifestyle.html          # Lifestyle research page
├── weekday_topics.html     # Weekday topic modeling visualization
├── weekend_topics.html     # Weekend topic modeling visualization
├── _config.yml            # Jekyll configuration
├── css/                   # site.css + legacy stylesheets
├── js/                    # JavaScript libraries and custom scripts
├── images/                # Profile pictures and assets
├── resources/             # PDFs (papers, resume, thesis, investment docs)
└── fonts/                 # newsreader-{regular,italic}.woff2 + legacy icon fonts
```

## Development Commands

This is a static Jekyll site hosted on GitHub Pages. Since no package.json, Gemfile, or build scripts are present, the site uses GitHub Pages' built-in Jekyll processing.

### Local Development
```bash
# System ruby 2.6 is too old; use Homebrew ruby (no sudo)
brew install ruby
/opt/homebrew/opt/ruby/bin/gem install --user-install jekyll kramdown-parser-gfm webrick
export PATH="/opt/homebrew/opt/ruby/bin:$HOME/.gem/ruby/4.0.0/bin:$PATH"
jekyll build        # outputs _site/ (git-ignored); or jekyll serve
python3 -m http.server 4173 -d _site
```

### Design checks
The impeccable skill is installed at `.claude/skills/impeccable` (git-ignored, includes a 16MB binary). Run `.claude/skills/impeccable/scripts/impeccable detect <file-or-url>` for the anti-pattern detector; `/impeccable audit` runs the full audit playbook. All homepage and Notes pages use Liquid layouts, so build with Jekyll first and scan the served `_site` (e.g. `detect http://localhost:4173/`).

### Deployment
The site is automatically deployed via GitHub Pages when changes are pushed to the `master` branch.

## Key Features

1. **Responsive Design**: Editorial layout (192px left gutter grid) collapsing to one column under 800px
2. **Theme Control**: one text button in the header nav cycling System -> Light -> Dark; stores `localStorage.theme` (`light`/`dark`, removed for System) and applies `data-theme` on `<html>` via a pre-paint script; `theme-color` metas follow
3. **Notes**: homepage lists the 3 latest `site.posts`; `/notes/` lists all; RSS at `/notes/feed.xml`; BlogPosting/Blog JSON-LD emitted by default.html
4. **Interactive Visualizations**: pyLDAvis integration for topic modeling results
5. **Technical Diligence Services**: Dedicated investing page with Calendly integration
6. **Resource Downloads**: Direct links to research papers, resume, and investment documents
7. **Contact**: Book 30 minutes (Calendly), email, LinkedIn, Scholar, ZTO engineering blog
8. **Google Analytics**: GA4 only on the new layout

## Content Management

- **Profile Information**: Edit `index.html` for personal details and bio; head/meta/JSON-LD live in `_layouts/default.html`
- **Investment Services**: Edit `investing.html` for technical diligence offerings
- **Research Papers**: Add PDFs to `/resources/` directory
- **Profile Pictures**: Update images in `/images/` directory
- **Topic Visualizations**: Replace data in `weekday_topics.html` and `weekend_topics.html`
- **Investment Documents**: Add sample memos and service overviews to `/resources/`

## Styling Notes

- Design: cream paper, serif display headings, hairline rules; no cards, icons, gradients or shadows
- Tokens on `:root` in `css/site.css` (`--paper --ink --ink-soft --muted --hairline --accent --accent-light --white`); dark values under `html[data-theme="dark"]` and `@media (prefers-color-scheme: dark) { html:not([data-theme="light"]) }`
- Serif: `"Newsreader", Georgia, serif` for h1, h2, `.hero-lead`, `.contact-lead`, `.work-number`; regular file preloaded
- Muted text (#5a6560 light, #a3aca6 dark) never below 12px; skip link has its own hover/focus colors
- Legacy pages keep Plus Jakarta Sans and their own CSS

## Analytics Configuration

- GA4: `G-8M2DJ91XGL` (default layout)
- Legacy `UA-105631264-1` may remain on old standalone pages only