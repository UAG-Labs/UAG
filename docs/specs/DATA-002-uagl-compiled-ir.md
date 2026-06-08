# Spec: DATA-002 - UAGL Compiled IR

**Spec ID:** DATA-002
**Type:** Data
**Status:** Draft
**Date:** 2026-06-08
**Author:** Agent

## 1. Overview
1.1 Purpose - Defines UAGL as normalized compiled architecture IR.
1.2 Context - Exporters and validators need deterministic architecture truth separate from editor state.
1.3 Related artifacts
   1.3.A ADR: [ADR-0001 Repository Purpose](../adr/ADR-0001-repository-purpose.md)
   1.3.B Research: [Research Summary](../research/initial-research.md)
   1.3.C Open questions: [Open Questions](../open-questions.md) - none unresolved in this initialized package.
   1.3.D Plan: [Bootstrap Plan](../plans/PLAN-001-bootstrap.md)

## 2. Scope
2.1 Goals
   2.1.A Define UAGL as compiled IR.
   2.1.B Make UAGL exporter input.
   2.1.C Include validation/loss report support.
   2.1.D Preserve TAKG provenance through source maps.
   2.1.E Represent design intent separately from observed runtime state.
2.2 Non-Goals (out of scope)
   2.2.A Does not include editor selection state.
   2.2.B Does not become primary visual editing format.
   2.2.C Does not claim every export is lossless.
   2.2.D Does not store raw telemetry streams.

## 3. Requirements
3.1 Functional requirements
   3.1.A UAGL must contain resolved semantic objects.
   3.1.B UAGL output must be deterministic.
   3.1.C UAGL must separate design intent from observed runtime state.
   3.1.D UAGL must include source maps from TAKG objects, paths, and spans to compiled objects and diagnostics.
   3.1.E UAGL must include canonical package, dialect, schema, and compatibility metadata.
   3.1.F UAGL must model contracts as operations, messages, schemas, channels, servers, and protocol bindings.
   3.1.G UAGL must model runtime observations as separate objects linked to design entities by stable references.
   3.1.H UAGL must support dependency/provenance references for packages, services, artifacts, and generated outputs.
3.2 Non-functional requirements
   3.2.A UAGL must initially be human-readable YAML.
   3.2.B Unchanged source must compile to stable output.
   3.2.C UAGL must be suitable for machine validation, semantic diff, query, and export.

## 4. Interface / Data
4.1 Type-specific detail
   4.1.A Root fields include `uagl`, `ontology`, `packages`, `dialects`, `entities`, `relationships`, `boundaries`, `surfaces`, `operations`, `contracts`, `flows`, `views`, `runtime_observations`, `dependencies`, `artifacts`, `source_maps`, `validation`, and `policy`.
   4.1.B Every reference resolves or emits diagnostics.
   4.1.C `source_maps` entries include `source_package`, `source_file`, `source_path`, `source_span`, `compiled_object`, and `transform_stage`.
   4.1.D Runtime observations include `environment`, `observed_at`, `source`, `entity_ref`, `status`, `attributes`, and `confidence`.
   4.1.E Dependency/provenance references may map to external SBOM, deployment, telemetry, or repository artifacts without embedding their full contents.
   4.1.F Semantic diff uses stable object IDs, object kind, relationship endpoints, and normalized field paths.

## 5. Behavior
5.1 Happy path
   5.1.A Compiler receives TAKG.
   5.1.B Compiler resolves, validates, normalizes, and lowers to UAGL.
   5.1.C Exporter reads UAGL and emits an artifact plus a loss report.
5.2 Edge cases
   5.2.A Partial TAKG produces diagnostics.
   5.2.B Unsupported export target produces loss report.
   5.2.C Runtime observation without design entity becomes a drift diagnostic.
   5.2.D Unknown dependency metadata is preserved as external provenance when policy allows.
5.3 Error states
   5.3.A ID collision fails validation.
   5.3.B Lossy target reports omitted semantics.
   5.3.C Broken source map fails compiler tests.
   5.3.D Contract object without schema or message binding emits diagnostic.

## 6. Acceptance Criteria
6.1 Criteria
   6.1.A [ ] UAGL schema includes compiled fields (verifies 3.1.A) - Verified by: [--]
   6.1.B [ ] Repeated output is deterministic (verifies 3.1.B) - Verified by: [--]
   6.1.C [ ] Loss reports exist (verifies 3.1.C) - Verified by: [--]
   6.1.D [ ] Source maps connect TAKG to UAGL diagnostics (verifies 3.1.D) - Verified by: [--]
   6.1.E [ ] Runtime observations remain separate from design objects (verifies 3.1.G) - Verified by: [--]
   6.1.F [ ] Semantic diff fixture uses stable normalized paths (verifies 3.2.C) - Verified by: [--]

## 7. Open Questions & Assumptions
7.1 Open questions - No unresolved open questions are allowed in this initialized documentation package. Future uncertainty must be recorded in [Open Questions](../open-questions.md) before implementation continues.
7.2 Assumptions
   7.2.A YAML is initial compiled representation. - Validated: ../research/initial-research.md and ../adr/ADR-0001-repository-purpose.md.
   7.2.B UAGL is allowed to include external artifact references, but not become a telemetry database or package registry.
