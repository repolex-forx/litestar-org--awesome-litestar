# Repolex Knowledge Graph of litestar-org/awesome-litestar

RDF knowledge graph data for [litestar-org/awesome-litestar](https://github.com/litestar-org/awesome-litestar), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download litestar-org/awesome-litestar
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 18a06dba3edf411a7d539c703a8468959a6138cd
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 18a06dba3edf411a7d539c703a8468959a6138cd
│           └── chunk-001.nq.gz
├── blob
│   ├── 07fe87db27d0143127c12bb76bc70cdf669b1f14.nq.gz
│   ├── 0a4e75c9b3951cd9f2dba6925036bc7b542af9fb.nq.gz
│   ├── 2176e3782c07e5635e70f56bf93dcaef31928676.nq.gz
│   ├── 4576f00c7619304f96e4e71016adcb44884fe1d9.nq.gz
│   ├── 4e6d77aa828f3c6b908b155dc38a880df9da7396.nq.gz
│   ├── 6c97be0d364b4055420de63de1cd24ef4d98a74b.nq.gz
│   ├── 74142023ac3f44bd90db66fad4480ebfbe6488be.nq.gz
│   ├── 8600db6a92a167d38f930e4ee2f684da9fe78dad.nq.gz
│   └── d932a95fe5139cbb4a498f758329ed8ff9ebf422.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 18a06dba3edf411a7d539c703a8468959a6138cd.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 16 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[litestar-org/awesome-litestar](https://github.com/litestar-org/awesome-litestar)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
