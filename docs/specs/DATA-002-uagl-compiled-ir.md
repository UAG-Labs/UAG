# Spec: DATA-002 — UAGL Compiled IR

**Spec ID:** DATA-002
**Type:** Data
**Status:** Draft
**Date:** 2026-06-08
**Author:** Agent

## 1. Overview
1.1 Purpose — Defines UAGL as normalized compiled architecture IR.
1.2 Context — Exporters and validators need deterministic architecture truth separate from editor state.
1.3 Related artifacts
   1.3.A ADR: [ADR-0001 Repository Purpose](../adr/ADR-0001-repository-purpose.md)
   1.3.B Research: [Research Summary](../research/initial-research.md)
   1.3.C Open questions: [Open Questions](../open-questions.md) — none unresolved in this initialized package.
   1.3.D Plan: [Bootstrap Plan](../plans/PLAN-001-bootstrap.md)

## 2. Scope
2.1 Goals
   2.1.A Define UAGL as compiled IR.
   2.1.B Make UAGL exporter input.
   2.1.C Include validation/loss report support.
2.2 Non-Goals (out of scope)
   2.2.A Does not include editor selection state.
   2.2.B Does not become primary visual editing format.
   2.2.C Does not claim every export is lossless.

## 3. Requirements
3.1 Functional requirements
   3.1.A UAGL must contain resolved semantic objects.
   3.1.B UAGL output must be deterministic.
   3.1.C UAGL must separate design intent from observed runtime state.
3.2 Non-functional requirements
   3.2.A UAGL must initially be human-readable YAML.
   3.2.B Unchanged source must compile to stable output.

## 4. Interface / Data
4.1 Type-specific detail
   4.1.A Root fields include `uagl`, `ontology`, `entities`, `relationships`, `boundaries`, `surfaces`, `operations`, `contracts`, `flows`, `views`, `validation`.
   4.1.B Every reference resolves or emits diagnostics.

## 5. Behavior
5.1 Happy path
   5.1.A Compiler receives TAKG.
   5.1.B Compiler lowers to UAGL.
   5.1.C Exporter reads UAGL.
5.2 Edge cases
   5.2.A Partial TAKG produces diagnostics.
   5.2.B Unsupported export target produces loss report.
5.3 Error states
   5.3.A ID collision fails validation.
   5.3.B Lossy target reports omitted semantics.

## 6. Acceptance Criteria
6.1 Criteria
   6.1.A [ ] UAGL schema includes compiled fields (verifies §3.1.A) — Verified by: [—]
   6.1.B [ ] Repeated output is deterministic (verifies §3.1.B) — Verified by: [—]
   6.1.C [ ] Loss reports exist (verifies §3.1.C) — Verified by: [—]

## 7. Open Questions & Assumptions
7.1 Open questions — No unresolved open questions are allowed in this initialized documentation package. Future uncertainty must be recorded in [Open Questions](../open-questions.md) before implementation continues.
7.2 Assumptions
   7.2.A YAML is initial compiled representation. — Validated: ../research/initial-research.md and ../adr/ADR-0001-repository-purpose.md.
