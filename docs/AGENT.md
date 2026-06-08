# AGENT.md — Codex Context for `UAG`

## Repository Identity
Repository: `UAG`  
Organization: `UAG-Labs`  
GitHub description: Universal Architecture Graph — specs, docs, examples, research, and roadmap for a graph-native architecture compiler platform.

## Non-Negotiable Rules
- The architecture graph is the source of truth.
- The diagram is a view.
- The export is a projection.
- The code is a compilation target.
- UAG is not a diagramming tool. It is a graph-native architecture compiler platform.
- Software architecture becomes source code. The graph is the program.

## Role
Root knowledge repository for official purpose, specs, examples, research, roadmap, and cross-repo coordination.

## Technology
Markdown, YAML, and example artifacts. No Rust/React implementation belongs here.

## Dependency Boundary
Does not depend on sibling repos. It documents them.

## Expected Output
Complete source-of-truth documentation and example TAKG/UAGL systems covering:
- all graph primitive types: nodes, edges, events, capabilities, resources, constraints, goals
- all behavior layers: state machines, predicates, effects, transformations, holes
- compilation targets: Rust, TypeScript, React, C — not only diagram and doc projections
- platform adapter model and policy engine concepts

## Working Instructions
1. Read `README.md`, `docs/architecture.md`, `docs/artifact.md`, `docs/REPOSITORY_STRUCTURE.md`, and `docs/specs/README.md` before implementation.
2. Add or update specs using `docs/procedures/add-specification-file.md`.
3. Do not implement undocumented behavior.
4. Do not create unresolved implementation questions. Record blockers in `docs/open-questions.md` and stop.
5. Preserve TAKG as editable source graph and UAGL as compiled IR.
6. Treat code compilation targets (Rust, TypeScript, React, C) as first-class compiler outputs, equal in importance to diagram and doc projections.
7. Keep generated output deterministic wherever possible.
8. Keep repo responsibilities inside this repo's boundary.
