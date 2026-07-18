# Git Hooks

## Pre-commit Hook

Runs the same checks as `.github/workflows/ci.yml` so failures show up
locally instead of in CI:

1. `moon fmt --check` — fail if formatting drifted
2. `moon check --deny-warn` — type-check, warnings as errors
3. `moon info` + `.mbti` diff — fail if package interfaces drifted
4. `moon test` — run all unit + integration tests

### Usage Instructions

1. Make the hook executable if it isn't already:
   ```bash
   chmod +x .githooks/pre-commit
   ```

2. Configure Git to use the hooks in the `.githooks` directory:
   ```bash
   git config core.hooksPath .githooks
   ```

3. The hook will automatically run when you execute `git commit`.
