<!-- .github/PULL_REQUEST_TEMPLATE.md -->
### 📋 Summary
Provide a detailed explanation of *WHAT* this PR does and *WHY* it's needed.

### ✅ Checklist
- [ ] Commit messages have the following format:

```text
<type>(<scope>)<!>: <description of change>

<body>

<footer>
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

`<scope>` can be:
- **a component:** defined by the project, such as a specific feature, module, or library (e.g., `auth`, `ui`, `api`).
- **a module:** a specific part of the codebase, such as a directory or file (e.g., `src/components`, `lib/utils`).
- **another logical grouping:** such as a specific functionality or aspect of the project (e.g., `performance`, 
  `security`).  

**Note: <!> is placed immediately after the scope in the commit message header to indicate a breaking change.**

`<description of change>`: a concise summary of the change, written in the imperative mood (e.g., "add", "fix", "update").

`<body>`: a detailed explanation of the change, including the motivation, context, and any relevant 
implementation details. This helps reviewers understand the reasoning behind the change and its impact on the project.

`<footer>:` optional, but recommended for referencing issues or pull requests related to the change.
- **Fixes #<issue-number>:** Closes a specific issue when merged.
- **Related to #<issue-number>:** References a related issue without closing it.
- **Refs #<issue-number>:** References an issue for context.
- **BREAKING CHANGE:** Indicates a breaking change in the codebase.
Example:
```text
ci(workflows): add commitlint to CI pipeline

Added commitlint configuration and GitHub Action workflow to enforce 
conventional commit messages. This ensures all commits follow the 
project's commit message format (e.g., type: description) for better
changelog generation and readability.

Installed @commitlint/cli and @commitlint/config-conventional

Created .commitlintrc.json with rules for allowed types (ci,
docs, refactor, revert, test, wip)

Updated .github/workflows/ci.yml to run commitlint on push events

Fixes #123
```
**Note: a blank line is required between body and footer**
 
### Required before merge
- [ ] 1 major change per commit.
- [ ] Changes unrelated to the PR title are absent.
- [ ] Related changes are squashed.
- [ ] Merge commits are absent (use `git rebase`: see below).
  - You will be asked to rebase, if there are conflicts (even trivially resolvable ones).


### 🔧 Using `git rebase` to Remove Merge Commits PRs 🔧

Make sure your local `master` is up to date:

```bash
git checkout master
git pull origin master
```

Switch back to your feature branch:

```bash
git checkout my-feature-branch
```

---

### Step 1: Start an Interactive Rebase Against `master`

This lets you rewrite your feature branch history:

```bash
git rebase -i master
```

This opens a text editor with a list of all your commits since you branched off `master`.  
It might look like this:

```
pick 123abc Add login form
pick 456def Fix validation bug
pick 789ghi Merge branch 'master' into my-feature-branch
pick abc123 Improve login UI
```

---

### Step 2: Remove Merge Commits

Look for any line starting with `pick` and a message like `Merge branch ...`.  
**Delete** those lines entirely from the file.


### Step 3: Squash or Reword Commits

You can change `pick` to:

- `squash` to combine commits together
- `reword` to edit the commit message

Example:

```
pick 123abc Add login form
squash 456def Fix validation bug
reword abc123 Improve login UI
```

When you save and close the file, Git will guide you through combining or renaming commit messages.

---

### Step 4: Resolve Any Conflicts

If you see a message like this:

```
CONFLICT (content): Merge conflict in app.js
```

Do the following:

1. Open the conflicting file and fix the code.
2. Mark it as resolved:

```bash
git add app.js
```

3. Continue the rebase:

```bash
git rebase --continue
```

Repeat until the rebase finishes.

---

### Step 5: Confirm It’s Clean

Once the rebase completes, check your history:

```bash
git log --oneline
```

You should see a clean list of commits with no merge commits.

---

### Step 6: Update the PR Without Force Pushing

If you try to push now, Git will block it because the history changed and **force-pushing is not allowed**. 
Instead, do this:

1. Create a new branch:

```bash
git checkout -b my-feature-clean
git push origin my-feature-clean
```

2. On GitHub, open a new PR from `my-feature-clean` into `master`.

3. Close the original PR (optionally referencing the new one).

---

### 💡 Tips to Avoid Merge Commits in the Future

- Use **rebase instead of merge** when updating your branch:

```bash
git pull --rebase origin master
```

- Only merge into `master` from clean feature branches.

---
