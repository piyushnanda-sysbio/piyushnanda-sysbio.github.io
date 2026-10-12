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

The CSS already has a figure layout. Drop an image in `img/` and use:

```html
<div class="figure-row">
  <img src="/img/your-figure.png" alt="describe the figure">
  <p class="legend">Caption goes here.</p>
</div>
```

It stacks on mobile and sits side-by-side above 900px.

## Preview locally

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Paths are root-relative (`/css/main.css`), so opening the files directly with `file://`
will not load the stylesheet — use the server.
