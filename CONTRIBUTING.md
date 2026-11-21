# Contributing to DocPulse

Welcome to the DocPulse repository. This document outlines our development workflow, branching model, commit conventions, and mandatory worklog protocol.

---

## 1. Branching Strategy

- **Default Branch (`main`)**: The default branch must always be in a deployable, clean state.
- **Never Push Directly to `main`**: All modifications must arrive through Pull Requests.
- **Branch Naming Conventions**:
  - `feat/<task-slug>`: New features or capabilities.
  - `fix/<task-slug>`: Bug fixes and defect remediation.
  - `chore/<task-slug>`: Tooling, dependency, or process updates.
  - `docs/<task-slug>`: Documentation and design specification updates.
  - `spike/<task-slug>`: Time-boxed technical exploration spikes.

---

## 2. Commit Message Standards

DocPulse strictly enforces [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<optional scope>): <description>

[optional body explaining context and rationale]

Co-authored-by: <agent name> <agent email>
```

### Commit Types
- `feat`: A new feature or capability.
- `fix`: A bug fix.
- `docs`: Documentation only changes.
- `chore`: Maintenance, repository setup, or dependency updates.
- `test`: Adding or updating test fixtures and benchmarks.
- `refactor`: Code refactoring without behavioral modification.

### Agent Co-Authorship Trailer
When working with an AI assistant or agent, you must append the `Co-authored-by` trailer to preserve provenance:
```
Co-authored-by: Antigravity <agent@deepmind.com>
```

---

## 3. Mandatory Work Log Rule

DocPulse maintains an immutable audit trail of all project work in `/docs/worklog/`:

1. **One File Per Task**: Never write to a shared log file directly. Create:
   `/docs/worklog/<timestamp>-<handle>-<slug>.md`
2. **Real Shell Timestamps**: Obtain timestamps via `date +"%Y-%m-%dT%H%M%S%z"`. Never guess or mock a timestamp.
3. **Regenerate the Index**: Run `node scripts/build-log-index.mjs` before committing.
4. **CI Verification**: Every pull request is validated by a GitHub Actions check (`.github/workflows/worklog-check.yml`) that asserts:
   - At least one new worklog entry is included in the PR diff.
   - `PROJECT_LOG.md` is strictly synchronized (`node scripts/build-log-index.mjs --check`).

---

## 4. Security & Privacy Standard: Zero Third-Party Egress

- **Zero Third-Party Egress**: Codebases and documentation must never be exfiltrated to external third-party services, hosted LLMs, or paid SaaS platforms.
- **No Secrets in Repos**: Never commit API keys, personal access tokens, or credentials.
- **Fork Safety**: All PR validation workflows must operate in read-only mode using `$GITHUB_STEP_SUMMARY` and workflow annotations.
