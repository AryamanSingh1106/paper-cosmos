# Paper Cosmos

A single-page website: the solar system cut from paper and animated like stop-motion. Scroll outward from the Sun, past all eight planets, and fall into a black hole that sends you back to the start.

No build step and no dependencies to install. Everything is in one file, `index.html`.

## Run it

Open `index.html` in any modern browser. An internet connection is needed for two things loaded from CDNs:

- **Syne** (Google Fonts) for all text. Falls back to the system sans-serif.
- **Lenis** (jsDelivr) for smooth scrolling. Falls back to normal scrolling.

## What's inside

| Section | What you see |
| --- | --- |
| Hero | Title built from colored paper tiles that fall in frame by frame, then jitter |
| Sun to Neptune | Eight planets, each on its own torn sheet of paper, with a stat and an unfoldable fact |
| Black hole | Spinning accretion disc and the "Fall back to the start" button |

## How it works

- **Stop-motion feel:** jitter animations use `steps(1)`, and the confetti, twinkling dust and stat scramble update at about 10 frames per second from one shared clock.
- **Cut-paper look:** an SVG displacement filter (`#rough`) roughens the edges of planets and the title. Shadows are flat offset shadows, not blurs. A grain overlay sits on top of everything.
- **Torn sheets:** each section's top edge is a randomly generated `clip-path` polygon, regenerated on every load.
- **Smooth scroll:** Lenis drives the scroll itself. Orbit rings, planet spin and scale, parallax, skew and dust all follow a smoothed scroll value every frame.
- **Cursor:** a paper dart eases toward the pointer at full frame rate and sheds paper scraps. Clicking anywhere bursts confetti.
- **Black hole transition:** a swirling clipped overlay expands from the button, the page jumps to the top while it covers the screen, then it shrinks away.
- **Accessibility:** respects `prefers-reduced-motion` (animations off, no smooth scroll, no cursor effects), fact cards are real buttons with `aria-expanded`, and focus outlines are visible.

## Customize

- **Palette:** the color variables at the top of the `<style>` block (`--bg`, `--red`, `--gold`, `--mint`, `--pink`, `--blue`). Each section sets its own sheet color through `--sheet` and its text color through `--t`.
- **Planets:** each is an inline SVG inside a `<section class="sheet">`. Copy a section to add a body, and the flip layout, torn edge and scroll effects apply automatically. Give the main group the class `rot` so it spins with scroll.
- **Smoothness:** change `lerp:.08` in the `new Lenis(...)` call. Lower is floatier, higher is snappier.
- **Frame rate of the stop-motion:** change `acc>=100` in the `loop` function (100 ms is 10 frames per second).

## Facts used

Sun holds 99.8% of the system's mass. Mercury's year is 88 Earth days. Venus averages about 465°C. Earth is 71% ocean. Olympus Mons on Mars is about 2.5 times the height of Everest. Jupiter could hold about 1,300 Earths. Saturn's rings are often only about 10 meters thick. Uranus is tilted about 98°. Neptune's year is about 165 Earth years.

## Credits

Typeface: Syne by Bonjour Monde. Smooth scrolling: Lenis by Studio Freight / darkroom.engineering.

Thank Youuuuu.........
