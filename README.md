<p align="center">
    <img src="https://cocoindex.io/images/github.svg" alt="CocoIndex">
</p>

<h1 align="center">Build Real-Time Codebase Indexing </br> for [Coding Agents | Code Review Agents | ...]</h1>

<div align="center">

[![GitHub](https://img.shields.io/github/stars/cocoindex-io/cocoindex?color=5B5BD6)](https://github.com/cocoindex-io/cocoindex)
[![Documentation](https://img.shields.io/badge/Documentation-394e79?logo=readthedocs&logoColor=00B9FF)](https://cocoindex.io/docs/getting_started/quickstart)
[![License](https://img.shields.io/badge/license-Apache%202.0-5B5BD6?logoColor=white)](https://opensource.org/licenses/Apache-2.0)
[![PyPI version](https://img.shields.io/pypi/v/cocoindex?color=5B5BD6)](https://pypi.org/project/cocoindex/)
<!--[![PyPI - Downloads](https://img.shields.io/pypi/dm/cocoindex)](https://pypistats.org/packages/cocoindex) -->
[![PyPI Downloads](https://static.pepy.tech/badge/cocoindex/month)](https://pepy.tech/projects/cocoindex)
[![CI](https://github.com/cocoindex-io/cocoindex/actions/workflows/CI.yml/badge.svg?event=push&color=5B5BD6)](https://github.com/cocoindex-io/cocoindex/actions/workflows/CI.yml)
[![release](https://github.com/cocoindex-io/cocoindex/actions/workflows/release.yml/badge.svg?event=push&color=5B5BD6)](https://github.com/cocoindex-io/cocoindex/actions/workflows/release.yml)
[![Link Check](https://github.com/cocoindex-io/cocoindex/actions/workflows/links.yml/badge.svg)](https://github.com/cocoindex-io/cocoindex/actions/workflows/links.yml)
[![Discord](https://img.shields.io/discord/1314801574169673738?logo=discord&color=5B5BD6&logoColor=white)](https://discord.com/invite/zpA9S2DR7s)

</div>

<div align="center">
  
[Step By Step Tutorial](https://cocoindex.io/examples/code_index)
[Youtube](https://youtu.be/G3WstvhHO24?si=Bnxu67Ax5Lv8b-J2)

</div>


Build codebase index. CocoIndex provides built-in support for codebase chunking, with native Tree-sitter support. It works with large codebases, and can be updated in near real-time with incremental processing - only reprocess what's changed.

## Usecases
<img width="2732" height="1540" alt="cover" src="https://github.com/user-attachments/assets/5b4bdf75-7e7f-4503-837c-ebe86ec81ddc" />

A wide range of applications can be built with an effective codebase index that is always up-to-date.

- Semantic code context for AI coding agents like Claude, Codex, Gemini CLI.
- MCP for code editors such as Cursor, Windsurf, and VSCode.
- Context-aware code search applications—semantic code search, natural language code retrieval.
- Context for code review agents—AI code review, automated code analysis, code quality checks, pull request summarization.
- Automated code refactoring, large-scale code migration.
- SRE workflows: enable rapid root cause analysis, incident response, and change impact assessment by indexing infrastructure-as-code, deployment scripts, and config files for semantic search and lineage tracking.
- Automatically generate design documentation from code—keep design docs up-to-date.



## Steps

### Indexing Flow

<p align='center'>
  
 <img width="1710" height="1220" alt="flow" src="https://github.com/user-attachments/assets/4134ce8a-f65a-4f0f-9513-1de38bb81c41" />

</p>

1. We will ingest CocoIndex codebase.
2. For each file, perform chunking (Tree-sitter) and then embedding.
3. We will save the embeddings and the metadata in Postgres with PGVector.

### Query

We will match against user-provided text by a SQL query, reusing the embedding operation in the indexing flow.

## Prerequisite

[Install Postgres](https://cocoindex.io/docs/getting_started/installation#-install-postgres) if you don't have one.

## Run

- Install dependencies:

  ```sh
  pip install -e .
  ```

- Update index:

  ```sh
  cocoindex update main
  ```

- Run:

  ```sh
  python main.py
  ```

## CocoInsight

I used CocoInsight (Free beta now) to troubleshoot the index generation and understand the data lineage of the pipeline.
It just connects to your local CocoIndex server, with Zero pipeline data retention. Run the following command to start CocoInsight:

```
cocoindex server -ci main
```

<img width="2087" height="1800" alt="chunk" src="https://github.com/user-attachments/assets/a63e96f6-cfc3-4c82-9552-6d741f36cf9f" />



Then open the CocoInsight UI at [https://cocoindex.io/cocoinsight](https://cocoindex.io/cocoinsight).

<img width="1305" alt="Chunking Visualization" src="https://github.com/user-attachments/assets/8e83b9a4-2bed-456b-83e5-b5381b28b84a" />
