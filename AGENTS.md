# AGENTS.md

## Scope
- These instructions apply to the entire repository unless a deeper `AGENTS.md` overrides them.

## Repository Overview
- This repository aggregates `techcv-*` repositories as Git submodules.
- Top-level files should mainly document and manage the submodule layout.
- Source code for each product lives inside its own submodule and keeps its own conventions.

## Working Rules
- Make focused, minimal changes that match the user request.
- Avoid introducing top-level tools, frameworks, or extra structure unless the user asks for them.
- Prefer adding each `techcv-*` repository as a Git submodule at the repository root.
- Keep submodule directory names aligned with repository names unless the user requests otherwise.
- Update `README.md` when a change affects setup, usage, or repository structure.

## Local Codex Skills
- Project-local Codex skills live under `.codex/skills`.
- When a task clearly matches a local skill, read that skill's `SKILL.md` and follow it for that turn.
- Use `go-best-practices` when reading, reviewing, refactoring, or writing `.go` files or `go.mod`.
- Keep local skills small and task-focused. Prefer repository-specific guidance over generic boilerplate.
- Do not move local skills into submodules unless the user explicitly asks for that layout.

## Style
- Follow existing naming and formatting patterns when they exist.
- Prefer straightforward implementations over clever abstractions.
- Do not add boilerplate comments or license headers unless explicitly requested.

## Validation
- Validate changes with the smallest relevant check available.
- If no runnable checks exist yet, state that clearly in the handoff instead of inventing process.

## Notes for Future Contributors
- Do not modify files inside a submodule unless the user explicitly asks for work in that submodule.
- Add more specific `AGENTS.md` files only when repository-level rules are no longer enough.
