# 3D Hex Color Cube Inspector

An interactive, WebGL-powered 3D visualization of RGB color space. This tool maps 4,096 discrete hexadecimal colors across Cartesian coordinates ($16 \times 16 \times 16$), providing an intuitive way to explore digital color models and spatial color theory harmonies.

---

## Overview

In digital displays, colors are typically defined via the RGB additive model. Shorthand hex notation (`#RGB`) assigns values from `0x0` to `0xF` (0 to 15 in decimal) to each channel:

$$
\text{Color}(R, G, B) \quad \text{where} \quad R, G, B \in \{0, 1, \dots, 15\}
$$

This project structures the entire discrete gamut into a Euclidean 3D lattice, treating the Red, Green, and Blue channels as orthogonal spatial axes:

* **Origin $(0, 0, 0)$**: Pure Black (`#000` / `#000000`)
* **Opposite Apex $(15, 15, 15)$**: Pure White (`#FFF` / `#FFFFFF`)
* **Achromatic Axis**: The main diagonal line from $(0,0,0)$ to $(15,15,15)$ where $R = G = B$ contains neutral grays.
* **Primary Extrema**: Red $(15,0,0)$, Green $(0,15,0)$, Blue $(0,0,15)$
* **Secondary Extrema**: Yellow $(15,15,0)$, Cyan $(0,15,15)$, Magenta $(15,0,15)$

---

## Features

* **Real-Time 3D Exploration**: Full orbit, pan, and scroll-to-zoom controls driven by Three.js and OrbitControls.
* **Color Theory Harmonies**: Select any color point to map geometric relationships across HSL color space with interactive 3D vector lines:
  * **Complementary** ($180^\circ$ inversion across the color circle)
  * **Triadic** (Equilateral triangle spanning $120^\circ$ intervals)
  * **Analogous** ($\pm 30^\circ$ neighboring hues)
  * **Split-Complementary** (Dual nodes adjacent to the true complement)
  * **Monochromatic** (Luminance variations along identical hue vectors)
* **Curated Harmonic Swatches**: Displays up to three distinct matching colors in a sub-palette, complete with hovering tooltips and one-click clipboard copying.
* **Hex Search & Auto-Focus**: Jump directly to any 3-digit (`#RGB`) or 6-digit (`#RRGGBB`) color code via smooth camera interpolation (powered by Tween.js).
* **Smart Deselect & Roam**: Click empty canvas space to reset scaling without losing your current camera perspective.
* **High Performance**: Built with `THREE.InstancedMesh` to render all 4,096 spheres in a single draw call at 60 FPS.

---

## Navigation & Controls

| Action             | Control                                      |
|:------------------ |:-------------------------------------------- |
| **Orbit / Rotate** | Left Click + Drag                            |
| **Pan / Roam**     | Right Click + Drag                           |
| **Zoom**           | Mouse Wheel / Pinch Gesture                  |
| **Inspect Color**  | Left Click directly on any sphere            |
| **Copy Hex Code**  | Click the preview box or any harmonic swatch |
| **Deselect Point** | Left Click on empty space outside the cube   |
| **Help Overlay**   | Click the floating `?` button                |

---
