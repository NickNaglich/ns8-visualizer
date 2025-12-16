# NS8 Visualizer — Large-Scale Synthetic Field Inspection for ML

An interactive WebGL-based visualization tool for exploring **large structured synthetic datasets**
used in machine learning experiments. The visualizer supports full 3D field inspection or
2D slice-based views, enabling dataset debugging, feature isolation, and interpretability-style analysis
even at extremely large parameter sizes.

This tool is designed to support **synthetic data generation, benchmark development, and ML model evaluation** workflows.

---

## Why This Exists

Synthetic datasets are powerful for ML research, but they are often difficult to inspect once
they grow large or exhibit complex structure.

This visualizer allows you to:
- verify dataset correctness
- inspect long-range structure
- isolate feature patterns
- debug edge cases before training models
- explore temporal / phase-based structure in 3D fields

It is used alongside NS8 synthetic benchmarks to understand **what models see** before and after training.

---

## What It Visualizes

- Deterministic, structured 2D and 3D lattice fields
- Full 3D phase cubes or individual k-slices
- Extremely large parameter spaces (Very Large N)
- Feature-aligned filters and transformations

---

## Key Features

### Dataset Inspection & Debugging
- Slice-based viewing (2D k-slices) for ML-friendly inspection
- Full 3D voxel rendering for global structure analysis
- Tooltip inspection of `(row, column, phase, value)`

### Feature Isolation
- Filters for:
  - odd / even
  - prime / composite
  - exact value matches
  - modular number families
- Dim or hide non-matching values to isolate patterns

### Scalability & Performance
- Viewport limiter to focus on subregions of large datasets
- Skip rendering of hidden voxels for performance
- Instance-based rendering for large fields
- High-N safety warnings

### Very Large N Support
- Supports N values up to 999,999,999,999
- Automatic BigInt arithmetic when floating-point precision would be lost
- Deterministic results across runs

### Transform & Composition Support
- Multiple deterministic transform families
- Optional combination of transforms with wrap-to-N behavior
- Useful for generating controlled dataset variants

---

## Usage

1. Open  
   `HTML MCS Cube Visualizer/MCS_Cube_Visualizer_Very_Large_N.html`  
   in a modern browser (Chrome or Edge recommended).

2. Set dataset parameters (`N`, transform family, view mode).

3. Use the viewport limiter to focus on a region for performance.

4. Apply filters to isolate features or patterns of interest.

5. Orbit, pan, and zoom using mouse or touch.
   Hover to inspect individual values.

---

## Precision Notes

- For `N > 30,000,000`, the visualizer automatically switches to BigInt arithmetic
  in both the main thread and worker contexts.
- Transform combinations are summed using BigInt before wrapping to N.

This ensures correctness for large synthetic datasets used in ML evaluation.

---

## Dependencies

- Three.js (ES modules via unpkg)
- OrbitControls
- No build step required — runs as a static HTML application

---

## Intended Use

- Synthetic dataset inspection
- ML benchmark debugging
- Feature structure analysis
- Visualization-driven sanity checks before training
- Educational demonstrations of structured data

