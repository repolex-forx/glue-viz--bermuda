# Repolex Knowledge Graph of glue-viz/bermuda

RDF knowledge graph data for [glue-viz/bermuda](https://github.com/glue-viz/bermuda), parsed by [repolex](https://repolex.ai).

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
rlex download glue-viz/bermuda
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 0bc26bac376d4f08a4964481d1f737f6deb86270
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 0bc26bac376d4f08a4964481d1f737f6deb86270
│           └── chunk-001.nq.gz
├── blob
│   ├── 0b7e90a5769d5e45dae418f0e034fd90269bdc99.nq.gz
│   ├── 4247f48b604b3266e1275af7b2726e5ce1f8fff2.nq.gz
│   ├── 488bab05f63072bda2febf3c3b9e1cc8f86f8ee6.nq.gz
│   ├── 51cbe85254929af8fd49313f8a53a5e2fdab1347.nq.gz
│   ├── 6a548bbb764aed051f286853f62d968fbc992574.nq.gz
│   ├── 8c7936f34badf732b9ccd13305cc42eaadae52ef.nq.gz
│   ├── 8dedf326c8351e9a175aadaaf4e5c00e01f7b8c7.nq.gz
│   ├── a7c8d5b5d388f20e75af07eb3cf668b8787596cc.nq.gz
│   ├── b616985678754ac20d25b88c375155b4e8fd271e.nq.gz
│   ├── df5ac96627e0b1c7a3335d449697aa481c74fde6.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── f4c47287903b7c2b21bb0a8ce79dbf75c98fcfb4.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 0bc26bac376d4f08a4964481d1f737f6deb86270.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 20 files
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

[glue-viz/bermuda](https://github.com/glue-viz/bermuda)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
