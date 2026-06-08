# Open Questions - `UAG`

## Status
All initial audit questions have been answered for planning purposes. Future uncertainty should be added as new open questions.

## Research Basis
- Structurizr separates architecture `model` from `views`, supports workspace extension/includes, and treats generated view keys/layout stability as a design concern: https://docs.structurizr.com/dsl/language
- Structurizr stores a source DSL and a compiled JSON workspace, with layout in the compiled representation rather than the hand-authored source: https://docs.structurizr.com/workspaces/file-types
- D2 is a declarative text-to-diagram language and useful comparison point for export ergonomics: https://d2lang.com/tour/intro
- OpenAPI descriptions are machine-readable API descriptions rooted at an OpenAPI Object: https://learn.openapis.org/specification/structure.html
- AsyncAPI models channels, messages, operations, protocol bindings, and event-driven APIs: https://www.asyncapi.com/docs/reference/specification/v3.0.0

## Question Format
```markdown
## Q-001 - Title
Status: Open | Resolved
Raised by:
Question:
Why it matters:
Options:
Impacts:
Decision needed before:
Resolution evidence:
```

## Q-001 - What is the authoritative cross-repo contract for TAKG and UAGL?
Status: Resolved
Raised by: Audit of `DATA-001-takg-source-graph.md`, `DATA-002-uagl-compiled-ir.md`, `UAG-core`, `UAG-compiler`, and `UAG-studio`.
Question: Should the source-of-truth language contract live only in `UAG`, or should `UAG-core` generated schemas become the canonical contract after implementation begins?
Why it matters: Studio, compiler, examples, and docs can drift if prose specs and generated schemas are both treated as authoritative.
Options:
- `UAG` specs are normative; `UAG-core` schemas are generated conformance artifacts.
- `UAG-core` schemas are normative; `UAG` specs explain intent and examples.
- A versioned contract bundle is published from `UAG-core` and referenced by all repos.
AI recommendation: Use `UAG` specs as the normative intent contract until `UAG-core` can generate versioned schemas; after that, publish a contract bundle from `UAG-core` and reference it from `UAG` as the executable form of the prose specs.
Decision: Use `UAG` specs as the normative intent contract until `UAG-core` can generate versioned schemas; after that, publish a contract bundle from `UAG-core` and reference it from `UAG` as the executable form of the prose specs.
Impacts: Release process, schema versioning, examples, compiler compatibility, Studio file open/save.
Decision needed before: Implementation plan for first TAKG/UAGL structs.
Resolution evidence: [ADR-0002 Implementation Readiness Decisions](./adr/ADR-0002-implementation-readiness-decisions.md)

## Q-002 - What versioning policy governs the four repositories?
Status: Resolved
Raised by: Cross-repo audit.
Question: Will `UAG`, `UAG-core`, `UAG-compiler`, and `UAG-studio` share one ecosystem version, or will each repo version independently with compatibility ranges?
Why it matters: Studio must know which compiler/core/schema versions it can use; examples must declare which language version they target.
Options:
- Lockstep ecosystem version, such as `0.1.0` across all repos.
- Independent semver with compatibility matrices.
- Language schemas version independently from implementation crates/apps.
AI recommendation: Version language schemas independently, and version each implementation repo with semver plus an explicit compatibility matrix. Avoid lockstep releases unless a breaking language change requires coordinated publishing.
Decision: Version language schemas independently, and version each implementation repo with semver plus an explicit compatibility matrix. Avoid lockstep releases unless a breaking language change requires coordinated publishing.
Impacts: Release planning, CI, package names, docs, generated schemas, user support.
Decision needed before: First release plan.
Resolution evidence: [ADR-0002 Implementation Readiness Decisions](./adr/ADR-0002-implementation-readiness-decisions.md)

## Q-003 - What are the first official architecture dialects?
Status: Resolved
Raised by: Audit of examples and `UAG-core` dialect model.
Question: Which dialects are first-class for the first implementation: core-only, AI-agent/MCP, enterprise/domain, low-level systems, data systems, cloud infrastructure, or another minimal set?
Why it matters: Dialects determine object kinds, validation rules, examples, and export semantics.
Options:
- Ship only `core` dialect first.
- Ship `core` plus the four example-driven dialects.
- Define a formal dialect registry but implement only placeholders initially.
AI recommendation: Ship `core` first, with AI-agent/MCP, enterprise/domain, low-level systems, and data-systems represented as draft dialect fixtures rather than fully enforced dialects in milestone one.
Decision: Ship `core` first, with AI-agent/MCP, enterprise/domain, low-level systems, and data-systems represented as draft dialect fixtures rather than fully enforced dialects in milestone one.
Impacts: `UAG-core` ontology, compiler validation, example coverage, Studio node palette.
Decision needed before: Core object model implementation.
Resolution evidence: [ADR-0002 Implementation Readiness Decisions](./adr/ADR-0002-implementation-readiness-decisions.md)

## Q-004 - What is the first supported view model?
Status: Resolved
Raised by: Structurizr model/view research and Studio canvas specs.
Question: How should UAG represent views: named filters over the semantic graph, persisted diagram layouts, generated projections, or all three as separate concepts?
Why it matters: Views are where Studio layout, generated diagrams, and source graph semantics can become tangled.
Options:
- Views are semantic filters; layouts are separate per-view editor artifacts.
- Views include layout directly in TAKG but never UAGL.
- Views compile into UAGL as resolved projection definitions without pixel layout.
AI recommendation: Represent views as semantic filters over the graph, keep layout as separate per-view TAKG/editor metadata, and compile only resolved projection definitions into UAGL.
Decision: Represent views as semantic filters over the graph, keep layout as separate per-view TAKG/editor metadata, and compile only resolved projection definitions into UAGL.
Impacts: TAKG schema, UAGL schema, Studio state, exporter targets, deterministic output.
Decision needed before: TAKG view/layout schema implementation.
Resolution evidence: [ADR-0002 Implementation Readiness Decisions](./adr/ADR-0002-implementation-readiness-decisions.md)

## Q-005 - What external export targets are in the first milestone?
Status: Resolved
Raised by: Export research into D2, Mermaid, OpenAPI, AsyncAPI, and deployment stubs.
Question: Which export targets must be implemented first, and which are explicitly deferred?
Why it matters: Export targets drive which semantics must be preserved, which loss reports are needed, and which examples are useful.
Options:
- Diagrams first: Mermaid and D2 only.
- Contracts first: OpenAPI and AsyncAPI first.
- Mixed first milestone: Mermaid, Markdown summary, OpenAPI, AsyncAPI, and AI context.
AI recommendation: Start with Mermaid, D2, Markdown summaries, and AI context as the first exporter set; define OpenAPI and AsyncAPI contracts now but implement them after the core graph contract stabilizes.
Decision: Start with Mermaid, D2, Markdown summaries, and AI context as the first exporter set; define OpenAPI and AsyncAPI contracts now but implement them after the core graph contract stabilizes.
Impacts: Compiler exporter architecture, loss report shape, acceptance criteria, examples.
Decision needed before: Compiler implementation plan.
Resolution evidence: [ADR-0002 Implementation Readiness Decisions](./adr/ADR-0002-implementation-readiness-decisions.md)

## Q-006 - What is the minimum example suite that proves the model?
Status: Resolved
Raised by: Audit of existing examples.
Question: Which example systems must exist and remain valid in CI to prove TAKG/UAGL coverage across high-level, low-level, data, and AI-agent architectures?
Why it matters: Examples are the practical regression suite for the language.
Options:
- Keep the current four examples as canonical.
- Add a smaller smoke-test example for CI plus larger examples for docs.
- Add one example per official dialect.
AI recommendation: Keep the current four examples as canonical long-form examples, and add one small smoke-test example that CI can compile quickly on every repo change.
Decision: Keep the current four examples as canonical long-form examples, and add one small smoke-test example that CI can compile quickly on every repo change.
Impacts: `UAG` examples, compiler fixtures, Studio demo data, CI runtime.
Decision needed before: First CI plan.
Resolution evidence: [ADR-0002 Implementation Readiness Decisions](./adr/ADR-0002-implementation-readiness-decisions.md)

## Q-007 - What does "loss report" mean across the ecosystem?
Status: Resolved
Raised by: Audit of UAGL and compiler exporter specs.
Question: Is a loss report only an exporter artifact, or is it a general trace of semantics lost during normalization, compilation, import, and export?
Why it matters: Loss reports are central to the mission statement but under-specified.
Options:
- Exporter-only loss reports.
- Pipeline-wide loss reports from TAKG import through final export.
- Separate diagnostic, warning, and loss-report channels.
AI recommendation: Make loss reporting pipeline-wide, but require every exporter to produce an exporter-specific loss section. This keeps compile/import/export honesty under one shared model.
Decision: Make loss reporting pipeline-wide, but require every exporter to produce an exporter-specific loss section. This keeps compile/import/export honesty under one shared model.
Impacts: UAGL schema, compiler pipeline, Studio UI panels, acceptance tests.
Decision needed before: Diagnostic/loss report data implementation.
Resolution evidence: [ADR-0002 Implementation Readiness Decisions](./adr/ADR-0002-implementation-readiness-decisions.md)

## Q-008 - What is the security boundary for architecture data?
Status: Resolved
Raised by: TAKG requirement to avoid literal secrets and AI context export goal.
Question: What information is forbidden in TAKG/UAGL, and how should the compiler detect, redact, or report sensitive values?
Why it matters: Architecture graphs may contain endpoints, credentials, internal topology, trust boundaries, and AI-exported context.
Options:
- Hard ban on literal secrets with heuristic diagnostics.
- Allow references to external secret stores only.
- Add sensitivity/classification metadata and export policies.
AI recommendation: Ban literal secrets, allow references to external secret stores, and add sensitivity/classification metadata so AI context and public exports can be policy-gated.
Decision: Ban literal secrets, allow references to external secret stores, and add sensitivity/classification metadata so AI context and public exports can be policy-gated.
Impacts: Core schema, validation, AI context exporter, Studio warnings.
Decision needed before: First schema and validator implementation.
Resolution evidence: [ADR-0002 Implementation Readiness Decisions](./adr/ADR-0002-implementation-readiness-decisions.md)

## Q-009 - What repository owns implementation plans?
Status: Resolved
Raised by: User request to create implementation plans after documentation audit.
Question: Should implementation plans live in each implementation repo, in `UAG`, or both?
Why it matters: Plans that span repositories need coordination without duplicating or drifting.
Options:
- Each repo owns its own implementation plan; `UAG` owns a cross-repo master plan.
- `UAG` owns all plans; sibling repos link back.
- Each repo has plans and `UAG` tracks only milestones and dependencies.
AI recommendation: Let each implementation repo own its local implementation plan, while `UAG` owns a cross-repo master plan that tracks sequencing and dependency gates.
Decision: Let each implementation repo own its local implementation plan, while `UAG` owns a cross-repo master plan that tracks sequencing and dependency gates.
Impacts: Planning workflow, issue creation, dependency ordering, review process.
Decision needed before: Creating implementation plans.
Resolution evidence: [ADR-0002 Implementation Readiness Decisions](./adr/ADR-0002-implementation-readiness-decisions.md)

## Q-010 - What CI gates prove documentation readiness?
Status: Resolved
Raised by: Audit of draft specs and unchecked acceptance criteria.
Question: What automated checks should all repos run before implementation begins?
Why it matters: Broken links, invalid schemas, stale examples, and inconsistent spec indexes will compound quickly.
Options:
- Markdown link check and file naming only.
- Link check, spec index validation, example schema validation, and README asset check.
- Full cross-repo compatibility validation using generated schemas.
AI recommendation: Use a layered CI gate: markdown link checks and spec index validation first, then schema/example validation once `UAG-core` can publish schemas.
Decision: Use a layered CI gate: markdown link checks and spec index validation first, then schema/example validation once `UAG-core` can publish schemas.
Impacts: All repositories, PR workflow, release readiness.
Decision needed before: First implementation PRs.
Resolution evidence: [ADR-0002 Implementation Readiness Decisions](./adr/ADR-0002-implementation-readiness-decisions.md)

## Q-011 - Should source code compilation targets live in `UAG-compiler` or a separate repo?
Status: Resolved
Raised by: Direction change to graph-native architecture compiler platform with real code generation targets (Rust, TypeScript, C, React).
Question: Should the code generation backends (Rust emitter, TypeScript emitter, C emitter, React emitter) live inside `UAG-compiler`, or should they be extracted into a separate `UAG-codegen` repository?
Why it matters: Code generation is now a first-class output alongside diagrams and docs. If it grows substantially it could become a maintenance burden inside one repo, but splitting too early creates cross-repo versioning overhead.
Options:
- Keep codegen inside `UAG-compiler` as a `codegen/` module with per-language emitters.
- Create a separate `UAG-codegen` repo from the start.
- Keep codegen in `UAG-compiler` now, with a documented extraction criteria for later.
AI recommendation: Keep code generation in `UAG-compiler` as a `codegen/` module. The codegen step is the backend of the same pipeline — UAGL goes in, code comes out. A separate repo only makes sense when: (a) there are 5+ language targets with independent contributors, (b) each target has its own release cycle, or (c) build/test infrastructure per language becomes independently heavy.
Decision: Keep code generation in `UAG-compiler` with a `codegen/` module housing per-language emitters. Extract to a separate repo only when the independence criteria above are met.
Impacts: `UAG-compiler` module structure, release planning, versioning strategy.
Decision needed before: First compiler implementation plan.
Resolution evidence: Direction change to compiler platform identity, June 2026.

## Resolved Initialization Decisions
- R-001: Repos are `UAG`, `UAG-core`, `UAG-compiler`, and `UAG-studio`.
- R-002: Rust is used for system-level implementation.
- R-003: React + TypeScript are used for Studio frontend.
- R-004: TAKG is editable source; UAGL is compiled IR.
- R-005: All specs follow fixed `TYPE-NNN-name.md` naming and seven-section format.
- R-006: Code generation targets (Rust, TypeScript, C, React) are first-class compiler outputs, housed in `UAG-compiler` under a `codegen/` module.
