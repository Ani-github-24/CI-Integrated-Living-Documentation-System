## Description
<!-- Provide a clear, concise summary of the changes introduced in this PR -->

## Type of Change
- [ ] `feat`: New feature or capability
- [ ] `fix`: Bug fix
- [ ] `docs`: Documentation or design document update
- [ ] `chore`: Process setup, tooling, or dependency update
- [ ] `test`: Testing, benchmarking, or evaluation harness update

## Pre-Merge Checklist
- [ ] Created an immutable worklog entry in `/docs/worklog/<timestamp>-<handle>-<slug>.md`
- [ ] Ran `node scripts/build-log-index.mjs` to update `/PROJECT_LOG.md`
- [ ] Verified `node scripts/build-log-index.mjs --check` passes cleanly
- [ ] Verified zero third-party egress: no secrets, external API dependencies, or credential leaks
- [ ] Used Conventional Commits formatting with `Co-authored-by` trailer if agent-assisted
