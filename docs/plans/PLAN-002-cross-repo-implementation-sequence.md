# Plan: PLAN-002 - Cross-Repo Implementation Sequence

**Status:** Draft
**Derived From:** ../specs/SYS-001-uag-labs-ecosystem.md
**Derivation Status:** Current

## Objective
Define the order in which the four repositories should begin implementation so the architecture graph contract becomes executable before UI or exporter work depends on unstable semantics.

## Planning Role
`UAG` is the coordination repo. It should not implement the Rust model, compiler, CLI, or Studio UI. It does need implementation plans for sequencing, compatibility gates, canonical examples, and readiness criteria.

## Dependency Order
1. `UAG` maintains canonical examples and language intent.
2. `UAG-core` implements typed model, serialization, schemas, dialect loading, and validation primitives.
3. `UAG-compiler` consumes `UAG-core`, compiles canonical examples, emits UAGL, diagnostics, source maps, and loss reports.
4. `UAG-studio` consumes compiler/core outputs through adapters and becomes the authoring surface after schemas and compile results are stable.

## Readiness Gates
1. Gate A - Root examples: canonical TAKG/UAGL fixtures exist for AI-agent, trading/event, enterprise, and low-level systems.
2. Gate B - Core schema: `UAG-core` generates TAKG, UAGL, dialect, diagnostic, loss-report, and package schemas.
3. Gate C - Compiler fixture compile: `UAG-compiler` compiles the canonical examples with deterministic output and source maps.
4. Gate D - Export honesty: each exporter declares target capability and emits loss reports.
5. Gate E - Studio adapter: `UAG-studio` can open/save TAKG, call compiler, display diagnostics, and keep canvas state separate from semantics.
6. Gate F - Compatibility matrix: release notes identify compatible TAKG, UAGL, core, compiler, and Studio versions.

## Milestone Sequence
| Milestone | Owning Repo | Depends On | Exit Criteria |
|---|---|---|---|
| M0 Documentation baseline | All | None | Open questions resolved or logged; ADR-0002 present where decisions exist. |
| M1 Contract fixtures | UAG | M0 | Canonical examples parse and exercise relationships/views/source maps. |
| M2 Executable model | UAG-core | M1 | Rust structs, schemas, canonical serialization, validation primitives pass fixtures. |
| M3 Compiler vertical slice | UAG-compiler | M2 | TAKG to UAGL compile works for canonical examples with diagnostics/source maps. |
| M4 Export vertical slice | UAG-compiler | M3 | Mermaid, D2, Markdown, and AI context exporters emit artifacts and loss reports. |
| M5 Studio authoring slice | UAG-studio | M3 | Open/save/edit/compile/diagnostic loop works on a canonical example. |
| M6 Compatibility release | All | M2-M5 | Compatibility matrix and cross-repo smoke tests pass. |

## Implementation Planning Rules
1. Implementation plans must reference the spec acceptance criteria they satisfy.
2. No plan may mark criteria verified without test, fixture, or command evidence.
3. Any new unresolved design question must be added to `../open-questions.md` before implementation continues.
4. Plans that depend on sibling repos must name the exact contract they need from the sibling repo.
5. Each repo should own local implementation steps; `UAG` should own sequence and gate tracking only.

## First Planning Actions
1. Keep `UAG` examples and language specs stable enough for `UAG-core` planning.
2. Start `UAG-core` implementation planning with model/schema first, not compiler behavior.
3. Start `UAG-compiler` planning only after naming its expected `UAG-core` contracts.
4. Start `UAG-studio` planning around adapters and compile-result display, not final UI polish.
