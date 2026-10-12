# Repolex Knowledge Graph of PyCQA/mccabe

RDF knowledge graph data for [PyCQA/mccabe](https://github.com/PyCQA/mccabe), parsed by [repolex](https://repolex.ai).

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
rlex download PyCQA/mccabe
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 292b5c71c3fe5496771b46ac9d86361c9b760d17
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 292b5c71c3fe5496771b46ac9d86361c9b760d17
│           └── chunk-001.nq.gz
├── blob
│   ├── 041ce5007156d76c86f9b9d9a9a540f307d86a37.nq.gz
│   ├── 0a584e05b08039e3b75b6fc223c9a33009a56115.nq.gz
│   ├── 4ddce38aaf4f4e26492e22a0fcba59e909a55699.nq.gz
│   ├── 5864ba48fd34e9e2f72bd874adba286535e14bc2.nq.gz
│   ├── 8fd356e83a1edda3750e85a91b79fbfa1ca3d5e9.nq.gz
│   ├── 9092497064116d30072d96edb7d67ca34054ef14.nq.gz
│   ├── a2bd6db0e89e70eaddc3dac548b995ec834d0897.nq.gz
│   ├── c0de7f55a6933bc50e4b8f696e2ff8d9480112f0.nq.gz
│   ├── cc10d7c1fd54e4513dbdd6edc68373268e75b821.nq.gz
│   └── ed8a958e0a8da154b0db9b1edca6e47e5dae146a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 292b5c71c3fe5496771b46ac9d86361c9b760d17.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 18 files
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

[PyCQA/mccabe](https://github.com/PyCQA/mccabe)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
