# Spec: SYS-001 - UAG-Labs Ecosystem

**Spec ID:** SYS-001
**Type:** System-overview
**Status:** Draft
**Date:** 2026-06-08
**Author:** Agent

## 1. Overview
1.1 Purpose - Defines the organization-level system made of four repositories.
1.2 Context - UAG-Labs is brand new and needs a closed map before implementation begins.
1.3 Related artifacts
   1.3.A ADR: [ADR-0001 Repository Purpose](../adr/ADR-0001-repository-purpose.md)
   1.3.B Research: [Research Summary](../research/initial-research.md)
   1.3.C Open questions: [Open Questions](../open-questions.md) - none unresolved in this initialized package.
   1.3.D Plan: [Bootstrap Plan](../plans/PLAN-001-bootstrap.md)

## 2. Scope
2.1 Goals
   2.1.A Define all repo purposes.
   2.1.B Define dependency direction.
   2.1.C Define TAKG/UAGL workflow.
   2.1.D Define cross-repo readiness gates for schemas, examples, source maps, diagnostics, and loss reports.
2.2 Non-Goals (out of scope)
   2.2.A Does not define Rust structs line-by-line.
   2.2.B Does not implement Studio UI.
   2.2.C Does not define every exporter syntax.

## 3. Requirements
3.1 Functional requirements
   3.1.A The ecosystem must keep UAG-core independent from compiler and Studio.
   3.1.B The ecosystem must treat TAKG as source and UAGL as compiled IR.
   3.1.C The ecosystem must keep canonical examples in UAG.
   3.1.D The ecosystem must require executable schemas before Studio becomes the primary authoring interface.
   3.1.E Cross-repo releases must publish a compatibility matrix covering TAKG schema version, UAGL schema version, core crate version, compiler version, and Studio version.
   3.1.F Runtime observations, dependency provenance, generated artifacts, and external inventory data must attach by reference and must not overwrite TAKG design intent.
3.2 Non-functional requirements
   3.2.A Docs must stand alone without prior conversation.
   3.2.B Repo boundaries must prevent circular dependencies.
   3.2.C Canonical examples must stay useful as validation fixtures, not just marketing samples.

## 4. Interface / Data
4.1 Type-specific detail
   4.1.A The ecosystem contains UAG, UAG-core, UAG-compiler, and UAG-studio.
   4.1.B Workflow is Studio edits TAKG, compiler emits UAGL, exporters emit projections.
   4.1.C `UAG` owns language intent, canonical examples, cross-repo sequencing, and compatibility policy.
   4.1.D `UAG-core` owns executable model types, generated schemas, dialect loading, validation primitives, and canonical serialization.
   4.1.E `UAG-compiler` owns semantic validation, source maps, normalization, lowering, query/diff/package behavior, exporters, diagnostics, and loss reports.
   4.1.F `UAG-studio` owns TAKG authoring UX, layout/editor state, compiler interaction, diagnostics display, and export UI.

## 5. Behavior
5.1 Happy path
   5.1.A Agent reads this spec.
   5.1.B Agent maps each repo to its role.
   5.1.C Agent implements only within that boundary.
5.2 Edge cases
   5.2.A Future repo changes require ADR.
   5.2.B Future specs cite root context.
   5.2.C Any new dialect, exporter, or graph plane must declare validation and loss behavior.
5.3 Error states
   5.3.A Boundary conflict stops implementation.
   5.3.B Missing repo purpose blocks implementation.
   5.3.C Cross-repo version mismatch blocks release until compatibility is documented.

## 6. Acceptance Criteria
6.1 Criteria
   6.1.A [ ] All four repos are documented (verifies 3.1.A) - Verified by: [--]
   6.1.B [ ] TAKG/UAGL workflow is documented (verifies 3.1.B) - Verified by: [--]
   6.1.C [ ] Examples live under UAG and are non-empty fixtures (verifies 3.1.C) - Verified by: [--]
   6.1.D [ ] Compatibility matrix exists before first coordinated release (verifies 3.1.E) - Verified by: [--]
   6.1.E [ ] Runtime/provenance/artifact attachment is documented by reference (verifies 3.1.F) - Verified by: [--]

## 7. Open Questions & Assumptions
7.1 Open questions - No unresolved open questions are allowed in this initialized documentation package. Future uncertainty must be recorded in [Open Questions](../open-questions.md) before implementation continues.
7.2 Assumptions
   7.2.A The four-repo split is stable for first implementation. - Validated: ../research/initial-research.md and ../adr/ADR-0001-repository-purpose.md.
