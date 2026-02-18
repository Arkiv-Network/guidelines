# Gitflow

We follow the **Gitflow** branching model to keep development, reviews, and releases predictable and consistent.

Reference documentation:
[https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

## Branches and their purpose

- **`develop`**: default integration branch for day-to-day work.
  - Set `develop` as the default branch in the GitHub repository settings.
- **`main`**: release/production branch.
  - Updates to `main` happen as part of the release process (and should be protected).
- **Developer branches**: short-lived branches created from `develop` (e.g. `feature/*`, `bugfix/*`).
- **Hotfix branches**: created from `main` only for urgent production issues (e.g. `hotfix/*`).

## Branching and merging rules

- **Branch from `develop`** for normal development work (features, bug fixes, refactors, etc.).
- **Open a Pull Request back into `develop`** for every change. No direct merges into `develop`.
- **Rebase on top of `develop` before merging** (or before final review), and resolve conflicts in your branch.  
  - This keeps the commit history **flat and readable**, and makes it easier to understand what changed in a single PR/merge (a clean, linear sequence of commits that belongs to one integration into `develop`).
- **Keep `develop` always mergeable into `main`** (i.e., after changes land in `develop`, merging `develop` → `main` should not require conflict resolution).

## Pull Request requirements

- **Every PR must reference a GitHub issue** using standard closing keywords in the PR description, for example:
  - `closes #<issue-number>`
  - `fixes #<issue-number>`
- **The referenced issue should live in the same repository** as the PR.
  - If a task spans multiple repositories, create **a tracking issue (sub-task) in each repository** and reference the appropriate issue from each PR.

## When a PR can be merged

A PR can be merged only when:

- **Review is completed** (when more than one developer is active on the project)
- **All CI checks are green**

Best practice: enforce the above using **GitHub branch protection rules**.

## Standard flow

```
developer branch → develop → main
```

## Hotfixes (exceptional cases)

The reverse direction (`main` → `develop`) is reserved only for exceptional cases, such as urgent production issues.

1. Create a **hotfix** branch from `main`
2. Merge it directly into `main`
3. Sync the fix back into `develop` as soon as possible (via PR)

## Notes

We should follow these rules by default, but not rigidly. There are valid exceptions, for example:

- A colleague is on holiday and no one else can review
- Single-person projects, where review does not make sense
- Depending on the project and its environments, sometimes the default branch can be `main` instead of `develop`  
  - Example: a demo dashboard with no staging/testing environment, where changes go directly to production and the project has low impact
