<!-- .github/PULL_REQUEST_TEMPLATE.md -->
### Provide a detailed explanation of *WHAT* this PR does and *WHY* it's needed.

### Checklist
- [ ] Commit messages have the following format:

```text
<type>: <description of change>

<body>

<footer(s): linked to GH Issue(s)>
```

For breaking changes, add `!` after the type:
```text
<type>!: <description of breaking change>
```
`<type>` can be:
- **ci:** Changes to continuous integration (CI) configuration, scripts, or workflows (e.g., updating GitHub Actions, 
  build pipelines, or deployment processes).
- **docs:** Updates to documentation, such as README files, API docs, or code comments, without affecting the 
  codebase's functionality.
- **feat:** Introduces a new feature or significant enhancement to the codebase.
- **refactor:** Code changes that improve structure or readability (e.g., renaming variables, reorganizing code) 
  without altering functionality or fixing bugs.
- **revert:** Reverts a previous commit or set of changes, restoring the codebase to an earlier state (e.g., undoing a 
  problematic feature or bug fix).
- **test:** Additions or modifications to tests, such as unit tests, integration tests, or test scripts, without 
  changing production code. 

> **`<footer>:` References GitHub Issues related to the change.
- **Resolves #<issue-number>:** Closes a specific issue when merged.
- **Refs #<issue-number>:** References a related issue without closing it.

> **`!` after the type indicates a breaking change.**
> **A blank line is required between body and footer**
 
### Required before merge
- [ ] One logical change per commit.
- [ ] Changes unrelated to the PR title are absent.
- [ ] Related changes are squashed.
- [ ] Merge commits are absent.
- [ ] Referenced Issue is linked in footer.
- [ ] Conflicts are resolved; if necessary, use rebase:
  - Rebase: `git pull --rebase <upstream_remote> dev`
  - If there are conflicting changes, resolve them and run: `git rebase --continue`
  - Push your changes: `git push -f <your_remote> <feature_branch>`
- [ ] CI tests all pass.
