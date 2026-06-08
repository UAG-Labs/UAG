# Plan: PLAN-102 - Canonical Fixture Suite

**Status:** Draft
**Handoff Target:** cheaper/faster planning or implementation model
**Repo Scope:** `UAG`

## Goal
Build the complete canonical fixture suite used by core, compiler, Studio, exporters, and release gates.

## Required Fixture Families
1. Minimal smoke graph.
2. CRUD SaaS graph.
3. AI-agent/MCP graph.
4. Trading/event-driven graph.
5. Enterprise/capability graph.
6. Low-level driver/hardware graph.
7. Data pipeline/analytics graph.
8. Kubernetes/runtime/deployment graph.
9. Security/trust-boundary/redaction graph.
10. Package/import/multi-namespace graph.
11. Invalid graph set for diagnostics.
12. Lossy-export graph set.

## Tasks
1. Ensure each fixture has TAKG source and expected UAGL output shape.
2. Ensure each fixture has non-empty entities, relationships, views, and relevant policies.
3. Add fixture README files that explain why the fixture exists and what it must prove.
4. Keep expected outputs high-level until `UAG-core` schemas and `UAG-compiler` canonical output stabilize.
5. Add a fixture inventory table to the docs index when the suite is complete.

## Success Criteria
1. Every major graph feature appears in at least one fixture.
2. Every fixture has a stated validation purpose.
3. Sibling repos can use fixtures as tests without inventing their own hidden examples.
