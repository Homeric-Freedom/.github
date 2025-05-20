# Security Policy

## Supported Versions
| Version | Supported          |
|---------|--------------------|
| master  | ✔️ |

## Reporting a Vulnerability
If you believe you’ve found a security issue, **please do not open an issue or pull-request**.  
Instead, email **eumaios1212@proton.me** or create a
[private security advisory](../../security/advisories/new).

## Collaboration Guidelines
To maintain a clean and reliable commit history in this repository, please adhere to the following guidelines:
* Committing directly to the repository: Prohibited. Pushing directly to any branch is not allowed under any circumstances.
* Development: branches should be hosted on your personal fork and only be submitted to the upstream repository using a pull request.
* Squashing: All commits on pull requests must be squashed into a single meaningful commit before being eligible for merge. Do not combine unrelated changes—you may keep separate commits during WIP stages. Use `git rebase -i` (not `git merge`) to reorder, squash, and clearly label commits before merging.
 
Failure to follow these guidelines may result in delayed or rejected merges. For questions, contact [Eumaios1212](mailto:eumaios1212@proton.me).

## CI/CD Hardening Summary
* Workflows run with a **read-only `GITHUB_TOKEN`** by default.  
* Only actions from **`Homeric-Freedom`**, GitHub-authored, or *verified* Marketplace publishers are allowed.  
* The `master` branch is protected: **2 approvals required** and **@eumaios1212** must be one of them.  
* Dependabot PRs target `master` **every Friday** and must pass the same review gate.

---

