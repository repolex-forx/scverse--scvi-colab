# Repolex Knowledge Graph of scverse/scvi-colab

RDF knowledge graph data for [scverse/scvi-colab](https://github.com/scverse/scvi-colab), parsed by [repolex](https://repolex.ai).

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
rlex download scverse/scvi-colab
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 4bf7fcf9380272ad5c093e3f03870acac048ef26
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 4bf7fcf9380272ad5c093e3f03870acac048ef26
│           └── chunk-001.nq.gz
├── blob
│   ├── 0b5b93c5d2d852707f00049d3671ad8b7c2b66b7.nq.gz
│   ├── 1fb9b14d331cd7a186a8c0638a560aa3e3dd8aed.nq.gz
│   ├── 26d33521af10bcc7fd8cea344038eaaeb78d0ef5.nq.gz
│   ├── 373253be0cf05bb804c19e505b59b1f25457979a.nq.gz
│   ├── 491e46609299189dc3f9ba9a65293adf461a4aca.nq.gz
│   ├── 4fd9ffca430b1d0a6c0d151be1fff8d0a22ecf40.nq.gz
│   ├── 7e2320f2f32a5954a0e7e92a982fbe5129bf9d6a.nq.gz
│   ├── 914ad69d5046bebb8743ad4f7a9f003284d56925.nq.gz
│   ├── aac4cf4e016b70366ab6a4e8a31dd87dcf486ce7.nq.gz
│   ├── cdbbe3d9ddf02378537429f9fc3fd252b5043a26.nq.gz
│   ├── cec2437153b4010766958c951dfdfda33369600d.nq.gz
│   ├── d3a6bd11da36e5c596e2d2bc3d77d14dfdf2d914.nq.gz
│   ├── d5d78d87aac05ee25dd73a45a6ddad367d1a098f.nq.gz
│   ├── dc7e9b7466e239ee9714d5e3612bb2c595df2c0e.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── e7381556efdf6a9b8218a109f7a7e7836e712ccd.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 4bf7fcf9380272ad5c093e3f03870acac048ef26.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 24 files
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

[scverse/scvi-colab](https://github.com/scverse/scvi-colab)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
