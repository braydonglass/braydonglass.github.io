# braydonglass.github.io

Personal site. Two hand-written static pages, plus one Next.js page that ships as a
static export.

| File | What it is |
| --- | --- |
| `index.html` | Portfolio. Work, stack, background, contact. |
| `games.html` | Seven browser games written from scratch in plain JavaScript. |
| `cepa82/` | The Cepa 82. A scroll-scrubbed product page, exported from Next.js. |

## The lens

The panel at the top of `index.html` is a hand-written WebGL shader. A grid is drawn to an
offscreen 2D canvas, uploaded as a texture, then resampled through a sphere-refraction
lens that follows the cursor, with a little chromatic separation at the rim. If WebGL is
unavailable it falls back to drawing the grid flat.

## The games

Snake, Memory, Reaction, Tetris, Minesweeper, Flap, and Coil (a slither.io-style arena).
Every score is kept in `localStorage` on your own machine and is never sent anywhere.

## The Cepa 82

A product page for a yellow onion, written in the register of a watch campaign and never
breaking character. The hero is 144 JPEG frames drawn to a canvas and indexed by scroll
position, not a `<video>` element, because video seeking stutters when you scrub it. A
`requestAnimationFrame` loop reads `getBoundingClientRect()` each frame; there is no
scroll listener.

The source clip is a raytracer I wrote in Rust with no dependencies. It models the bulb as
eleven nested ellipsoid shells, opens an animated wedge through them, and pipes raw RGB
straight into ffmpeg. Every specification on the page is true of Allium cepa.

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

Served by GitHub Pages from the default branch, root folder. No Actions workflow: the two
hand-written pages need no build, and `cepa82/` is committed already built. Its source
lives outside this repo, so rebuilding it means running `npm run export:pages` there and
copying `out/` back over `cepa82/`. The `.nojekyll` file at the root is what stops Pages
from swallowing `cepa82/_next/`.
