# DocPulse

A TypeScript GitHub Action that keeps documentation in sync with code on the user's own GitHub runner with zero third-party egress (no server, no database, no paid hosting).

## Overview
DocPulse operates directly within a repository's GitHub Actions workflow to parse source code, extract contracts from existing documentation, detect drift, and automatically reconcile marked documentation blocks or open pull requests for prose suggestions.

## Problem
Documentation drifts out of sync as codebases evolve. Manual peer review frequently overlooks changes to API signatures, parameter models, and architecture diagrams, resulting in stale READMEs, broken integration examples, and degraded developer trust.

## Architecture
DocPulse follows a two-phase architecture:
1. **Deterministic AST Gate (Phase 1)**: Extracts symbol tables from Python (FastAPI) and TypeScript using `web-tree-sitter` (WASM) and matches them against Markdown parameter tables and Mermaid import diagrams. Exit code controls CI status.
2. **Advisory Reconciliation & Telemetry (Phase 2)**: Reconciles marker blocks (`<!-- docpulse:start NAME -->` ... `<!-- docpulse:end NAME -->`) on default-branch pushes with `[skip ci]` metadata, emits GitHub Step Summaries and line annotations on PRs, and exports telemetry to the `docpulse-data` branch for visualization on a static GitHub Pages dashboard.

See [`docs/designs/01-problem-statement.md`](./docs/designs/01-problem-statement.md) and [`docs/designs/concepts_brief.md`](./docs/designs/concepts_brief.md) for full design specifications.

## Setup
TBD

## Usage
TBD

## Testing
TBD

## Deployment
TBD

## Team
3-person university capstone team:
- **Student 1 (Lead)**: Core Static Analysis & AST/Mermaid Engine (`/packages/core`)
- **Student 2 (Lead)**: Action Runtime & Idempotent Reconciler (`/packages/reconciler`, `/action`)
- **Student 3 (Lead)**: Observability Dashboard, Metrics & Benchmarks (`/dashboard`, `/benchmarks`)

## Links
- [Project Log](./PROJECT_LOG.md)
- [Design Documents](./docs/designs)
- [Worklog Protocol](./docs/worklog)
- [Contributing Guide](./CONTRIBUTING.md)
