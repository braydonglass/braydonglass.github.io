# braydonglass.github.io

Personal site. Two static pages, no framework and no build step.

| File | What it is |
| --- | --- |
| `index.html` | Portfolio. Work, stack, background, contact. |
| `games.html` | Seven browser games written from scratch in plain JavaScript. |

## The lens

The panel at the top of `index.html` is a hand-written WebGL shader. A grid is drawn to an
offscreen 2D canvas, uploaded as a texture, then resampled through a sphere-refraction
lens that follows the cursor, with a little chromatic separation at the rim. If WebGL is
unavailable it falls back to drawing the grid flat.

## The games

Snake, Memory, Reaction, Tetris, Minesweeper, Flap, and Coil (a slither.io-style arena).
Every score is kept in `localStorage` on your own machine and is never sent anywhere.

## Motion

Text and section reveals use [anime.js](https://animejs.com) 4.5.0, vendored as
`anime.esm.min.js` so there is no CDN request. Every from-state is set in JavaScript
rather than CSS, so if the module fails to load the page is simply visible and static
instead of blank. Each animation also has a timeout that snaps it to its final state,
because an animation only progresses while `requestAnimationFrame` is running.

## Running it

Because `index.html` loads anime.js as an ES module, opening the file directly with
`file://` will be blocked by CORS. Serve it instead:

```
python3 -m http.server 8000
```

Then open http://localhost:8000. Nothing needs installing or compiling.

## Deploying

Served by GitHub Pages from the default branch, root folder. Because both pages are plain
static HTML, no Actions workflow and no build step are involved.
