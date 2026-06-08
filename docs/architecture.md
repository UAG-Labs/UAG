# Architecture — UAG

## Identity
UAG is a graph-native architecture compiler platform. The architecture graph is the program. The compiler validates, transforms, and compiles it into real implementation targets. UAG is not a diagramming tool.

## Boundary
This repo coordinates the full ecosystem through docs, specs, examples, research, and roadmap.

## Core Pipeline
```text
Human or AI edits TAKG (in Studio or directly)
→ Policy engine resolves naming, code decisions, adapter bindings
→ Compiler validates and resolves
→ Compiler lowers to UAGL (normalized IR)
→ Compiler emits: Rust · TypeScript · React · C
                  diagrams · docs · contracts · deployment · AI context
```

## Graph Primitives
The seven typed primitives that every UAG graph is built from:

| Primitive | Description |
|---|---|
| **Nodes** | Systems, services, modules, components, agents, processes |
| **Edges** | Calls, dependencies, data flows, event subscriptions |
| **Events** | Domain events, commands, queries, notifications |
| **Capabilities** | Operations a node exposes or consumes |
| **Resources** | Databases, queues, stores, streams, cloud primitives |
| **Constraints** | Security boundaries, SLAs, data retention, access rules |
| **Goals** | Business objectives, quality attributes, non-functional requirements |

## Behavior Layers
The graph carries behavior in five layers, each more granular than the last:

```text
1. STRUCTURE   — nodes, edges: what exists and what connects
2. STATE       — state machines per capability: control flow and error paths
3. COMPOSITION — predicates + effects + typed dataflow: logic from primitives
4. POLICY      — how primitives map to implementation decisions
5. HOLES       — typed contracts for irreducible business logic → adapter implementations
```

Layers 1–3 are pure graph. Layer 4 is policy configuration. Layer 5 is the honest escape valve — the existence, contract, and adapter binding of every hole is still tracked in-graph.

## Compilation vs Projection
- **Compilation targets** (Rust, TypeScript, C, React) — the compiler emits working code from the graph.
- **Projections** (diagrams, docs, API contracts, AI context) — views generated from the graph.

Both flow from UAGL. Neither is the source of truth. Code is compiled, not projected.

## Platform Scope
UAG compiles well for: service-oriented systems, event-driven architectures, APIs, cloud-native infrastructure, AI agent topologies.

UAG does not target: embedded/real-time systems, game engines, numerical computing, OS kernels, or firmware. For platform gaps, adapters are built in Rust and registered with the policy engine — the platform capability is not faked.

## Studio
The visual editor is the human trust and inspection layer. AI systems can read and modify the graph directly, but Studio is required for human understanding and approval. The compiled output is read-only — all developer intent flows back through the graph.

## Event-Driven Compilation
The compiler supports incremental, event-driven recompilation. When any graph node changes, only affected output files are regenerated. This enables live, reactive compilation from Studio or AI modifications.

## Sibling Repo Map
- `UAG-core` — canonical Rust graph model, new node types (StateMachine, Predicate, Effect, Transformation, Hole), schema versioning
- `UAG-compiler` — validates TAKG, runs policy engine, lowers to UAGL, emits all targets via codegen/ module and adapter system
- `UAG-studio` — visual editor, trust layer, event-driven compilation UI
