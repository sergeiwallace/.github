# PR title convention

Configure squash merges to use the PR title as the resulting commit subject, so this convention is
also the commit-title convention.

Format:

```
type(scope): description
```

- `type` — one of `feat|fix|perf|refactor|docs|test|build|ci|chore|revert` (Conventional Commits).
- `scope` — the bd issue display id when the PR is tied to one (e.g. `AIH-786`), otherwise omit.
- `description` — imperative, lower-case, no trailing period.

Examples:

```
feat(AIH-786): fleet-wide delegation provenance standard
fix(AIH-tzgx6.9): ship export LICENSE + fix shell-profile command injection
chore(beads): sync mirror
```

Source: `docs/research/pr-bots-and-multiagent-pr-workflow-best-practices.md` § 5 (ai-harness) —
title linting is only load-bearing when the squash title becomes the commit subject or another
automation parses it; keep any title check advisory unless changelog/release tooling depends on it.
