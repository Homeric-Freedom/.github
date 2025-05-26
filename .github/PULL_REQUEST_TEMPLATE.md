<!-- .github/PULL_REQUEST_TEMPLATE.md -->
### 📋 Summary
Explain *WHAT* this PR does and *WHY*

### ✅ Checklist
- [ ] Commit messages have a subject line that describes the patch, with an optional longer body that gives details, 
  documentation, etc., following this format:
```
<subdirectory under core, else parent dir where changes were made>: <description of change>

[optional body]

[optional footer(s)]
```
Example: `controller: fixed callback error`

### Required before merge
- [ ] 1 major change per commit.
- [ ] Related changes are squashed.
- [ ] merge commits or changes unrelated to the PR title are absent.
  - You may be asked to rebase if there are conflicts (even trivially resolvable ones).
  - CI must pass
