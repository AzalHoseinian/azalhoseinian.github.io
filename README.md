# azalhoseinian.github.io

Personal AI × Healthcare project & research hub — **Software Engineer · AI in Healthcare**.

Live at **https://azalhoseinian.github.io**

One file, no build step: `index.html` holds the markup, styles, and script.
Push to `main` and GitHub Pages redeploys in a minute or two.

---

## The content model

Everything editable lives in one object marked `① CONTENT`, near the top of the
`<script>` block. Cards, group headings, counts, the flow diagram and the log
are all rendered from it — the HTML never needs touching.

### Add a project

Append an object to `CONTENT.projects`:

```js
{
  title: "project-name",
  url: "https://github.com/AzalHoseinian/project-name",
  desc: { en: "One honest sentence.", fa: "یک جملهٔ دقیق." },
  tags: ["Python", "Healthcare Data"],
  category: "health",     // "health" → AI × Healthcare  |  "software"
  featured: true,         // true → shows under Selected work, at the top
  year: 2026,
  status: "active"        // or null / "wip" / "archived"
}
```

Two rules worth knowing:

- **`featured: true`** promotes a project into **Selected work**. While no
  project is featured, that section shows an honest placeholder instead of
  looking empty. Everything else falls into **Other work** automatically.
- **`desc: null`** renders the card with no description. Use it rather than
  writing something you can't stand behind.

### Add an experiment

`CONTENT.experiments` is empty by design. Append:

```js
{
  date: "2026-09",
  title: { en: "Digital twin baseline", fa: "پایهٔ دوقلوی دیجیتال" },
  note:  { en: "What was tried and what came out of it.",
           fa: "چه امتحان شد و چه نتیجه‌ای داد." },
  state: "in progress",              // optional
  url: "https://github.com/..."      // optional
}
```

Entries sort newest-first. The placeholder disappears as soon as the array has
one item. `CONTENT.logYear` sets the year marker at the top of the timeline.

### The rest

| Key | Controls |
|---|---|
| `CONTENT.focus` | The satellite cards under the active-focus panel |
| `CONTENT.flow` | The Problem → Build → … → Repeat diagram |
| `CONTENT.now` | The focus areas in the Now section |
| `CONTENT.nowStamp` | The "last updated" date — change it when you change the list |
| `CATEGORY` | Display labels for the two project categories |

The **active focus** panel ("AI in Healthcare") and the hero copy are interface
strings, not data — edit them in `UI.en` / `UI.fa` under `focus.active*`.

---

## Two languages

Both live in `② INTERFACE STRINGS` (`UI.en` / `UI.fa`). Every key used in the
markup exists in both; a new key means adding it to both. Static text carries
`data-i18n="key"` in the HTML, and translated `aria-label`s use
`data-i18n-aria-label`.

Switching to FA sets `lang="fa"` and `dir="rtl"`. The layout mirrors through CSS
logical properties, so there is no second stylesheet. Persian labels
automatically drop the monospace face, which has no Persian glyphs.

---

## Notes

- Theme and language persist in `localStorage`; dark is the default.
- `prefers-reduced-motion` disables every animation.
- `.nojekyll` keeps GitHub from running the Jekyll pipeline over the site.
- No dependencies, no npm, no build — plain HTML, CSS, and vanilla JavaScript.
