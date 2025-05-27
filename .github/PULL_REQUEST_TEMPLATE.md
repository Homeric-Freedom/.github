<!-- .github/PULL_REQUEST_TEMPLATE.md -->
### 📋 Summary
Provide a detailed explanation of *WHAT* this PR does and *WHY* it's needed.

### ✅ Checklist
- [ ] Commit messages have the following format:

```
<type>: <description of change>

[required body]

[footer(s): required, when linked to a specifc Issue]
```
`<type>` can be one of the following:
- ci: Changes to continuous integration (CI) configuration, scripts, or workflows (e.g., updating GitHub Actions, build pipelines, or deployment processes).
- docs: Updates to documentation, such as README files, API docs, or code comments, without affecting the codebase's functionality.
- refactor: Code changes that improve structure or readability (e.g., renaming variables, reorganizing code) without altering functionality or fixing bugs.
- revert: Reverts a previous commit or set of changes, restoring the codebase to an earlier state (e.g., undoing a problematic feature or bug fix).
- test: Additions or modifications to tests, such as unit tests, integration tests, or test scripts, without changing production code.
- wip: Work-in-progress commits, indicating incomplete or temporary changes that are not ready for production or final review.

Example:
```
ci: add commitlint to CI pipeline

Added commitlint configuration and GitHub Action workflow to enforce conventional commit messages. This ensures all commits follow the project's commit message format (e.g., type: description) for better changelog generation and readability.

- Installed @commitlint/cli and @commitlint/config-conventional
- Created .commitlintrc.json with rules for allowed types (ci, docs, refactor, revert, test, wip)
- Updated .github/workflows/ci.yml to run commitlint on push events

Fixes #123
```
**Note the required whiteline between body and footer**
 
### Required before merge
- [ ] 1 major change per commit.
- [ ] Changes unrelated to the PR title are absent.
- [ ] Related changes are squashed.
- [ ] Merge commits are absent (use `git rebase`).
  - You will be asked to rebase, if there are conflicts (even trivially resolvable ones).
- CI must pass
