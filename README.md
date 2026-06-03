# 🌍 Gravity Simulator

<div align="center">

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Canvas](https://img.shields.io/badge/Canvas-000000?style=for-the-badge&logo=canvas&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
[![Physics](https://img.shields.io/badge/Physics-N%2Fbody%20Simulation-6C5CE7?style=for-the-badge)](https://en.wikipedia.org/wiki/N-body_simulation)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

**An awe-inspiring N-body gravitational simulation running entirely in your browser — no frameworks, no dependencies, just raw physics.**

[🚀 Live Demo](#) · [▶ Try a Preset](#presets) · [📖 Physics](#physics)

![Gravity Simulator Preview](https://img.shields.io/badge/Particles-1000%2B-00cec9?style=flat-square)
![Performance](https://img.shields.io/badge/Target-60%20FPS-dfe6e9?style=flat-square)

</div>

---

## What Is This?

Gravity Simulator renders the gravitational dance of celestial bodies in real time using the HTML5 Canvas. It solves the **N-body problem** — computing the mutual gravitational attraction between every pair of particles at each frame — and renders the result at a smooth 60 FPS.

This is not a pre-baked animation. Every trajectory emerges from Newton's law of universal gravitation. Add two bodies and you get ellipses. Add three and you enter **chaos**.

---

## ✨ Features

- **Real-time N-body simulation** — O(n²) gravitational force calculation every frame
- **Barnes-Hut approximation** — Quadtree optimization for large particle counts (optional)
- **5 curated presets** — Solar System, Binary Star, Three-Body, Galaxy Collision, Figure-8
- **Interactive particle spawning** — Click and drag to place bodies with initial velocity
- **Trail rendering** — Configurable particle trails that trace orbital paths
- **Collision detection** — Bodies merge on impact conserving momentum
- **Time controls** — Pause, slow-mo, and speed-up simulation time
- **Zoom & pan** — Navigate vast cosmic distances with mouse wheel and drag
- **Fully responsive** — Adapts to any screen size, mobile-friendly controls
- **Zero dependencies** — Pure HTML, CSS, and vanilla JavaScript

---

## ⚛️ Physics

The simulation is governed by **Newton's law of universal gravitation**:

```
F = G × (m₁ × m₂) / r²
```

...where `F` is the gravitational force between two bodies, `G` is the gravitational constant, `m₁` and `m₂` are the masses, and `r` is the distance between them.

<details>
<summary><strong>🔬 Dive deeper into the physics</strong></summary>

- **Force calculation**: Each frame, the net force on every particle is computed by summing the gravitational attraction from every other particle.
- **Numerical integration**: Positions are updated using **Velocity Verlet** integration, which is symplectic — meaning it conserves energy far better than naive Euler methods over long simulations.
- **Softening parameter**: A small ε is added to the distance calculation (`r² + ε²`) to prevent numerical blowups during near-collisions.
- **The Three-Body Problem**: With three or more bodies, the system becomes **chaotic** — infinitesimal changes in initial conditions lead to wildly different trajectories. This is a hallmark of non-integrable Hamiltonian systems and one of the oldest unsolved problems in classical mechanics. Your browser is simulating chaos theory in real time.
- **Barnes-Hut O(n log n)**: For large particle counts, the optional Barnes-HUT algorithm groups distant particles into a quadtree, treating far-away clusters as single pseudo-particles — dropping complexity from O(n²) to O(n log n).

</details>

---

## 🌌 Presets

| Preset | Description | Particles | Chaos Level |
|--------|-------------|-----------|-------------|
| ☀️ **Solar System** | Sun with 8 orbiting planets | 9 | Low |
| ⭐ **Binary Star** | Two stars dancing with orbiting debris | ~200 | Medium |
| 🔀 **Three-Body** | The legendary chaotic three-body problem | 3 | Maximum |
| 🌀 **Galaxy Collision** | Two galaxies colliding and merging | ~500 | High |
| ♾️ **Figure-8** | The famous stable figure-8 three-body orbit | 3 | None (stable) |

---

## 🎮 Controls

| Action | Control |
|--------|---------|
| Place a particle | **Left-click + drag** |
| Set velocity vector | **Drag length & direction** |
| Zoom | **Mouse wheel** |
| Pan | **Middle-click drag** |
| Play / Pause | **Spacebar** |
| Reset | **R** |
| Toggle trails | **T** |
| Toggle trails | **T** |
| Cycle presets | **1 – 5** |
| Time speed | **← / → arrows** |
| Spawn burst of particles | **B** (hold) |

---

## 🚀 Installation

No build tools. No npm. Just open it.

```bash
git clone https://github.com/mayank-dev-15/gravity-simulator.git
cd gravity-simulator
# Open directly in your browser — that's it
open index.html
```

Or serve it locally for the best experience:

```bash
# Python 3
python3 -m http.server 8080

# or Node.js
npx serve .
```

Then open `http://localhost:8080` in your browser.

---

## 📖 Usage

1. **Choose a preset** by pressing `1` through `5` on your keyboard.
2. **Watch gravity unfold** — the simulation starts automatically.
3. **Interact** — click and drag anywhere to spawn a new body with an initial velocity vector based on your drag direction.
4. **Experiment** — try the Three-Body preset, nudge a planet slightly, and watch the system diverge into chaos.

### Example: Replicate the Figure-8

1. Press `5` for the Figure-8 preset.
2. Press **Spacebar** to play.
3. Watch three equal-mass bodies chase each other in a perfect figure-8 — one of only three known stable periodic solutions to the three-body problem, discovered by Cris Moore (1993) and rediscovered by Chenciner & Montgomery (2000).

---

## ⚡ Performance Tips

| Tip | Impact |
|-----|--------|
| Disable trails | Major FPS boost with 500+ particles |
| Use Barnes-HUT | Enables 1000+ particles at 60 FPS |
| Reduce particle count | The biggest factor — force is O(n²) without optimization |
| Lower canvas resolution | Set a lower `devicePixelRatio` for weaker hardware |
| Close other tabs | Canvas rendering is GPU-dependent |

On a modern laptop, expect:
- **~200 particles** at 60 FPS with O(n²) brute force
- **~2000 particles** at 60 FPS with Barnes-Hut enabled

---

## 🛠️ Tech Stack

- **HTML5** — Structure and canvas element
- **CSS3** — Dark space theme, responsive layout, control panel styling
- **Vanilla JavaScript** — Physics engine, canvas rendering, input handling
- No frameworks. No libraries. No build step.

---

## 📄 License

This project is open source under the [MIT License](https://opensource.org/licenses/MIT).

---

<div align="center">

*"The universe is under no obligation to make sense to you." — Neil deGrasse Tyson*

**⭐ Star this repo if you find it as mesmerizing as an actual night sky.**

</div>
