# Release standard for public repositories

Every public repository that ships versions follows one stack.

| Part | Rule |
|---|---|
| Versioning | [Semantic Versioning](https://semver.org/spec/v2.0.0.html). While the major version is 0, a minor release may add a subsystem or change an interface and a patch release only fixes defects and documentation. A major bump is a deliberate decision, never automatic. |
| Commits | [Conventional Commits](https://www.conventionalcommits.org/). `feat` raises the minor version, other types raise the patch version, and `type!:` or a `BREAKING CHANGE:` footer asks for a major one. |
| Changelog | `CHANGELOG.md` in [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) form, with one `## [X.Y.Z]` section per release and `## [Unreleased]` on top. A `feat` change adds its entry in the same commit. |
| Version source | One file per repository holds the version: `pyproject.toml`, `VERSION`, or a JSON file such as `plugin.json`. |
| Tags | `vX.Y.Z`, created from the default branch when the version file's version has no tag yet. A `protect-release-tags` ruleset blocks moving or deleting `v*` tags. |
| Release | A GitHub Release per tag, with that version's `CHANGELOG.md` section as its notes. |
| Registry publishing | PyPI or npm publishing is opt-in per repository and has its own workflow, triggered by the tag. |

## Adding it to a repository

1. Put `CHANGELOG.md` and the version file in place.
2. Add this caller as `.github/workflows/release.yml`:

   ```yaml
   name: Release
   on:
     push:
       branches: [main]
       paths: [CHANGELOG.md, pyproject.toml]   # the changelog and the version file
   permissions:
     contents: write
   jobs:
     release:
       uses: sergeiwallace/.github/.github/workflows/release.yml@main
       with:
         version-file: pyproject.toml
         title: myproject
   ```

3. Add a `protect-release-tags` ruleset for `refs/tags/v*` that blocks deletion, non-fast-forward
   updates and updates.

A release happens when a change that raises the version reaches the default branch. A push that
leaves the version alone finds its tag and does nothing.
