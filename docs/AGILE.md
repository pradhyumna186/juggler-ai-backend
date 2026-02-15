# Agile + GitHub workflow (Juggler.ai)

We build Juggler.ai in short iterations, with **GitHub as the single source of truth** for backlog, code, and collaboration.

## Principles we follow

- **Working software often** — Ship small, shippable increments (e.g. one endpoint, one integration).
- **Backlog in GitHub** — All work is an Issue (task, bug, or spike). Prioritize with labels and milestones.
- **Branches and PRs** — Work on feature branches; merge via Pull Requests after review (or self-review for solo).
- **Transparency** — README, docs, and issues stay up to date so anyone can see what’s done and what’s next.

## How we use GitHub

| Use case | How |
|----------|-----|
| **Backlog** | [GitHub Issues](https://github.com/yourusername/juggler-ai-backend/issues) — use **Task** and **Bug** templates. |
| **Sprints / phases** | [Milestones](https://github.com/yourusername/juggler-ai-backend/milestones) (e.g. “Config & API stubs”, “Google Tasks”, “Juggle logic”). |
| **In progress** | Assign issues, use a **GitHub Project** board (To Do / In Progress / Done) if you want a kanban view. |
| **Code** | Feature branches → PR → merge to `main`. Keep `main` buildable and deployable. |
| **Releases** | Tag versions (e.g. `v0.1.0`) when you have a usable increment. |

## Suggested workflow

1. **Pick an issue** from the backlog (or create one from the roadmap).
2. **Create a branch**: `git checkout -b feature/short-description` or `fix/bug-description`.
3. **Implement**, commit often with clear messages (e.g. “Add buffer config properties”).
4. **Open a PR** against `main`; fill the PR template and link the issue (`closes #12`).
5. **Merge** after review (or self-review); delete the branch. Close the issue.
6. **Repeat** — next iteration, next issue.

## Branch naming

- `feature/<name>` — New capability (e.g. `feature/schedule-complete-endpoint`).
- `fix/<name>` — Bug fix.
- `chore/<name>` — Config, deps, docs (e.g. `chore/add-issue-templates`).

## Getting started

1. Create the repository on GitHub (if you haven’t): **New repository** → name e.g. `juggler-ai-backend` → don’t add a README (we have one).
2. Add the remote and push:
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/juggler-ai-backend.git
   git branch -M main
   git push -u origin main
   ```
3. Create initial backlog issues from the roadmap (config, API stubs, Google Tasks, juggle logic, Gemini). See the project README for the “where to start” order.
4. Optionally create a **Milestone** for the first iteration and assign issues to it.
5. For **Milestones** and **linking the repo to the Project** board, see [MILESTONES-AND-PROJECT.md](MILESTONES-AND-PROJECT.md).

Once this is in place, we’ll use **Issues for scope** and **PRs for code** on every change.
