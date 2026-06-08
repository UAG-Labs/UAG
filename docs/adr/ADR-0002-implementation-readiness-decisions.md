# ADR-0002 - Implementation Readiness Decisions for UAG

## Status
Accepted

## Context
The first documentation audit identified open implementation-readiness questions for UAG. The questions covered ecosystem contracts, cross-repo ownership, examples, exports, security, CI, and implementation plan ownership. Each question received an AI recommendation after reviewing the repository documentation and comparable systems.

## Decision
Adopt the AI recommendations recorded in [open-questions.md](../open-questions.md) as the planning baseline for the first implementation plans. These decisions are not final product law; they are the current accepted defaults that implementation plans should use unless a later ADR supersedes them.

## Decisions
| Question | Topic | Decision |
|---|---|---|
| Q-001 | What is the authoritative cross-repo contract for TAKG and UAGL? | Use `UAG` specs as the normative intent contract until `UAG-core` can generate versioned schemas; after that, publish a contract bundle from `UAG-core` and reference it from `UAG` as the executable form of the prose specs. |
| Q-002 | What versioning policy governs the four repositories? | Version language schemas independently, and version each implementation repo with semver plus an explicit compatibility matrix. Avoid lockstep releases unless a breaking language change requires coordinated publishing. |
| Q-003 | What are the first official architecture dialects? | Ship `core` first, with AI-agent/MCP, enterprise/domain, low-level systems, and data-systems represented as draft dialect fixtures rather than fully enforced dialects in milestone one. |
| Q-004 | What is the first supported view model? | Represent views as semantic filters over the graph, keep layout as separate per-view TAKG/editor metadata, and compile only resolved projection definitions into UAGL. |
| Q-005 | What external export targets are in the first milestone? | Start with Mermaid, D2, Markdown summaries, and AI context as the first exporter set; define OpenAPI and AsyncAPI contracts now but implement them after the core graph contract stabilizes. |
| Q-006 | What is the minimum example suite that proves the model? | Keep the current four examples as canonical long-form examples, and add one small smoke-test example that CI can compile quickly on every repo change. |
| Q-007 | What does "loss report" mean across the ecosystem? | Make loss reporting pipeline-wide, but require every exporter to produce an exporter-specific loss section. This keeps compile/import/export honesty under one shared model. |
| Q-008 | What is the security boundary for architecture data? | Ban literal secrets, allow references to external secret stores, and add sensitivity/classification metadata so AI context and public exports can be policy-gated. |
| Q-009 | What repository owns implementation plans? | Let each implementation repo own its local implementation plan, while `UAG` owns a cross-repo master plan that tracks sequencing and dependency gates. |
| Q-010 | What CI gates prove documentation readiness? | Use a layered CI gate: markdown link checks and spec index validation first, then schema/example validation once `UAG-core` can publish schemas. |

## Consequences
- Implementation plans can proceed from a concrete baseline instead of unresolved ambiguity.
- Future disagreement should create a new open question and, if accepted, a superseding ADR.
- Specs and plans should cite this ADR when they rely on these decisions.

## Follow-up
- Update implementation plans to reference this ADR.
- Promote decisions into detailed specs when implementation starts.
