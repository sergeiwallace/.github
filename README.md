# .github

Account-wide default community health files for `sergeiwallace` repositories that don't ship
their own local override (GitHub falls back to these — `PULL_REQUEST_TEMPLATE.md` here becomes
every consumer repo's default PR template).

- `PULL_REQUEST_TEMPLATE.md` — default PR template; its opening comment also documents the PR title
  convention (`type(optional-scope): concise summary`). Source of truth:
  `ai-harness/docs/templates/github-account-pull-request-template.md`.

This repo must stay public — GitHub does not support a private repo as a default-community-health
-file source, even for repos it applies to that are themselves private.
