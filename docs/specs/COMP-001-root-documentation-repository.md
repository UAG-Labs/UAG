# Spec: COMP-001 — Root Documentation Repository

**Spec ID:** COMP-001
**Type:** Component
**Status:** Draft
**Date:** 2026-06-08
**Author:** Agent

## 1. Overview
1.1 Purpose — Specifies UAG as root documentation and coordination component.
1.2 Context — The ecosystem needs one place where all specs, examples, and repo boundaries are defined.
1.3 Related artifacts
   1.3.A ADR: [ADR-0001 Repository Purpose](../adr/ADR-0001-repository-purpose.md)
   1.3.B Research: [Research Summary](../research/initial-research.md)
   1.3.C Open questions: [Open Questions](../open-questions.md) — none unresolved in this initialized package.
   1.3.D Plan: [Bootstrap Plan](../plans/PLAN-001-bootstrap.md)

## 2. Scope
2.1 Goals
   2.1.A Centralize specs and examples.
   2.1.B Keep implementation out.
   2.1.C Provide Codex context.
2.2 Non-Goals (out of scope)
   2.2.A Does not implement compiler.
   2.2.B Does not implement Rust core.
   2.2.C Does not implement Studio.

## 3. Requirements
3.1 Functional requirements
   3.1.A Repo must include README, architecture, roadmap, research, open-questions, specs, examples, and plan.
   3.1.B Repo must maintain specs index.
   3.1.C Repo must define boundaries.
3.2 Non-functional requirements
   3.2.A Docs must contain no unresolved placeholders.
   3.2.B Examples must reveal model weaknesses.

## 4. Interface / Data
4.1 Type-specific detail
   4.1.A Inputs are design decisions and research.
   4.1.B Outputs are specs, examples, and coordination docs.

## 5. Behavior
5.1 Happy path
   5.1.A Agent reads root docs.
   5.1.B Agent locates spec.
   5.1.C Agent implements in sibling repo.
5.2 Edge cases
   5.2.A Spec changes require affected plans to be revisited.
   5.2.B New repo responsibility requires ADR.
5.3 Error states
   5.3.A Conflicting implementation defers to specs.
   5.3.B Broken examples become tracked issues.

## 6. Acceptance Criteria
6.1 Criteria
   6.1.A [ ] Root docs exist (verifies §3.1.A) — Verified by: [—]
   6.1.B [ ] Specs index exists (verifies §3.1.B) — Verified by: [—]
   6.1.C [ ] Examples exist (verifies §3.1.C) — Verified by: [—]

## 7. Open Questions & Assumptions
7.1 Open questions — No unresolved open questions are allowed in this initialized documentation package. Future uncertainty must be recorded in [Open Questions](../open-questions.md) before implementation continues.
7.2 Assumptions
   7.2.A Root docs control first implementation. — Validated: ../research/initial-research.md and ../adr/ADR-0001-repository-purpose.md.
