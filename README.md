# azalhoseinian.github.io

Personal research & project hub — **Software Engineer · AI in Healthcare**.

Live at **https://azalhoseinian.github.io**

One file, no build step: `index.html` contains the markup, styles, and script.
Push to `main` and GitHub Pages redeploys in a minute or two.

---

## How to add things

All editable content lives in one object near the top of the `<script>` block,
marked `① CONTENT`. Nothing else needs to be touched — the cards, filters,
counts and log rows are rendered from it.

### Add a project

Append an object to `CONTENT.projects`:

```js
{
  title: "project-name",
  url: "https://github.com/AzalHoseinian/project-name",
  desc: { en: "One honest sentence.", fa: "یک جملهٔ دقیق." },
  tags: ["Python", "Healthcare Data"],
  category: "healthcare",   // "healthcare" | "software"
  year: 2026,
  status: null              // or "wip" / "active" / "archived"
}
```

- `category: "healthcare"` puts it under the **AI & Healthcare** filter, and the
  filter counts update by themselves.
- `desc: null` renders the card with no description — use it rather than
  writing something you can't stand behind.

### Add an experiment

`CONTENT.experiments` starts empty on purpose. Append:

```js
{
  date: "2026-09",
  title: { en: "Digital twin baseline", fa: "پایهٔ دوقلوی دیجیتال" },
  note:  { en: "What was tried and what came out of it.",
           fa: "چه امتحان شد و چه نتیجه‌ای داد." },
  state: "in progress",     // optional
  url: "https://github.com/..."   // optional
}
```

Entries sort newest-first and group under a year heading automatically.
Once the array has one item, the empty-state panel disappears.

### Update "Now"

- `CONTENT.now` — the focus areas shown as cards.
- `CONTENT.nowAlso` — the secondary line beneath them.
- `CONTENT.nowStamp` — the "last updated" date. Change it when you change the list.

### Focus areas

`CONTENT.focus` — set `primary: true` on exactly one entry to give it the accent dot.

---

## Interface text

Both languages live in the `② INTERFACE STRINGS` object (`UI.en` / `UI.fa`).
Every key used in the markup exists in both; adding a new one means adding it
to both. Static text carries a `data-i18n="key"` attribute in the HTML.

Switching to FA sets `lang="fa"` and `dir="rtl"`; the layout uses CSS logical
properties, so it mirrors without a separate stylesheet.

---

## Notes

- Theme and language choices persist in `localStorage`.
- `prefers-reduced-motion` disables all animation.
- `.nojekyll` stops GitHub from running the Jekyll pipeline over the site.
- No dependencies, no npm, no build — plain HTML, CSS, and vanilla JavaScript.
