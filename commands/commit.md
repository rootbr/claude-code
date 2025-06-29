# Commit Changes

Review all staged and modified files. Split changes into atomic commits following Conventional Commits.

## Rules

- Each commit must have a single, clear purpose
- Format: `<type>(<scope>): <subject>`
- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `perf`
- Breaking changes: add `!` after type (e.g., `feat!`)
- Subject: imperative mood, lowercase, no period, max 50 chars
- Auto-update CLAUDE.md if architecture changes.

## Grouping

Group changes that:
- Fix the same issue
- Add one complete feature
- Refactor the same module

Split unrelated changes into separate commits.

## Examples

```
feat(auth): add OAuth2 login
fix(api): handle null user response
docs(readme): update setup instructions
refactor(utils): extract date helpers
```

Create commits now.