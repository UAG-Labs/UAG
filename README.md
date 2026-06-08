<p align="center">
  <img src="./assets/logos/uag-labs-readme-banner.svg" alt="UAG banner" />
</p>

# UAG

**UAG-Labs is building a graph-native architecture compiler platform. Software architecture becomes source code.**

The architecture graph is the program — not a picture of it. It describes software as nodes, edges, events, capabilities, resources, constraints, and goals. The compiler validates, transforms, and compiles that graph into real implementation targets.

```text
The architecture graph is the source of truth.
The diagram is a view.
The export is a projection.
The code is a compilation target.
```

## Documentation

All specifications, architecture decisions, research, plans, and examples live in [`docs/`](./docs/README.md).

| Path | Contents |
|---|---|
| [`docs/architecture.md`](./docs/architecture.md) | System architecture and design |
| [`docs/open-questions.md`](./docs/open-questions.md) | Decisions log |
| [`docs/specs/`](./docs/specs/) | Language and system specifications |
| [`docs/plans/`](./docs/plans/) | Roadmap and implementation plans |
| [`docs/adr/`](./docs/adr/) | Architecture decision records |
| [`docs/research/`](./docs/research/) | Research summaries |
| [`examples/`](./examples/) | TAKG and UAGL examples |

## Repositories

| Repository | Purpose |
|---|---|
| [`UAG`](https://github.com/UAG-Labs/UAG) | This repo — specs, docs, examples, research, roadmap |
| [`UAG-core`](https://github.com/UAG-Labs/UAG-core) | Shared Rust graph model, schemas, ontology, dialects, validation primitives |
| [`UAG-compiler`](https://github.com/UAG-Labs/UAG-compiler) | Rust compiler and CLI — validates TAKG, lowers to UAGL, compiles to all targets |
| [`UAG-studio`](https://github.com/UAG-Labs/UAG-studio) | React visual editor — the human trust and inspection layer |
