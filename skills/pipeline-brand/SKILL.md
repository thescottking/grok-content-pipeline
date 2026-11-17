---
name: pipeline-brand
description: >-
  Render on-brand featured, X, and LinkedIn images and data charts for the
  content pipeline. Use when a drop needs a featured image, og:image, X
  header, LinkedIn share image, or a section chart from research/data.csv,
  or when someone says "make the article images," "brand this chart," or
  "render the social cards." Reads brand.md. If brand.md is missing, stop
  and tell them to run content-pipeline-setup. Look at every render before
  handing off.
---

# Pipeline Brand

This skill owns layout, sizing, rendering, and checking. It owns no color,
font, logo, or copy. Every one of those comes from `{pipeline_dir}/brand.md`
and from settings.md. Charts come only from `research/data.csv`.

## Before you render anything

Read these first. Do not invent a look around them.

1. `{pipeline_dir}/settings.md`: `brand_skill`, `banned_punctuation`,
   `site_url`, `author_name`.
2. `{pipeline_dir}/brand.md`: colors, fonts, logo path, image style, banned
   punctuation on images, footer or site name.
3. The drop's `article.md`, `outline.md` (which charts are flagged), and
   `research/data.csv` if charts are needed.
4. `{pipeline_dir}/voice.md` for every word that goes on an image, if that
   file exists. Honor `banned_phrases` and `banned_punctuation` even if it
   does not.

If `settings.md` or `brand.md` is missing, stop and tell the owner to run
`content-pipeline-setup`. Do not pick colors or fonts from memory.

If `brand.md` is thin (for example only two colors and no fonts), derive
the missing tokens (a muted text color, a surface color, a system sans as
the body face), tell the owner exactly what you derived, and offer to add
the real values through setup. A derived value that passes contrast is
still a guess about their brand.

## Sizes and files

In a pipeline run, write these under the drop's `images/` folder. Keep the
HTML sources in `images/src/`.

| Asset | Pixels | File |
|---|---|---|
| Featured / og:image | 1200 x 630 | `images/featured.png` |
| X header | 1500 x 600 | `images/x-header.png` |
| LinkedIn share | 1200 x 627 | `images/linkedin.png` |
| Section chart | sized to stay readable, often 1200 x 630 | `images/charts/section-<n>.png` |

These three social sizes are required for every article drop. Charts are
required only when `outline.md` flags them. If a flagged chart has no rows
in `research/data.csv`, skip it and log the skip in `gates.md`. Never
invent data.

## 1. Build the card from brand.md

Map `brand.md` onto CSS variables. Never type a hex or a font family that
is not in the file (or in the short derived list you already told the
owner about).

Typical tokens, filled from the file's headings (names can vary):

```css
:root {
  --bg:        /* Background */;
  --fg:        /* Body text / Ink */;
  --accent:    /* Accent, one per view */;
  --primary:   /* Primary */;
  --muted:     /* Muted text */;
  --rule:      /* Hairline / rule */;
  --font-display: /* Display / heading family */;
  --font-body:    /* Body family */;
  --font-mono:    /* Optional mono, for labels and numbers */;
}
```

**One accent per image**, on the single phrase or number to read first.
Status is never carried by color alone: label the series on a chart.

If `Logo` has a real file path and the file exists, use it in the footer.
If the path is empty or the file is missing, set the site or author name
in the display face. Never draw a logo.

Image-style notes in `brand.md` (light vs dark, terminal vs editorial,
photography vs type-only) choose the variant. When in doubt, use a light
ground, primary rail or footer band, and type only.

Copy on the card comes from the article, not from you: eyebrow (two to
five words, content type or series name), title (the claim, not the
topic; aim under 60 characters), kicker (one sentence that pays it off).
Every word follows `voice.md` and settings. No banned punctuation on
images. No real person unless the owner supplied the photo.

Alt text is required for every file. Say what the image says, including
every word on it, headline first. Under 250 characters. Never start with
"Image of".

## 2. HTML template

Write one HTML file per asset to `images/src/`. Keep the frame exact:
`html, body` are the pixel size of the asset, `overflow: hidden`. Load
web fonts with a `<link>` or `@font-face` from `brand.md`. A starter
layout:

```html
<!doctype html>
<html>
<head>
<meta charset="utf-8">
<link rel="stylesheet" href="FONTS_FROM_BRAND">
<style>
  :root { /* tokens from brand.md, plus --eyebrow, --title, --kicker */ }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html, body { width: WIDTH_PX; height: HEIGHT_PX; overflow: hidden; }
  .card {
    width: 100%; height: 100%;
    background: var(--bg); color: var(--fg);
    font-family: var(--font-body);
    display: flex; flex-direction: column;
    padding: 8% 10%; /* text stays in the middle 80 percent */
  }
  .eyebrow {
    font-family: var(--font-mono, var(--font-display));
    font-size: 14px; letter-spacing: 0.14em; text-transform: uppercase;
    color: var(--muted);
  }
  .title {
    font-family: var(--font-display);
    font-weight: 650; line-height: 1.1;
    margin-top: 24px; max-width: 90%;
  }
  .kicker { margin-top: 20px; color: var(--muted); max-width: 80%; }
  .footer {
    margin-top: auto; display: flex; align-items: center; gap: 12px;
    color: var(--muted); font-size: 16px;
  }
  .footer img { height: 28px; }
</style>
</head>
<body>
  <div class="card">
    <div class="eyebrow"></div>
    <h1 class="title"></h1>
    <p class="kicker"></p>
    <div class="footer"><!-- logo img or site name --></div>
  </div>
  <script>
    const r = getComputedStyle(document.documentElement);
    const set = (sel, key) => {
      const el = document.querySelector(sel);
      const v = r.getPropertyValue(key).trim().replace(/^["']|["']$/g, "");
      if (el) el.textContent = v;
    };
    set(".eyebrow", "--eyebrow");
    set(".title", "--title");
    set(".kicker", "--kicker");
  </script>
</body>
</html>
```

Fit long titles down until they stay inside the frame (a loop that lowers
`font-size` while the title's height overflows). Keep the title large
enough to read; if it has to shrink past about 34px, cut words and
re-render.

## 3. Render with Playwright

Use Chromium. Set the viewport to the exact asset size, `deviceScaleFactor`
1. Wait for `document.fonts.ready`, then a short extra pause so fallbacks
do not get captured. Screenshot the page, not a clipped element, to the
output path.

```js
const { chromium } = require("playwright");

const assets = [
  { src: "images/src/featured.html", out: "images/featured.png", w: 1200, h: 630 },
  { src: "images/src/x-header.html", out: "images/x-header.png", w: 1500, h: 600 },
  { src: "images/src/linkedin.html", out: "images/linkedin.png", w: 1200, h: 627 },
];

(async () => {
  const browser = await chromium.launch();
  for (const asset of assets) {
    const page = await browser.newPage({
      viewport: { width: asset.w, height: asset.h },
      deviceScaleFactor: 1,
    });
    await page.goto("file://" + require("path").resolve(asset.src));
    await page.evaluate(() => document.fonts.ready);
    await page.waitForTimeout(700);
    await page.screenshot({ path: asset.out });
    await page.close();
  }
  await browser.close();
})();
```

Always wait for `document.fonts.ready` before screenshotting. Without it
the render falls back to system fonts and the metrics shift. If a font
does not load, say so, try a local `@font-face` if the owner provided
files, and do not ship a silent fallback.

If Playwright is not installed on the box, install Chromium for the job
(`npx playwright install chromium`) rather than switching tools.

## 4. Charts from research/data.csv

Charts are evidence, not decoration.

1. Read `research/data.csv`. Use only the columns and rows that already
   exist. No computed totals unless the file already has them.
2. Build a simple HTML/SVG chart (bar or line, labeled axes, a source
   line). Colors come from `brand.md` chart colors, or from primary and
   muted if none are listed. Every series is labeled next to the mark,
   not by color alone.
3. The title is a claim that the data supports, not a topic. The source
   line is the source already recorded with the table.
4. Render the same way as a card. File it as `images/charts/section-<n>.png`
   to match the flagged section.
5. If the CSV is missing, empty, or does not contain the flagged table,
   skip the chart and log it. Never invent a series.

## 5. Check every render

The automatic checks are not enough. Open every PNG with a file reader
and look at it before you hand off. For each file:

- **Size.** The image is exactly the pixel size in the table.
- **Fonts.** The brand faces loaded. No unexpected system fallback.
- **Crop.** All text and the logo sit inside the middle 80 percent.
  Platforms crop the outer band.
- **Overflow.** Nothing is clipped, nothing collides, the title is not
  comically small.
- **Contrast.** Text and important marks read clearly on their ground.
- **Copy.** No banned punctuation, no banned phrases, no price unless
  `price_rule` allows it on images, no unsourced number.
- **People.** No real person unless the owner supplied the photo.
- **Alt text.** Written, and it includes every word on the image.

Nothing that fails this list ships. Fix the HTML and re-render. Do not
edit the PNG.

In a drop-in run, do not wait for a separate image approval. Hand back
the file paths and alt text. The images are reviewed in the final review.

## Rules

1. Every color, font, and logo comes from `brand.md`. Never type a new
   hex into a template and call it the brand.
2. One accent per image.
3. Featured is 1200x630, X header is 1500x600, LinkedIn is 1200x627.
   Text stays in the middle 80 percent.
4. Charts come only from `research/data.csv`.
5. Look at every render. A screenshot that succeeded can still be wrong.
6. The HTML is the source. Revise it and re-render rather than editing
   the PNG.
7. Every word on an image follows `voice.md` and settings.
8. No passwords or keys in files or chat.

Adapted from B2B PMM Skills (github.com/thescottking/b2b-pmm-skills)
