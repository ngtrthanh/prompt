# CLAUDE.md — code-quality baseline

Copy into a repo root (or `~/.claude/CLAUDE.md` for all repos). Rules distilled from
Anthropic's prompting best practices (see README sources), rewritten for our stack.

## Truthfulness
- Read a file before making any claim about it. No guessing about unopened code.
- Label unconfirmed statements: [Inference], [Speculation], [Unverified].
- If a test or requirement looks wrong, say so. Do not work around it.

## Scope
- Change only what was asked or is strictly required.
- No drive-by refactors, no new abstractions for one-off code, no speculative config.
- No comments/docstrings/types added to lines you did not touch.
- Validate only at boundaries (user input, external APIs, devices, files). Trust internal code.
- Delete any scratch files/scripts you created before finishing.

## Correctness
- Solve the general case. Never hard-code values to make a test pass.
- Never swallow errors. Every catch/`if err != nil`/`Result` path either handles, wraps with context, or propagates.
- No silent fallbacks (default values that hide a failure) unless the task asks for them.

## Safety
- Ask before: deleting files/branches, dropping tables, `rm -rf`, `git push --force`,
  `git reset --hard`, pushing, touching shared infra.
- Never bypass checks (`--no-verify`, disabling lint/tests).

## Stack conventions
- Go: `gofmt`, `go vet`, errors wrapped with `%w`.
- Rust: `cargo fmt`, `cargo clippy -D warnings`; no `unwrap()` outside tests.
- Python/FastAPI: `ruff`, typed signatures on public functions.
- TS/JS: `tsc --noEmit` clean; vanilla JS stays dependency-free.
- Docker: `docker compose` (never `docker-compose`); no `version:` key in compose files.

## Workflow
- One WIP at a time (FOCUS.md). New ideas go to IDEAS.md, not into the current change.
- Before declaring done: run build, lint, tests; report what ran and the result.
