# Still Life in WebGPU

An interactive WebGPU scene built around Hüseyin Zekâî Paşa's *Karpuzlu Natürmort* (Still Life with Watermelon). The painting hangs in the scene as a textured quad. In front of it are objects you can transform, a scene-graph hierarchy, an orbit camera with perspective and orthographic projection, and curves traced over the painted shapes.

All matrix, camera and curve maths is written by hand. There is no Three.js, no gl-matrix and no other maths or scene library.

**Live demo:** <github-pages-link> (needs a WebGPU browser, e.g. current Chrome or Edge)

![demo](docs/media/demo.gif)

## Features

- **Transformations:** a hand-written 4×4 column-major matrix library, with a T·R·S vs S·R·T switch and both matrices shown on screen
- **Scene graph:** a 3+ level hierarchy where world matrices come from traversal, with an animated joint and per-node debug axes
- **Camera & projection:** `lookAt` from cross products, a WebGPU perspective (z ∈ [0, 1]) and an orthographic projection, an orbit camera, and the camera's frustum seen from a second inspection camera
- **Curves:** cubic Bézier with the de Casteljau construction, a piecewise C¹ curve, Catmull–Rom, draggable control points on the painting, an object that follows the curve's tangent, and JSON export
- **Integration:** a single app with view switching, reset, debug toggles, and frame-time and vertex-count readouts

## Run

```bash
npm install
npm run dev
```

## Controls

| Control | What it does |
|---|---|
| <mouse drag> | orbit the camera |
| <…> | <…> |

## Structure

```
src/math/     matrices and vectors
src/scene/    scene graph and camera
src/curves/   Bézier and Catmull–Rom
src/render/   WebGPU setup, pipelines, WGSL shaders
src/ui/       controls and readouts
docs/         report.pdf and screenshots
curve.json    exported curve
```

## Credits

- Painting: Hüseyin Zekâî Paşa (1860–1919), *Karpuzlu Natürmort*, oil on canvas. © Sabancı University Sakıp Sabancı Museum. The image is not covered by this repository's license.
- Built for CS405 Introduction to Computer Graphics, Sabancı University, Fall 2026 (Project 1).
- AI assistance was used for explanation and debugging only; details are in the report's appendix.
