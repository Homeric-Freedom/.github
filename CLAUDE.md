# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a special `.github` organization repository for **Homeric-Freedom**. GitHub automatically inherits files from this `.github/` directory to all repositories in the organization that don't have their own version of these files.

## Repository Structure

```text
.github/
├── workflows/
│   ├── ci.yml              # Universal CI that auto-detects Node/Java/Go/Python
│   └── commitlint.yml      # Validates commit message format on PRs
├── workflow-templates/     # Templates available to other repos
├── PULL_REQUEST_TEMPLATE.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
├── CODEOWNERS              # @eumaios1212 reviews all PRs
└── dependabot.yml          # Weekly dependency updates for multiple ecosystems
```

## Commit Message Format

All commits MUST follow Conventional Commit format:

```text
<type>: <description of change>

<body>

<footer(s): linked to GH Issue(s)>
```

For breaking changes, add `!` after the type:
```text
<type>!: <description of breaking change>
```

### Valid Types
- **ci:** Changes to CI configuration, scripts, or workflows
- **docs:** Documentation updates (README, API docs, code comments)
- **feat:** New feature or significant enhancement
- **refactor:** Code structure improvements without functionality changes
- **revert:** Reverts a previous commit
- **test:** Test additions or modifications

### Footer Format
- `Resolves #<issue-number>` – Closes the issue when merged
- `Refs #<issue-number>` – References an issue without closing it

### Important Rules
- **`!` after the type** indicates a breaking change (e.g., `feat!: remove deprecated API`)
- A blank line is required between body and footer
- Keep description ≤ 72 characters
- Use imperative mood (e.g., "Add rate-limiting middleware")

## PR Requirements

Before a PR can be merged:
1. **One logical change per commit**
2. **Squash related changes** (target: 1 commit per PR)
3. **No merge commits**
4. **No changes unrelated to PR title**
5. **Issue linked in footer** (Resolves #N or Refs #N)
6. **All CI tests pass** (commitlint + ci.yml)
7. **Conflicts resolved via rebase:**
   ```bash
   git pull --rebase origin dev
   git rebase --continue  # if conflicts
   git push -f origin <feature_branch>
   ```

## Branch Strategy

- **master:** Main branch for production/releases
- **dev:** Active development branch
- Create PR branches from updated `dev` branch
- Always rebase before pushing

## Workflows

### ci.yml (Universal CI)
Auto-detects project type and runs appropriate tests:
- Checks for `package.json` (Node), `go.mod` (Go), `pom.xml`/`build.gradle` (Java), or Python files
- Includes dependency caching for performance
- Runs language-specific tests + shellcheck for shell scripts
- Triggers on: PRs and pushes to master/dev

### commitlint.yml
Validates all commit messages in PRs against Conventional Commit format using `@commitlint/config-conventional`.

## Code Ownership

All files require approval from @eumaios1212 (see CODEOWNERS).

## Security Reporting

**NEVER** open public issues for security vulnerabilities. Email eumaios1212@proton.me with:
- Descriptive subject line
- Optional: Use PGP key from SECURITY.md for encrypted communication
- Acknowledgment within 2 business days
- Initial assessment within 7 days
