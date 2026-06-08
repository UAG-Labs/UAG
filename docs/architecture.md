# Architecture — UAG

## Identity
UAG is a graph-native architecture compiler platform. The architecture graph is the program. The compiler validates, transforms, and compiles it into real implementation targets.

## Boundary
This repo coordinates the full ecosystem through docs, specs, examples, research, and roadmap.

## Main Concepts
- TAKG is the editable source graph — the input to the compiler.
- UAGL is the compiled architecture IR — the input to all output targets.
- Code compilation targets (Rust, TypeScript, React, C) are first-class outputs, not afterthoughts.
- Examples prove the graph model can represent different architecture ranges.
- Specs are mandatory before implementation.

## Graph Primitives
The graph describes software through typed primitives: nodes, edges, events, capabilities, resources, constraints, and goals.

## Compilation vs Projection
- **Compilation targets** (Rust, TypeScript, C, React) — the compiler emits working code from the graph.
- **Projections** (diagrams, docs, API contracts, AI context) — views generated from the graph.

Both flow from UAGL. Neither is the source of truth. The distinction matters: code is compiled, not projected.

## Studio
The visual editor is the human trust and inspection layer. AI can read and modify the graph directly, but Studio is required for human understanding and approval before and after compilation.

## Event-Driven Compilation
The compiler is designed to support incremental, event-driven recompilation when the graph changes — through Studio edits or AI modifications — producing live updated outputs across all targets.

## Sibling Repo Map
- `UAG-core`: implements the canonical Rust graph model and validation primitives.
- `UAG-compiler`: validates TAKG, lowers to UAGL, compiles to code and other targets.
- `UAG-studio`: visual editor — the human trust and inspection layer.
