<p align="center">
  <img src="./assets/logos/uag-labs-readme-banner.svg" alt="UAG banner" />
</p>

# UAG

Universal Architecture Graph: specs, docs, examples, research, and roadmap for a graph-native software architecture modeling system.

## Mission
UAG-Labs exists to make architecture graph-native, typed, validatable, compilable, searchable, diffable, and useful to humans and AI systems.

## Core Principle
```text
The graph is the source of truth.
The diagram is a view.
The export is a projection.
```

## What This Repo Is
`UAG` is the root documentation and specification repository for the UAG-Labs organization.

It owns:
- organization-level purpose,
- TAKG and UAGL specs,
- examples,
- research summaries,
- roadmap,
- cross-repo context.

It does not own:
- Rust core implementation,
- compiler implementation,
- CLI implementation,
- Studio UI implementation.

## Four Repositories
- `UAG` — specs, docs, examples, research, and roadmap.
- `UAG-core` — shared Rust graph/language model, schemas, ontology, dialects, and validation primitives.
- `UAG-compiler` — Rust compiler and CLI for transforming TAKG to UAGL and generated outputs.
- `UAG-studio` — React and Rust visual architecture graph editor.

## TAKG
Typed Architecture Knowledge Graph. The editable source graph used by Studio.

## UAGL
Universal Architecture Graph Language. The normalized compiled architecture IR emitted by the compiler.

## End-to-End Workflow
```text
Studio edits TAKG
→ Compiler resolves/validates/lowers
→ Compiler emits UAGL
→ Exporters emit diagrams, docs, API specs, deployment stubs, and AI context
```

## Current State
Brand-new documentation initialization. This repo should be committed before implementation begins in sibling repos.
