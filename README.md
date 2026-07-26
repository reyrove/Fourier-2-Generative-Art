# Fourier 2 — Generative Art

[![Live Demo](https://img.shields.io/badge/demo-live-green?style=for-the-badge)](https://reyrove.github.io/Fourier-2-Generative-Art)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

> **Generative parametric particle art with Fourier synthesis.** Each refresh creates a unique composition of scattered particles following complex Fourier curves, with recursive tree patterns and vibrant colors.

## 🎨 Live Demo

<div align="center">
  <a href="https://reyrove.github.io/Fourier-2-Generative-Art" target="_blank">
    <img src="demo-screenshot.jpg" alt="Fourier 2 Website Demo" width="800" style="border-radius: 12px; box-shadow: 0 8px 32px rgba(0,0,0,0.4);"/>
  </a>
  <br><br>
  <a href="https://reyrove.github.io/Fourier-2-Generative-Art" target="_blank">
    <img src="https://img.shields.io/badge/🌐_View_Live_Demo-0a0a0a?style=for-the-badge&logo=githubpages&logoColor=white&color=c9a84c" alt="View Live Demo" width="300"/>
  </a>
  <br>
  <em>Click the image or button to experience the generative art</em>
</div>

## 👕 Apparel Preview

<div align="center">
  <img src="Fourier-2.jpg" alt="Fourier 2 on T-Shirt" width="600" style="border-radius: 12px; box-shadow: 0 8px 32px rgba(0,0,0,0.3);"/>
  <br>
  <em>Fourier 2 artwork printed on a T-shirt</em>
</div>

## ✨ Features

- **Particle Systems** — Scattered particles following Fourier curves
- **Parametric Curves** — Two different curve types with random parameters
- **Recursive Trees** — Organic branching patterns inside circular masks
- **Rich Color Palettes** — 37+ vibrant foreground and background colors
- **Mathematical Beauty** — LCM-based curve periods for complex patterns
- **Seed-Based** — Every composition is unique and reproducible via its seed
- **Save & Share** — Download as PNG with seed in filename
- **Apparel Mode** — Preview artwork on a T-shirt mockup
- **Responsive** — Works on desktop, tablet, and mobile
- **Pure JavaScript** — No external dependencies
- **Keyboard Shortcuts**:
  - `R` — Regenerate
  - `S` — Save image
  - `T` — Toggle apparel view

## 🎨 Artwork Details

| Parameter | Range | Description |
|-----------|-------|-------------|
| **Tree Depth** | 10 | Recursive branching depth |
| **Curve 1 Steps** | 80 | Particle count on first curve |
| **Curve 2 Steps** | 150 | Particle count on second curve |
| **Foreground Colors** | 9 options | Bright, vibrant colors |
| **Background Colors** | 28+37 options | Rich color palettes |

## 🌀 The Mathematics

### Fourier Synthesis
The parametric curves are generated using Fourier synthesis, where multiple sine and cosine waves with different frequencies and amplitudes combine to create complex, organic shapes.

### Particle Distribution
Particles are scattered along the Fourier curves, creating a sense of flow and movement. Each particle is rendered as a small arc with random rotation.

### LCM-Based Periods
The curve period is determined by the Least Common Multiple (LCM) of the frequency vectors, creating closed, repeating patterns with complex symmetry.

## 🚀 Quick Start

### Local Development

```bash
# Clone the repository
git clone https://github.com/reyrove/Fourier-2-Generative-Art.git

# Navigate to the directory
cd Fourier-2-Generative-Art

# Open in browser
open index.html
# or use a live server
```

### Deploy to GitHub Pages

1. Push to GitHub
2. Go to Settings → Pages
3. Select branch `main` and root folder
4. Your site will be live at `https://reyrove.github.io/Fourier-2-Generative-Art`

## 🧠 How It Works

The artwork is generated using a deterministic random number generator, seeded by timestamp + random noise. Every refresh:

1. **Setup**:
   - Random colors from multiple palettes
   - Random parameters for curves

2. **Tree Generation**:
   - Recursive branching with random sub-branches
   - Circle mask creates circular tree pattern
   - Max 3 branches per node

3. **Parametric Curve 1**:
   - 4 sine and cosine waves with random frequencies (5-8)
   - Random phase shifts (0-5)
   - Particles as small arcs with glow effect

4. **Parametric Curve 2**:
   - 4 sine and cosine waves with random frequencies (1-5 and 4-8)
   - Random coefficients (0-2)
   - Auto-scaling for optimal fit
   - Particles with varying sizes

5. **Rendering**:
   - Black background
   - Multi-layer composition
   - Glow effects for depth

## 📁 File Structure

```
Fourier-2-Generative-Art/
├── index.html          # Main application (all-in-one)
├── Fourier-2.jpg       # T-shirt mockup image
├── fav.svg             # Favicon
├── demo-screenshot.jpg # Website demo screenshot
├── README.md           # This file
└── LICENSE             # MIT License
```

## 🛠️ Tech Stack

- **Pure Vanilla HTML/CSS/JS** — No dependencies
- **Canvas API** — 2D rendering
- **CSS Flexbox/Grid** — Responsive layout
- **GitHub Pages** — Hosting

## 🎯 Interactive Controls

| Action | Keyboard | Button |
|--------|----------|--------|
| Regenerate | `R` | Click "regenerate" |
| Save Image | `S` | Click "regenerate" |
| Toggle Apparel | `T` | Click "apparel" |

## 🎨 The Creative Process

### Two Curve Types

**Curve 1 (Outer)**:
- Larger radius (3/4 of canvas)
- Higher frequencies (5-8)
- Phase shifts for variety
- 80 particles with arc shapes

**Curve 2 (Inner)**:
- Smaller radius (1/2 of canvas)
- Mixed frequencies (1-5 and 4-8)
- Auto-scaling based on coefficients
- 150 particles with varying sizes

### Particle Rendering
Each particle is rendered as a small arc with:
- Random start and end angles
- Random size variations
- Glow effect for depth
- Vibrant colors

### Tree Pattern
A recursive tree fills the center circle:
- 10 levels of depth
- 1-3 branches per node
- Branch length increases by 50%
- Same color for all branches

## 📱 Responsive Design

The application automatically adapts to:
- Desktop screens
- Tablets
- Mobile phones
- Landscape orientation
- Various aspect ratios

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Fork the repository
- Create a feature branch
- Submit a pull request

### Ideas for Contributions:
- New curve equations
- Additional color palettes
- Animation features
- Interactive controls
- Performance optimizations

## 📄 License

MIT License — see [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by Fourier analysis and particle systems
- Pure JavaScript implementation
- Special thanks to the creative coding community

---

**Built with ❤️ and Fourier particles**