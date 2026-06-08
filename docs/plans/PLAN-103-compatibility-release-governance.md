# Plan: PLAN-103 - Compatibility and Release Governance

**Status:** Draft
**Handoff Target:** cheaper/faster planning or implementation model
**Repo Scope:** `UAG`

## Goal
Define how the ecosystem versions, releases, and verifies compatibility.

## Tasks
1. Define language versioning for TAKG and UAGL.
2. Define schema versioning and compatibility expectations.
3. Define a compatibility matrix template for core, compiler, Studio, fixtures, schemas, and exporters.
4. Define what counts as breaking, additive, deprecated, experimental, and removed.
5. Define release gate evidence required from each sibling repo.

## Success Criteria
1. A release cannot be called compatible without a filled matrix.
2. Breaking language changes require an ADR and migration note.
3. Every sibling repo knows what evidence it must provide before a coordinated release.
