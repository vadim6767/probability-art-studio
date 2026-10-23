# AGENTS.md

## Purpose

Probability Art Studio is an experimental system for producing **static typographic artworks** from mathematically defined probability events. Each artwork connects:
1. a concrete event and its input data;
2. an accurate, explicit probability derivation;
3. a visual reference or geometric construction;
4. typographic mapping that constructs the depicted form.

The artist defines the visual language. Do not invent universal mapping rules or lock in a full architecture.

## Current development direction

**Do not rebuild the React/SVG editor.** The previous editor experiment has been abandoned.

Prototype a small, reproducible image-to-mask-to-typography workflow, beginning with exactly one artwork. Python scripts, raster reference images, masks, and SVG output are allowed. Avoid front-end frameworks, custom interfaces, animation engines, backend services, and 10,000-item pipelines unless explicitly requested.

Prefer the smallest working experiment over building a general-purpose tool.

## Static artwork

- Outputs are **static**. No motion, animation, timelines, video, GIFs, or animated SVG.
- A generated or photographed reference image may be raster.
- Processing masks may be raster, grayscale, or vector.
- Prefer SVG for final typographic geometry when it is practical; PNG previews are useful.
- The reference image is an input to geometry extraction, not a required visible layer of the final art.
- Keep enough intermediate files to inspect the process.

## Mathematics

- Always use an explicit probability statement beginning with `P(...)=` or `P=`.
- Preserve the complete derivation, its assumptions, input parameters, and exact probability where possible.
- Do not replace the mathematical expression with only a decimal or percentage.
- Validate probabilities before using them.
- Distinguish the mathematically authoritative expression from repeated or decorative glyphs.
- Decorative placement may repeat symbols but must not imply an incorrect equation.

First event: **two heads on two independent fair coin tosses**.

```text
P(H₁ ∩ H₂) = P(H₁) · P(H₂) = (1/2) · (1/2) = (1/2)² = 1/4 = 0.25
```

## Reference and mask workflow

For the first experiment:
1. Make a clean, static reference of a tilted coin with visible face and rim.
2. Extract at least silhouette, face and rim regions when practical.
3. Optionally derive a tonal map to guide glyph density or size.
4. Map mathematically relevant typography to regions and/or contours.
5. Export and evaluate static SVG/PNG variants.

Do not treat a simple block of text clipped to the silhouette as the finished solution. Evaluate whether the typography itself conveys the geometry, perspective, and surfaces of the object.

The exact mapping of tokens to specific regions is **not yet a permanent project rule**. The artist decides it through experiments.

## Implementation

- Python is preferred for early image processing and procedural layout tests.
- Add Pillow, NumPy, vector tracing, font processing, or other dependencies only when a specific task needs them.
- Keep calculations, region extraction, typography layout, and rendering logically distinct where practical.
- Use small scripts, readable configuration, stable identifiers, and deterministic seeds for procedural output.
- Retain image provenance, source filenames, rendering settings and experiment parameters.
- Do not add a UI or generalized editor unless requested.

## Scope

Work on **ART #001** before designing scale-out to 10,000 events. Do not prematurely add NFT minting, metadata infrastructure, web apps, wallets, user accounts, cloud services, or other unrelated capabilities.

## Codex operating guidelines

- Read this file and inspect the repository before writing code.
- Make focused, reversible changes.
- State any assumptions, especially artistic assumptions.
- Do not change visual rules merely to simplify coding.
- Explain how to run a script and what output it should produce.
- Run applicable checks and report what actually ran.
- Do not commit, push, delete user files, or alter repository branches without explicit instruction.

## Artistic authority

The creator owns the architecture, typographic system, mask interpretation and final artistic decisions. This file supplies engineering boundaries only; it is not a visual-style specification.
