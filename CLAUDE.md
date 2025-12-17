# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a personal portfolio website for Meghanath Macha built as a static Jekyll site with the minimal theme. The site showcases professional work, research papers, and includes interactive data visualizations using pyLDAvis for topic modeling results.

## Technology Stack

- **Static Site Generator**: Jekyll with `jekyll-theme-minimal`
- **Frontend**: HTML5, CSS3, JavaScript (jQuery-based)
- **Styling**: CSS with responsive design using media queries
- **JavaScript Libraries**:
  - jQuery 1.10.2
  - FlexSlider for image carousels
  - Magnific Popup for lightbox functionality
  - Waypoints for scroll-triggered animations
  - FitText for responsive typography
  - Modernizr for feature detection
- **Data Visualization**: pyLDAvis for interactive topic modeling visualization
- **Analytics**: Google Analytics integration
- **Features**: Dark mode toggle with localStorage persistence

## File Structure

```
/
├── index.html              # Main portfolio page
├── investing.html          # Technical diligence services page
├── lifestyle.html          # Lifestyle research page
├── weekday_topics.html     # Weekday topic modeling visualization
├── weekend_topics.html     # Weekend topic modeling visualization
├── _config.yml            # Jekyll configuration
├── css/                   # Stylesheets and fonts
├── js/                    # JavaScript libraries and custom scripts
├── images/                # Profile pictures and assets
├── resources/             # PDFs (papers, resume, thesis, investment docs)
└── fonts/                 # Custom web fonts
```

## Development Commands

This is a static Jekyll site hosted on GitHub Pages. Since no package.json, Gemfile, or build scripts are present, the site uses GitHub Pages' built-in Jekyll processing.

### Local Development
```bash
# Install Jekyll (if not already installed)
gem install jekyll bundler

# Serve locally (if you have Jekyll installed)
jekyll serve

# Or use GitHub Pages gem
bundle exec jekyll serve
```

### Deployment
The site is automatically deployed via GitHub Pages when changes are pushed to the `master` branch.

## Key Features

1. **Responsive Design**: Mobile-friendly layout with media queries
2. **Dark Mode**: Toggle with localStorage persistence to prevent flash
3. **Interactive Visualizations**: pyLDAvis integration for topic modeling results
4. **Technical Diligence Services**: Dedicated investing page with Calendly integration
5. **Resource Downloads**: Direct links to research papers, resume, and investment documents
6. **Social Links**: Professional profile links and contact information
7. **Google Analytics**: Integrated tracking with multiple property IDs

## Content Management

- **Profile Information**: Edit `index.html` for personal details and bio
- **Investment Services**: Edit `investing.html` for technical diligence offerings
- **Research Papers**: Add PDFs to `/resources/` directory
- **Profile Pictures**: Update images in `/images/` directory
- **Topic Visualizations**: Replace data in `weekday_topics.html` and `weekend_topics.html`
- **Investment Documents**: Add sample memos and service overviews to `/resources/`

## Styling Notes

- Uses CSS custom properties for theming
- Font stacks include Libre Baskerville and Open Sans
- Icon fonts from Font Awesome and Fontello
- Critical CSS inlined for performance
- Dark mode styles applied immediately to prevent flash

## Analytics Configuration

The site includes Google Analytics with two tracking IDs:
- Legacy: `UA-105631264-1`
- GA4: `G-8M2DJ91XGL`