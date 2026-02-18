## Arkiv engineering guidelines

This repository contains **shared guidelines for how we run development and releases across our repositories**. The goal is to keep day-to-day work predictable: consistent branching and PR practices, clear release steps, and a CI/CD flow that teams can adopt and adapt per project.

## What’s inside

- **Git workflow / branching model**: [`git-flow.md`](git-flow.md)  
  How we use `develop` and `main`, how feature/hotfix branches work, and what rules we follow for PRs and merging.

- **CI/CD workflow (PR → production)**: [`ci-cd-flow.md`](ci-cd-flow.md)  
  A recommended pipeline from PR checks through build, review, staging, release, and production deployment.

- **Diagram assets**: [`assets/processes.drawio.png`](assets/processes.drawio.png)  
  Diagram referenced by [`ci-cd-flow.md`](ci-cd-flow.md).

## How to use these guidelines

- [Optional] Link to the relevant documents from each project repo (or copy the parts you need into that repo’s own docs).
- Treat these docs as **defaults**; adjust the details to match the project’s risk profile, environments, and release process.

## Contributing

If you want to improve or extend the workflows, open a PR with:

- a short rationale (why the change helps),
- any trade-offs or project constraints,
- updates to diagrams/docs where applicable.
