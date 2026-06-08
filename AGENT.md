# AGENT.md — Codex Context for `UAG`

## Repository Identity
Repository: `UAG`  
Organization: `UAG-Labs`  
GitHub description: Universal Architecture Graph: specs, docs, examples, research, and roadmap for a graph-native software architecture modeling system.

## Non-Negotiable Rule
The graph is the source of truth. The diagram is a view. The export is a projection.

## Role
Root knowledge repository for official purpose, specs, examples, research, roadmap, and cross-repo coordination.

## Technology
Markdown, YAML, and example artifacts. No Rust/React implementation belongs here.

## Dependency Boundary
Does not depend on sibling repos. It documents them.

## Expected Output
Complete source-of-truth documentation and example TAKG/UAGL systems.

## Working Instructions
1. Read `README.md`, `docs/architecture.md`, `docs/artifact.md`, `docs/REPOSITORY_STRUCTURE.md`, and `docs/specs/README.md` before implementation.
2. Add or update specs using `docs/procedures/add-specification-file.md`.
3. Do not implement undocumented behavior.
4. Do not create unresolved implementation questions. Record blockers in `docs/open-questions.md` and stop.
5. Preserve TAKG as editable source graph and UAGL as compiled IR.
6. Keep generated output deterministic wherever possible.
7. Keep repo responsibilities inside this repo's boundary.
