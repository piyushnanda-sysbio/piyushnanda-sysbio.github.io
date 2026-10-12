# piyushnanda-sysbio.github.io

Personal academic site for Piyush Nanda. Plain static HTML — no build step, no Jekyll.
GitHub Pages serves the files exactly as they are (`.nojekyll` is present to guarantee that).

## Structure

```
index.html            About (home)
research/index.html   Research
publications/index.html
teaching/index.html   Teaching, talks, awards
contact/index.html
css/main.css          All styling (design tokens at the top)
img/piyush.jpg        Headshot
assets/cv.pdf         CV, linked from the nav
```

## Editing

- **Text**: edit the relevant `index.html` directly.
- **Colors / fonts / spacing**: all live in the `:root` block at the top of `css/main.css`.
  The accent is `--accent: #0f8b8d`. Dark mode overrides sit right below it.
- **Nav**: the nav block is duplicated in each page. If you add or rename a page, update
  all five. The `class="active"` marks the current page.
- **New CV**: replace `assets/cv.pdf`.

## Adding figures to the Research page

**Always resize first.** Slide-export PNGs are often 10,000+ px wide and several MB;
they display here at 460px. `sips` is built into macOS:

```sh
sips -s format jpeg -s formatOptions 80 -Z 1200 /path/to/source.png \
  --out img/your-figure.jpg
```

`-Z 1200` caps the long edge at 1200px — ample for a 460px slot on a retina screen,
and typically takes a 3MB PNG down to ~200KB.

Then paste this inside the relevant `<div class="entry">` in `research/index.html`:

```html
<div class="figure-row">
  <img src="/img/your-figure.jpg" alt="describe the figure">
  <p class="legend">Caption goes here.</p>
</div>
```

It sits side-by-side above 900px, stacks on mobile, and is rendered grayscale to match
the rest of the site (the filter is on `.figure-row img` in `css/main.css`).

## Preview locally

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Paths are root-relative (`/css/main.css`), so opening the files directly with `file://`
will not load the stylesheet — use the server.
