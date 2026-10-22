# AGENTS.md

## Project

This repository contains a generative art editor for creating static probability-based typographic artworks.

The project is experimental and design-driven. Do not make assumptions about the final visual language, architecture, or artistic rules unless they are explicitly documented in the repository.

## Core principles

- The final artworks are static images.
- Do not introduce animation systems, timelines, motion libraries, or animated exports unless explicitly requested.
- SVG is the primary rendering format.
- Mathematical expressions must remain editable and structurally accessible.
- Do not rasterize mathematical expressions during the editing process.
- Mathematical symbols may become part of geometric compositions.
- Formula elements must remain independently selectable whenever technically possible.
- The editor should support direct manipulation of visual elements.
- Avoid unnecessary abstractions during the MVP stage.
- Prefer simple, inspectable implementations over overly complex frameworks.

## Mathematical expressions

Probability expressions should generally use explicit probability notation.

Prefer expressions such as:

P(A) = ...

P(A ∩ B) = ...

P(X = k) = ...

Do not simplify expressions to only their final decimal result unless explicitly requested.

Example:

P(H₁ ∩ H₂)
= P(H₁) · P(H₂)
= (1/2)²
= 1/4
= 0.25

The complete derivation may be artistically meaningful and should not be discarded automatically.

## Rendering

Use SVG for:

- text
- mathematical symbols
- paths
- circles
- ellipses
- rectangles
- polygons
- lines
- masks
- clipping paths
- groups
- transformations

Do not use HTML elements positioned over the artwork when the same result can reasonably be represented inside SVG.

The artwork coordinate system should be deterministic.

The same project data should produce the same composition unless randomness is explicitly part of the project data or generated from a stored seed.

## Editor behavior

The editor should eventually support:

- selecting objects
- moving objects
- scaling objects
- rotating objects
- changing typography
- changing visual properties
- reordering layers
- grouping
- ungrouping
- duplicating objects
- deleting objects
- undo
- redo
- project serialization

Do not implement all features at once.

Build the minimum functionality required by the current task.

## Data model

Keep project data separate from presentation and UI state.

Prefer serializable data structures.

Artwork state should be capable of being saved as JSON.

Avoid storing critical artwork information only inside React component state or DOM state.

Objects should have stable IDs.

Example conceptual structure:

```ts
type ArtObject = {
  id: string
  type: string
  x: number
  y: number
  rotation: number
  scaleX: number
  scaleY: number
}
```

Do not treat this example as a fixed schema. Extend it only when necessary.

## Event data

Probability events should eventually be represented as structured data.

An event may contain:

- ID
- title
- description
- category
- input parameters
- mathematical expression
- exact probability
- decimal probability
- visual metadata
- mapping metadata

Do not hard-code event-specific logic directly into UI components if it can reasonably live in event data.

## Typography

Typography is a core part of the artwork, not merely UI decoration.

Mathematical tokens may need to:

- be positioned independently
- be resized independently
- follow SVG paths
- form contours
- fill regions
- become masks
- become repeated patterns
- participate in geometric structures

Avoid implementations where an entire formula becomes one flat SVG image unless explicitly requested.

## UI

The interface is a tool, not the artwork.

Keep the editor UI visually restrained.

Prioritize:

- workspace size
- direct manipulation
- clarity
- inspectability
- predictable controls

Avoid excessive decoration, gradients, animations, or dashboard-style UI unless requested.

## Dependencies

Before adding a dependency:

1. Check whether the feature can be implemented simply with React, TypeScript, and native SVG.
2. Prefer small focused libraries.
3. Avoid large editor frameworks unless their benefit is clearly justified.
4. Do not add animation libraries.
5. Do not add canvas-based rendering libraries without explicit approval.

## Code quality

Use TypeScript.

Prefer:

- small components
- clear types
- pure utility functions
- explicit state transitions
- readable names

Avoid:

- giant components
- deeply coupled UI and artwork logic
- unnecessary class hierarchies
- premature optimization
- hidden mutation
- magic constants

Extract constants when they define meaningful editor behavior.

## File organization

Keep concerns separated.

A reasonable starting direction is:

```text
src/
  components/
  editor/
  math/
  model/
  rendering/
  utils/
  data/
```

This is not a mandatory architecture.

Do not reorganize the entire repository unless the current task requires it.

## Scope control

Do not build features that were not requested.

Especially do not prematurely implement:

- blockchain integration
- NFT minting
- wallet connections
- marketplaces
- metadata upload
- 10,000-piece batch generation
- backend infrastructure
- user accounts
- cloud storage
- collaboration
- animation

Those may be added later.

## MVP priority

The first priority is proving that mathematical notation can be transformed into editable typographic geometry.

The MVP should focus on a single artwork first.

Initial event:

Two consecutive heads.

Example expression:

P(H₁ ∩ H₂)
= P(H₁) · P(H₂)
= (1/2)²
= 1/4
= 0.25

Initial visual subject:

Coin.

The exact artistic mapping is not defined in this file and must not be invented without user direction.

## Working rules for Codex

When modifying the repository:

- inspect existing code before changing architecture
- preserve working functionality
- make focused changes
- do not rewrite unrelated files
- avoid introducing speculative features
- run available type checks and builds after meaningful changes
- fix errors caused by your changes
- explain significant architectural decisions
- clearly state assumptions when requirements are ambiguous
- prefer reversible changes during experimentation

When artistic or architectural intent is unclear, preserve flexibility rather than hard-coding a subjective interpretation.

## Important

The project's architecture, visual language, probability-to-geometry mapping rules, and final artistic direction are intentionally not defined here.

Those decisions belong to the project creator and should be documented separately as they evolve.