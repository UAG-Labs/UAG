# Spec: DATA-001 — TAKG Source Graph

**Spec ID:** DATA-001
**Type:** Data
**Status:** Draft
**Date:** 2026-06-08
**Author:** Agent

## 1. Overview
1.1 Purpose — Defines TAKG as the editable source graph format.
1.2 Context — Studio needs a file format that can store draft visual graph state without polluting compiled IR.
1.3 Related artifacts
   1.3.A ADR: [ADR-0001 Repository Purpose](../adr/ADR-0001-repository-purpose.md)
   1.3.B Research: [Research Summary](../research/initial-research.md)
   1.3.C Open questions: [Open Questions](../open-questions.md) — none unresolved in this initialized package.
   1.3.D Plan: [Bootstrap Plan](../plans/PLAN-001-bootstrap.md)

## 2. Scope
2.1 Goals
   2.1.A Define TAKG as editable.
   2.1.B Support layout and editor metadata.
   2.1.C Compile into UAGL.
2.2 Non-Goals (out of scope)
   2.2.A Does not require every editing state to be valid.
   2.2.B Does not replace UAGL.
   2.2.C Does not define binary storage.

## 3. Requirements
3.1 Functional requirements
   3.1.A TAKG must support entities, relationships, boundaries, views, layouts, and editor metadata.
   3.1.B TAKG must allow unresolved references during editing.
   3.1.C TAKG must compile deterministically when valid enough.
3.2 Non-functional requirements
   3.2.A TAKG must initially be human-readable YAML.
   3.2.B TAKG must avoid literal secrets.

## 4. Interface / Data
4.1 Type-specific detail
   4.1.A Root fields include `takg`, `entities`, `relationships`, `boundaries`, `views`, `layouts`, `editor_metadata`.
   4.1.B Semantic data and layout data are separate.

## 5. Behavior
5.1 Happy path
   5.1.A Studio saves TAKG.
   5.1.B Compiler loads TAKG.
   5.1.C Compiler emits UAGL.
5.2 Edge cases
   5.2.A Unresolved references produce diagnostics.
   5.2.B Deleted nodes leave dangling-reference diagnostics.
5.3 Error states
   5.3.A Secret-like values produce diagnostics.
   5.3.B Missing compile fields produce diagnostics instead of crash.

## 6. Acceptance Criteria
6.1 Criteria
   6.1.A [ ] TAKG schema supports graph and layout (verifies §3.1.A) — Verified by: [—]
   6.1.B [ ] Unresolved references are diagnosable (verifies §3.1.B) — Verified by: [—]
   6.1.C [ ] Deterministic compile is possible (verifies §3.1.C) — Verified by: [—]

## 7. Open Questions & Assumptions
7.1 Open questions — No unresolved open questions are allowed in this initialized documentation package. Future uncertainty must be recorded in [Open Questions](../open-questions.md) before implementation continues.
7.2 Assumptions
   7.2.A YAML is initial source representation. — Validated: ../research/initial-research.md and ../adr/ADR-0001-repository-purpose.md.
