# Plan: PLAN-101 - Language Contract Finalization

**Status:** Draft
**Handoff Target:** cheaper/faster planning or implementation model
**Repo Scope:** `UAG`

## Goal
Finalize the TAKG and UAGL specs as stable language contracts.

## Inputs
- ../specs/DATA-001-takg-source-graph.md
- ../specs/DATA-002-uagl-compiled-ir.md
- ../specs/SYS-001-uag-labs-ecosystem.md
- ../open-questions.md

## Tasks
1. Review every root field in TAKG and UAGL and make sure it has purpose, ownership, validation expectation, and lifecycle.
2. Define required versus optional sections for authoring, compiling, exporting, and runtime attachment.
3. Add explicit compatibility rules for language version changes.
4. Ensure source maps, relationships, views, policies, runtime observations, packages/imports, and loss reports are specified without implementation ambiguity.
5. Confirm every open question is either resolved, converted into an ADR, or left clearly blocking.

## Success Criteria
1. Specs can be handed to `UAG-core` for schema generation without hidden assumptions.
2. Specs can be handed to `UAG-compiler` for semantic validation and lowering behavior.
3. Specs can be handed to `UAG-studio` for editing behavior and read-only UAGL behavior.
4. No unresolved language-shape question is hidden in prose.
