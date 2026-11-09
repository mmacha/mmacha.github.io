## Meghanath's website

Static Jekyll site for [mmacha.github.io](https://mmacha.github.io), deployed by GitHub Pages from `master`.

- `_layouts/default.html` — shared head (meta, GA4, JSON-LD), header with 3-state theme button, footer
- `css/site.css` — all styles for the homepage and Notes (cream paper, Newsreader serif, light/dark tokens)
- `fonts/newsreader-*.woff2` — self-hosted Newsreader (SIL OFL), latin subset
- `index.html` — homepage (`layout: default`; Notes list is generated from `site.posts`)
- `notes/`, `_posts/`, `_layouts/note.html`, `_layouts/post.html` — the Notes section
- `investing.html`, `lifestyle.html`, topic pages — older standalone pages using `css/` and `js/` legacy assets
- `resources/` — papers, resume, and other PDFs

### Build locally

```bash
brew install ruby                      # once; system ruby 2.6 is too old
/opt/homebrew/opt/ruby/bin/gem install --user-install jekyll kramdown-parser-gfm webrick
export PATH="/opt/homebrew/opt/ruby/bin:$HOME/.gem/ruby/4.0.0/bin:$PATH"
jekyll build                           # or: jekyll serve
python3 -m http.server 4173 -d _site   # serve the built site
```

### Design checks

The [impeccable](https://github.com/pbakaus/impeccable) design detector is installed under `.claude/skills/impeccable` (ignored by git). To scan:

```bash
.claude/skills/impeccable/scripts/impeccable detect http://localhost:4173/
.claude/skills/impeccable/scripts/impeccable detect https://mmacha.github.io/ --viewport 390x844
```

All pages now use Liquid layouts; build with Jekyll before scanning (a plain file server on the repo root shows raw Liquid).
