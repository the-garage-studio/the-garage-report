# Contributing Guidelines — The Garage

Welcome to **The Garage**.

This document defines the development workflow, commit conventions, and collaboration rules.

---

# Branching Strategy

This repository follows **Trunk-Based Development**.

As the central documentation and coordination repository for **The Garage**, it focuses on project planning, architecture, documentation, and organizational resources. Therefore, a lightweight branching strategy is preferred.

Software repositories within the organization (backend, frontend, infrastructure) may adopt **Git Flow** to support feature development, release management, and long-term maintenance.

## Main Branch

* `main` → Default and stable branch.
* Short-lived branches → Created for each task (`docs/*`, `chore/*`, `refactor/*`, etc.).

Every change must be submitted through a Pull Request.

Direct commits to `main` are discouraged.


---

# Branch Naming

Use short, descriptive branch names according to the type of work being performed.

Examples:

```text
docs/readme
docs/contributing-guidelines
docs/architecture
docs/roadmap

chore/github-templates
chore/repository-settings

refactor/document-structure

fix/broken-links
```

Software repositories may define additional branch prefixes (`feature/*`, `release/*`, `hotfix/*`) according to their adopted Git workflow.

---

# Development Workflow

## 1. Update the local repository

Before starting any task, ensure your local `main` branch is up to date.

```bash
git checkout main
git pull origin main
```

## 2. Create a short-lived branch

Create a new branch that clearly describes the task being performed.

Examples:

```bash
git checkout -b docs/contributing-guidelines
```

```bash
git checkout -b docs/readme
```

```bash
git checkout -b chore/github-templates
```

## 3. Implement the changes

Keep each branch focused on a single task or logical change.

## 4. Examples of commits

Follow the Conventional Commits specification.

Examples:

```bash
git commit -m "docs: add contributing guidelines"
```

```bash
git commit -m "chore: add GitHub issue templates"
```

```bash
git commit -m "fix: correct broken documentation links"
```

## 5. Push the branch

```bash
git push -u origin <branch-name>
```

Example:

```bash
git push -u origin docs/contributing-guidelines
```

## 6. Open a Pull Request

Create a Pull Request targeting the `main` branch.

Before merging:

* Review your own changes.
* Ensure the branch is up to date with `main`.
* Resolve merge conflicts, if any.
* Keep Pull Requests focused and easy to review.

## 7. Merge and clean up

Once the Pull Request has been approved and merged:

* Delete the remote branch.
* Delete the local branch.
* Return to the `main` branch before starting a new task.


---

# Commit Convention

We follow the Conventional Commits specification.

| Type     | Description                                |
| -------- | ------------------------------------------ |
| feat     | New feature                                |
| fix      | Bug fix                                    |
| docs     | Documentation                              |
| refactor | Code improvements without behavior changes |
| test     | Tests                                      |
| chore    | Maintenance tasks                          |
| ci       | CI/CD changes                              |
| build    | Build system or dependencies               |
| perf     | Performance improvements                   |
| style    | Formatting only                            |

Examples:

```
feat(api): add user registration

fix(auth): validate expired tokens

docs: update installation guide

refactor(database): simplify repository layer

test(api): add authentication tests

ci: configure GitHub Actions

build: update Docker image

chore: reorganize project structure
```

---

# Pull Requests

Each Pull Request should:

* Solve a single problem.
* Include a clear description.
* Reference related Issues when applicable.
* Pass all automated checks.

---

# Definition of Done

A task is considered complete when:

* Code compiles.
* Tests pass.
* Documentation is updated (if needed).
* Changes have been reviewed.
* No merge conflicts exist.

---

# Best Practices

* Keep commits small.
* Write meaningful commit messages.
* Avoid unrelated changes in the same PR.
* Prefer readability over cleverness.
* Document architectural decisions.


