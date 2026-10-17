# Repolex Knowledge Graph of colcon/colcon-ed

RDF knowledge graph data for [colcon/colcon-ed](https://github.com/colcon/colcon-ed), parsed by [repolex](https://repolex.ai).

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
rlex download colcon/colcon-ed
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e1b5b7e10141f4c826af1c03b58cfa9253ac60f8
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── e1b5b7e10141f4c826af1c03b58cfa9253ac60f8
│           └── chunk-001.nq.gz
├── blob
│   ├── 0f17157ed42b486a0c57cbffddd97987a4844e6b.nq.gz
│   ├── 131ac2ae9d760f8cce03c5201adadbadd9359b26.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 40620b2a675d8842d6258bfe6a571fb59c36036f.nq.gz
│   ├── 4697e69b03204c9b21bc2cfd599eb07d28c67766.nq.gz
│   ├── 4f2f3c7d07dc7e23af82f38436d6da4d54fcc3d6.nq.gz
│   ├── 73f870278f48a0a7e2a8446af0dbf2ce05453c99.nq.gz
│   ├── 801c0b5227458325e345acb848084b2d5f0b2777.nq.gz
│   ├── 9e92f73620642c4b0ba010e9d0b2a4fea472c96a.nq.gz
│   ├── bd7c8693b373f16474a10254e75b502ef8389f27.nq.gz
│   ├── d54766d12c4eafd935b9c8f3e430315fcd54d8ed.nq.gz
│   ├── dffe460f162da9929178a7ce342532e7ba896425.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── eca156cfd9536534f4050984b49e4e07d91dfa3b.nq.gz
│   └── f7618b310225191457820ac09d91244706cc246b.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── e1b5b7e10141f4c826af1c03b58cfa9253ac60f8.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 23 files
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

[colcon/colcon-ed](https://github.com/colcon/colcon-ed)

---
*Parsed on 2026-10-17 by [repolex](https://repolex.ai)*
