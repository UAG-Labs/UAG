# Spec: DATA-001 - TAKG Source Graph

**Spec ID:** DATA-001
**Type:** Data
**Status:** Draft
**Date:** 2026-06-08
**Author:** Agent

## 1. Overview
1.1 Purpose - Defines TAKG as the editable source graph format.
1.2 Context - Studio needs a file format that can store draft visual graph state without polluting compiled IR.
1.3 Related artifacts
   1.3.A ADR: [ADR-0001 Repository Purpose](../adr/ADR-0001-repository-purpose.md)
   1.3.B Research: [Research Summary](../research/initial-research.md)
   1.3.C Open questions: [Open Questions](../open-questions.md) - none unresolved in this initialized package.
   1.3.D Plan: [Bootstrap Plan](../plans/PLAN-001-bootstrap.md)

## 2. Scope
2.1 Goals
   2.1.A Define TAKG as editable source.
   2.1.B Support semantic graph objects, layout, editor metadata, and partial-invalid edit states.
   2.1.C Compile into deterministic UAGL with source maps and diagnostics.
   2.1.D Support rich example graphs for software, runtime, enterprise, AI-agent, data, and low-level systems.
2.2 Non-Goals (out of scope)
   2.2.A Does not require every editing state to be valid.
   2.2.B Does not replace UAGL.
   2.2.C Does not define binary storage.
   2.2.D Does not persist observed runtime telemetry directly inside editable design intent.

## 3. Requirements
3.1 Functional requirements
   3.1.A TAKG must support entities, relationships, boundaries, surfaces, operations, contracts, flows, views, layouts, and editor metadata.
   3.1.B TAKG must allow unresolved references during editing and preserve author intent until the compiler diagnoses it.
   3.1.C TAKG must compile deterministically when valid enough.
   3.1.D Relationships must declare `source`, `target`, `kind`, `direction`, `mode`, `protocol`, `cardinality`, `data`, `auth`, and `failure_behavior` when known.
   3.1.E Views must be semantic filters over graph objects; layout must be per-view and separate from the semantic filter.
   3.1.F Every semantic object should carry stable IDs, optional `tags`, optional `owner`, optional `lifecycle`, optional `classification`, and optional `provenance`.
   3.1.G Secret material is forbidden; secret references must point to external secret stores by reference only.
   3.1.H TAKG must support package imports and graph namespaces before multi-file projects become official.
3.2 Non-functional requirements
   3.2.A TAKG must initially be human-readable YAML.
   3.2.B TAKG must avoid literal secrets and support export redaction.
   3.2.C TAKG serialization must use canonical ordering so unchanged semantic input produces stable diffs.

## 4. Interface / Data
4.1 Type-specific detail
   4.1.A Root fields include `takg`, `imports`, `dialects`, `entities`, `relationships`, `boundaries`, `surfaces`, `operations`, `contracts`, `flows`, `views`, `layouts`, `editor_metadata`, and `policy`.
   4.1.B Semantic data and layout data are separate.
   4.1.C `takg` metadata includes `spec_version`, `package_id`, `name`, `namespace`, and optional `compatibility`.
   4.1.D `imports` entries include `package`, `version`, `namespace`, and optional `lock`.
   4.1.E `policy` includes `classification_defaults`, `redaction_rules`, and `secret_reference_schemes`.
   4.1.F `layouts` are keyed by view ID and object ID and may not define semantic graph membership.

## 5. Behavior
5.1 Happy path
   5.1.A Studio saves TAKG.
   5.1.B Compiler loads TAKG, resolves imports and dialects, and creates source maps.
   5.1.C Compiler emits UAGL.
5.2 Edge cases
   5.2.A Unresolved references produce diagnostics.
   5.2.B Deleted nodes leave dangling-reference diagnostics.
   5.2.C Unknown future fields are preserved where possible and diagnosed when they affect semantics.
   5.2.D Partial views render as incomplete projections with diagnostics, not crashes.
5.3 Error states
   5.3.A Secret-like values produce diagnostics.
   5.3.B Missing compile fields produce diagnostics instead of crash.
   5.3.C Duplicate canonical IDs fail validation.
   5.3.D Package namespace collisions fail validation unless explicitly aliased.

## 6. Acceptance Criteria
6.1 Criteria
   6.1.A [ ] TAKG schema supports graph and layout (verifies 3.1.A) - Verified by: [--]
   6.1.B [ ] Unresolved references are diagnosable (verifies 3.1.B) - Verified by: [--]
   6.1.C [ ] Deterministic compile is possible (verifies 3.1.C) - Verified by: [--]
   6.1.D [ ] Relationship contract fields validate (verifies 3.1.D) - Verified by: [--]
   6.1.E [ ] View filter and layout separation validate (verifies 3.1.E) - Verified by: [--]
   6.1.F [ ] Literal secret detection exists (verifies 3.1.G) - Verified by: [--]
   6.1.G [ ] Canonical example suite compiles with non-empty relationships and views (verifies 2.1.D) - Verified by: [--]

## 7. Open Questions & Assumptions
7.1 Open questions - No unresolved open questions are allowed in this initialized documentation package. Future uncertainty must be recorded in [Open Questions](../open-questions.md) before implementation continues.
7.2 Assumptions
   7.2.A YAML is initial source representation. - Validated: ../research/initial-research.md and ../adr/ADR-0001-repository-purpose.md.
   7.2.B TAKG remains the authoring truth even when runtime observations or generated artifacts are attached through UAGL.
