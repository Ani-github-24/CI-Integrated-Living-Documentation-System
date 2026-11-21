# Work Log Protocol

This directory contains immutable, per-task record files for **DocPulse**.

## Entry Format
Every task, architectural decision, design document, test, or code change must be recorded in its own dedicated Markdown file:
`/docs/worklog/<timestamp>-<handle>-<slug>.md`

### 1. File Naming Convention
- `<timestamp>`: Derived from system execution via `date +"%Y-%m-%dT%H%M%S%z"` (e.g., `2026-11-21T115849+0530`). Never guess or mock a timestamp.
- `<handle>`: The author's git handle (e.g., `Ani-github-24`).
- `<slug>`: Short, hyphen-separated descriptor of the task (e.g., `process-setup`).

### 2. Entry Schema
Each entry file must contain the following structured fields:
```markdown
# Worklog Entry: <timestamp>-<handle>-<slug>

- **Timestamp**: `<timestamp>`
- **Type**: `decision` | `design` | `code` | `test` | `infra` | `docs` | `fix`
- **Summary**: Concise description of changes.
- **Files Touched**:
  - `path/to/file1`
  - `path/to/file2`
- **Rationale**: Architectural or operational justification.
- **Author**: `human` | `agent`
- **Directed By**: GitHub handle of person directing the task
```

### 3. Rules
- **Immutable**: Never modify or reorder historical entries. Corrections are new entries referencing earlier ones.
- **Auto-generated Index**: Do not edit `PROJECT_LOG.md` directly. Run `node scripts/build-log-index.mjs` to regenerate the chronological index.
- **PR Requirement**: Every pull request must introduce at least one new worklog entry and verify index synchronization via `node scripts/build-log-index.mjs --check`.
