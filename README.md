# Fourier 2

**A seed-based generative system for layered particle-curve compositions.**

A catalogue of computational textile compositions for fashion, textile and surface design — algorithmically drawn, seed-documented, and ready for production.

---

## Overview

Fourier 2 is a generative design system rather than a single artwork. Each composition is layered in three passes: a tree of filled circles clipped inside a full-frame circle, and two separate parametric curves — each drawn not as a continuous line but as a scatter of tiny filled particles, one per sample along the curve. The result is a dense, luminous field of dots that reads as both astronomy and confetti.

The system is designed for:

- **Fashion houses** adapting particle-ornament for apparel and accessories
- **Textile studios** developing repeat patterns and yardage
- **Surface designers** working across print, wallpaper, and interior applications

Every composition can be licensed, adapted, or commissioned to a brief.

---

## Concept

A curve, when it is *scattered into particles*, becomes a constellation — harmonic, precise, quietly yours.

The parametric curve — summed from layered sines and cosines — has always carried the structure of ornament. From the Fourier series that decomposes any periodic motion into pure tones, to the geometric curves of a Persian garden plan, harmony is one of the oldest systems of mathematical beauty we have. Fourier 2 translates that harmony into code. Each composition begins with a palette and a set of harmonic frequencies, and unfolds through recursion and particle scatter, until the frame fills with a luminous field of dots.

The palette, the tree structure, the curve frequencies, and the particle sizes are all derived from a single numeric seed.

Like the other still volumes in this series (Girih, Arachne, Celestial Grove, ChaotiColor, Citrus Mosaic, Crazy Knight Curve, Crazy Knight Line, Crazy Letter, cyPollock, Digital Pollen, Draconic Fractals, Dreamscape Watercolors, Elliott Waves, Ellipses, Enigma Sudoku, Ephemeral Whirls, Eyes, Fourier 1), **Fourier 2 is a static composition.** The plate, the framed plate, the surfaces, and the archive are all static frames. A constellation is something you read; its character is stillness, not motion.

---

## Features

- **Seed-based generation** — every composition is defined by a numeric seed and can be regenerated exactly
- **Deterministic output** — the same seed always produces the same composition
- **Three layered passes** — a circle tree, and two separate particle curves
- **Full-frame circle clip** — the circle tree is drawn inside a clip that fills the frame
- **Particle scatter** — every curve is rendered as a scatter of tiny filled particles, not a continuous line
- **Two independent curves** — an outer curve that spirals around the frame, and an inner cloud that clusters near the centre
- **Harmonic period** — each curve's total period is the LCM of its frequencies, so the curve closes exactly
- **Four-colour palette** — dark backgrounds, light backgrounds, hot foregrounds, and cool foregrounds
- **Glow effect** — each particle carries a soft shadow, giving the field a luminous quality
- **Performance-tuned** — batched particle paths, cached archive thumbnails, and debounced resize
- **Adaptive surfaces** — one seed applied across print, scarf, textile, and wall formats
- **Archive** — eight curated seeds available for immediate loading
- **Download** — export the composition as a high-resolution PNG
- **Keyboard shortcuts** — `R` for new seed, `S` to save

---

## Project Structure

```
.
├── index.html          # Main catalogue page
├── images/
│   ├── fav.svg         # Favicon
│   ├── tote.png        # Mockup: tote bag
│   ├── tee.png         # Mockup: t-shirt
│   └── cushion.png     # Mockup: cushion
└── README.md
```

---

## How It Works

### The Seed

A numeric seed (a large integer) initializes a deterministic pseudo-random generator. From this seed, the system derives:

- Two colours from the light background palette
- One colour from the dark background palette
- Two colours from the hot foreground palette
- One colour from the cool foreground palette
- A set of harmonic frequencies for each of the two parametric curves
- Amplitude coefficients and phase offsets for each curve
- Particle sizes for each sample point

Because the generator is deterministic, the same seed always produces the same composition — on any device, at any time.

### The Circle Tree

The first layer is a recursive tree of filled circles, drawn from the centre of the frame:

1. Starting at the centre, a circle is drawn at the current position with a random radius derived from a base `radius` value.
2. The tree branches: between 1 and 2 sub-branches, each rotated by a random angle.
3. The recursion stops at a fixed depth (10 levels).

This entire layer is clipped inside a full-frame circle — a circle of `w / 2` radius centred on the frame. So the tree of circles only appears inside the composition, and never spills off the edges.

### The Two Particle Curves

The composition then adds two separate parametric curves, each drawn as a **scatter of particles** rather than a continuous line.

**Curve 1 — Outer spiral.** Four frequencies in the range 5–8, four amplitudes in the range 2–6, four phase offsets. The curve is sampled from `θ = 0` to `θ = 2·LCM·π` and at every sample point a small particle is drawn — a short arc segment with a random start and end angle — producing a ring of glowing dots that spirals around the frame.

**Curve 2 — Inner cloud.** Four frequencies in the range 1–5, four amplitudes in the range 2–8, and three weighting coefficients in the range 0–2. This curve is scaled by a factor derived from `O = C1[0]/B1[0] + C1[1]/B1[1] + C1[2]/B1[2] + 1/B1[3]`, which normalizes the overall size. The result is a denser, more chaotic cloud that clusters near the centre and overlaps both the circle tree and curve 1.

### The Parametric Formula

Each curve is traced from a pair of summed sines and cosines:

```
x(θ) = Σ [Cₙ · R / Bₙ · sin(θ / Aₙ + Dₙ)]
y(θ) = Σ [Cₙ · R / Bₙ · cos(θ / Aₙ + Dₙ)]
```

where `Aₙ` are the frequencies, `Bₙ` are the amplitudes, `Cₙ` are the weighting coefficients, and `Dₙ` are the phase offsets — all drawn from the seed.

The curve is sampled from `θ = 0` to `θ = 2·LCM(A)·π`, so the curve always closes exactly, and the composition has a natural boundary.

### The Particles

Instead of drawing a continuous line, each sample point draws a small particle:

- **Curve 1 particles** — arcs of random start and end angle, with size proportional to `radius / 300 · rand()`.
- **Curve 2 particles** — arcs of random start and end angle, with size proportional to `radius / 100 · rand() + radius / (10 · lcm)`.

Each particle is filled with the curve's colour and carries a soft shadow blur, giving it a luminous, glowing quality. The result is a field of hundreds of small dots that together trace out the curve.

### The Colours

Four palettes meet in every composition:

| Palette                 | Role                       |
|-------------------------|----------------------------|
| Dark backgrounds        | Circle-tree inner colour   |
| Light backgrounds       | Circle-tree outer colour   |
| Hot foregrounds         | Curve 1 particle fill      |
| Cool foregrounds        | Particle glow              |

The result is a layered composition: dark circles inside, and two luminous particle curves scattered over the top.

### The Surfaces

The same seed is rendered across four surface formats. These are static frames — they represent the print-ready composition.

| Surface  | Aspect | Material          |
|----------|--------|-------------------|
| Print    | 1 : 1  | Cotton rag        |
| Scarf    | 3 : 1  | Twill silk        |
| Textile  | 4 : 3  | Fabric yardage    |
| Wall     | 2 : 3  | Wallpaper         |

Each surface uses the same underlying seed and structural logic — only the repeat, orientation, and scale change.

### Stillness

Like the rest of the still volumes, Fourier 2 does not animate. The plate is a single frozen frame — the composition is complete the moment it is generated.

This is a deliberate design choice. A constellation is not a swarm. It is not a rotation. It is a scattered field, laid down once and left. Its stillness is what makes it print-ready in the strictest sense: what you see is what you get.

---

## Usage

### In the browser

1. Open `index.html` in any modern browser.
2. Click **New Seed** to generate a new composition.
3. Click **Download** to save the composition as a PNG.
4. Scroll to the **Archive** section and click any plate to load it into Plate 001.

### Keyboard shortcuts

| Key | Action          |
|-----|-----------------|
| `R` | New seed        |
| `S` | Save as PNG     |

### Reproducing a composition

Each composition is identified by an 8-digit seed label displayed in the metadata panel. To reproduce a specific composition, note the seed and regenerate it programmatically:

```js
const rng = new RandomGenerator(seed);
const features = buildFeatures(rng);
renderComposition(canvas, features, rng);
```

Because the generator is deterministic, this will produce the identical composition on any device.

---

## Technical Notes

- **No build step.** The system is a single HTML file with inline CSS and JavaScript.
- **No dependencies.** All drawing is done with the native Canvas 2D API.
- **Deterministic.** The `RandomGenerator` class uses a xorshift-based PRNG seeded by an integer, so identical seeds produce identical outputs.
- **Static rendering.** Every canvas renders a single frame. There is no animation loop.
- **Feature isolation.** Cover, framed plate, surfaces, and archive thumbnails each derive their own feature set from their own local RNG, without disturbing the main plate's state.
- **Batched particle paths.** Each parametric curve builds a single path and fills it once, instead of issuing one `beginPath` / `arc` / `fill` per particle. This reduces the drawing cost by roughly 10–20×.
- **Cached archive thumbnails.** The eight archive plates are rendered once into offscreen canvases at init, then blitted with `drawImage` on every resize — eliminating eight full composition renders per resize.
- **Reduced shadow blur.** Particle shadows use `shadowBlur = Width`, half of the original, cutting the expensive shadow-composite cost without a visible difference.
- **Debounced resize.** Resize handler waits 300ms before firing, so rapid window resizing doesn't trigger many full redraws.
- **LCM-bounded curves.** Each parametric curve runs from `θ = 0` to `θ = 2·LCM(A)·π`, so it always closes exactly — no mismatched endpoints.
- **Curve 2 normalization.** The second curve is scaled by the `O` factor to keep its overall size bounded, regardless of the seed.
- **Clean shadow exit.** Every `renderComposition` resets `shadowBlur` and `shadowColor` at the end, so the glow from the particles never bleeds into subsequent drawing.
- **Responsive.** The layout adapts from large desktop down to very small mobile devices (tested at 360px viewport width).
- **Accessible.** Supports `prefers-reduced-motion`. Pinch-zoom is enabled.

### Browser support

Tested in current versions of:

- Chrome / Edge
- Firefox
- Safari (desktop and iOS)

---

## Licensing

All Fourier 2 compositions are **seed-documented** and available for licensing across textile, surface, and print applications.

- **Standard licenses** cover single-product production runs.
- **Commercial use, custom editions, or exclusive rights** are available on request.

Each license is issued against a specific seed ID. Regeneration of the same seed produces the identical composition — ensuring reproducibility between artist, studio, and manufacturer.

For licensing enquiries: [reyhanehdaneshdoost@gmail.com](mailto:reyhanehdaneshdoost@gmail.com)

---

## Commission

Fourier 2 is a generative design system, not a fixed artwork. It can be adapted for specific briefs:

| Service     | Description                                                       |
|-------------|-------------------------------------------------------------------|
| Licensing   | Existing seeds from the archive, licensed for production use      |
| Commission  | New compositions designed to your palette, repeat, and product    |
| Systems     | A private generative tool built for your studio's ongoing use     |

To begin a conversation: [reyhanehdaneshdoost@gmail.com](mailto:reyhanehdaneshdoost@gmail.com)

---

## Series

Fourier 2 is part of a computational textile series. Each volume approaches ornament from a different structural angle:

| Volume                     | Structure                    | Motion                     |
|----------------------------|------------------------------|----------------------------|
| Girih 1                    | Islamic geometric            | Static                     |
| Arachne                    | Rotating rings               | Static                     |
| Baroque Me Baby            | Baroque frames               | Static                     |
| Bezier 1                   | Concentric curves            | Static                     |
| Bezier 2                   | Single rotating curve        | Animated (plate)           |
| Brownian Graphe            | Graph networks               | Animated + interactive     |
| Celestial Grove            | Recursive branch trees       | Static                     |
| ChaotiColor                | Cellular automata            | Static                     |
| Citrus Mosaic              | Arc-and-triangle tiles       | Static                     |
| Crazy Knight Curve         | Knight's-tour smooth path    | Static                     |
| Crazy Knight Line          | Knight's-tour gradient       | Static                     |
| Crazy Letter               | Framed wavy lines            | Static                     |
| cyPollock                  | Scattered branch field       | Static                     |
| Digital Pollen             | Noise-driven texture         | Static                     |
| Draconic Fractals          | Tiled dragon curve           | Static                     |
| Dreamscape Watercolors     | Layered watercolor blooms    | Static                     |
| Elliott Waves              | Financial chart              | Static                     |
| Ellipses                   | Concentric elliptical rings  | Static                     |
| Enigma Sudoku              | Playable 9×9 puzzle          | Interactive (plate)        |
| Ephemeral Whirls           | Wandering looper field       | Static                     |
| Eyes                       | Layered iris portrait        | Static                     |
| Fibonacci Fourier          | Harmonic line field          | Animated (plate)           |
| Fixed Wave                 | Wave-equation field          | Animated (plate)           |
| Fourier 1                  | Layered parametric curve     | Static                     |
| **Fourier 2**              | **Particle curve field**     | **Static**                 |

The series is designed as a coherent whole — same page structure, same seed logic, same licensing and commission terms — so that each volume can be presented individually or as part of a larger body of work.

---

## Credits

- **Design & Generative System** — Reyhaneh Daneshdoost
- **Typefaces** — Cormorant Garamond · DM Mono
- **Platform** — Reyrove Studio
- **Edition** — Fourier 2, Autumn 2026

### On AI tools

Where technical obstacles were encountered, AI tools were used for debugging and code optimization. Every structural, aesthetic, and conceptual decision remained the artist's own.

---

## Links

- Website — [reyrove.github.io](https://reyrove.github.io/)
- Instagram — [@rey._.rove](https://www.instagram.com/rey._.rove/)
- LinkedIn — [Reyhaneh Daneshdoost](https://www.linkedin.com/in/reyhaneh-daneshdoost-730481160/)
- X — [@reyrove](https://x.com/reyrove)

---

© Fourier 2 · All compositions reproducible by seed · Computational Textile Design