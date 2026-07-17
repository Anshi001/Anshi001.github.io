# anshika-singh.github.io

Personal portfolio — [anshika-singh.github.io](https://anshika-singh.github.io)

Built as a single static HTML file. No framework, no build step, no dependencies.

## Why static

The site has three projects and no blog, so a framework would be ceremony.
Zero dependencies means zero supply chain, an instant first paint, and nothing
to break in two years when I'm not looking at it.

## Engineering notes

- **No render-blocking anything.** No external fonts, no CDN, no JS on the critical
  path. Content is in the HTML, so it renders with JavaScript disabled.
- **Reveals are applied by JS, never by CSS.** Elements are visible by default and
  animate *from* their final state — if the script fails, nothing strands invisible.
  The common version of this bug hides content forever behind an animation that
  never runs.
- **`prefers-reduced-motion` is a first-class path**, not an afterthought: the aurora
  freezes, the pulse stops, reveals are disabled outright.
- **Motion is compositor-only.** The ambient blooms animate `transform`; the blur is
  baked into the gradient stops, so no filter is ever animated.
- **Pointer effects are gated** behind `(hover: hover) and (pointer: fine)` — keyboard
  users get zero magnetism and a real focus ring.
- **The nav glass uses literal values**, not custom properties: Safari silently drops
  `var()` inside `-webkit-backdrop-filter` ([WebKit bug 289800](https://bugs.webkit.org/show_bug.cgi?id=289800)).
- **`ProfilePage` + `Person` JSON-LD** for structured data.

## Structure

```
.
├── index.html      # the whole site
├── shots/          # project screenshots
└── README.md
```

## Run locally

```bash
python -m http.server 8000
# or
npx serve .
```

Then open http://localhost:8000

## Deploy

Pushed to `main` → GitHub Pages builds automatically.

---

Anshika Singh · [anshika91190@gmail.com](mailto:anshika91190@gmail.com)
