# Plan: PLAN-003 - Language Contract Readiness

**Status:** Draft
**Derived From:** ../specs/DATA-001-takg-source-graph.md and ../specs/DATA-002-uagl-compiled-ir.md
**Derivation Status:** Current

## Objective
Define what the TAKG/UAGL contract must provide before the implementation repos treat it as stable enough to build against.

## Scope
This plan is about readiness of the architecture graph contract. It does not implement core structs, compiler stages, exporters, or Studio UI.

## Required Contract Areas
1. Root metadata: `spec_version`, `package_id`, `namespace`, `name`, dialects, compatibility.
2. Object model: entities, relationships, boundaries, surfaces, operations, contracts, flows, views, layouts, policies.
3. Relationship semantics: endpoint refs, direction, mode, protocol, cardinality, data, auth, failure behavior.
4. View semantics: filter-based membership separate from layout coordinates.
5. Security policy: classification defaults, redaction rules, allowed secret-reference schemes.
6. Source maps: source package, source file, object path, span, compiled object, transform stage.
7. Runtime observations: environment, source, entity ref, status, attributes, confidence.
8. Provenance/dependencies: external references for SBOM, deployments, generated artifacts, and source repos.
9. Determinism: canonical ordering and stable IDs.
10. Loss reporting: preserved, omitted, degraded, fidelity, and remediation.

## Readiness Checklist
1. [ ] Canonical examples cover each required contract area.
2. [ ] Each root field in TAKG and UAGL has an owning repo for implementation.
3. [ ] `UAG-core` plan names the structs and schemas for each contract area.
4. [ ] `UAG-compiler` plan names validation/lowering behavior for each contract area.
5. [ ] `UAG-studio` plan names editing/display behavior for each contract area.
6. [ ] Compatibility matrix template exists before the first tagged release.

## Fixture Expectations
1. AI-agent fixture must exercise tool invocation, policy, trust boundary, and AI-context redaction risk.
2. Trading fixture must exercise async relationships, event streams, external systems, and failure behavior.
3. Enterprise fixture must exercise capability mapping, identity, data boundary, and governance relationships.
4. Low-level fixture must exercise hardware, memory, privilege boundaries, DMA, and protocol-specific relationships.

## Exit Criteria
This plan is ready when all implementation repos can link to specific TAKG/UAGL contract sections instead of relying on conversation context.
