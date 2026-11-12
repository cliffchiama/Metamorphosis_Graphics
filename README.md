# Metamorphosis of a Butterfly

Computer Graphics project, Strathmore University (Faculty of Information Technology).

An animated short about the life cycle of a butterfly: caterpillar, chrysalis, emergence and first flight. This repository holds the graphics core, a **pure C++ software rasteriser** written without any graphics library. Later phases add OpenGL (wing-pattern shader) and a Blender-rendered film.

## Status

| Phase | Focus | State |
|-------|-------|-------|
| 1 | Design and foundations | Done |
| 2 | Primitives, polygons, curves, 2D transforms | Done (this repo) |
| 3 | Animation and OpenGL integration | Planned |
| 4 | Final render and demo | Planned |

## What is implemented

| Algorithm | Function in `main.cpp` | Used for |
|-----------|------------------------|----------|
| Bresenham line | `line()` | Twig, silk thread, leaf veins, grass |
| Midpoint circle | `fillCircle()` | Sun, caterpillar segments, head |
| Ellipse (parametric) | `ellipse()` | Wing spots, butterfly body |
| Scanline polygon fill (even-odd) | `fillPoly()` | Hills, trees, leaf, chrysalis, wings |
| Cubic Bezier curve | `bezier()` | Leaf, chrysalis and wing outlines |
| 2D affine transforms (3x3) | `Mat`, `T()`, `R()`, `S()`, `mul()`, `xf()` | Placement, rotation, wing mirroring and flapping |
| Colour interpolation | `mix()` | Sky and sun gradients |
| Frame animation | `main()` | Six-frame wing-flap cycle |

## Build and run

Requires a C++17 compiler (g++ or clang++). No other dependencies.

```bash
g++ -O2 -std=c++17 -o butterfly main.cpp
./butterfly
```

Output (960x540, PPM format):

- `scene.ppm` - the life-cycle scene
- `frame00.ppm` to `frame05.ppm` - wing-flap frames

Convert to PNG if needed, for example with ImageMagick: `magick scene.ppm scene.png`

## Files

- `main.cpp` - rasteriser and scene
- `scene.png` - current scene screenshot
- `flap_strip.png` - six-frame wing-flap sequence
- `Butterfly_Checkpoints_1_2.docx` - Checkpoint 1 and 2 report

## Next steps

- Camera and object animation (caterpillar crawl, chrysalis split, wing expansion, flight path)
- OpenGL integration and procedural wing-pattern shader
- Z-buffer, shading and textures
- DNA cell insert, forest and wildlife assets, and final film render in Blender
