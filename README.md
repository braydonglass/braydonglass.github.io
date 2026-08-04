# braydonglass.github.io

Personal site. Two static pages, no framework, no build step, no dependencies.

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

## Running it

Open `index.html` in a browser. That is the whole process. There is nothing to install
and nothing to compile.

## Deploying

Served by GitHub Pages from the default branch, root folder. Because both pages are plain
static HTML, no Actions workflow and no build step are involved.
