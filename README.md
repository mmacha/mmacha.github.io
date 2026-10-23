## Meghanath's website

Static Jekyll site for [mmacha.github.io](https://mmacha.github.io), deployed by GitHub Pages from `master`.

- `index.html` — portfolio homepage (plain HTML, no Liquid)
- `notes/`, `_posts/`, `_layouts/` — the Notes section, built by Jekyll
- `resources/` — papers, resume, and other PDFs

### Design checks

The [impeccable](https://github.com/pbakaus/impeccable) design detector is installed under `.claude/skills/impeccable` (ignored by git). To scan:

```bash
.claude/skills/impeccable/scripts/impeccable detect index.html _layouts/note.html
.claude/skills/impeccable/scripts/impeccable detect https://mmacha.github.io/ --viewport 390x844
```

Notes pages need Jekyll to render; a plain file server shows raw Liquid. Use `jekyll serve` or check the live site after pushing.
