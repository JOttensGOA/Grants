# AGENTS.md — AI coding agent guidance

Purpose: Give succinct, actionable guidance to AI coding agents working in this repository.

Source of truth
- Primary: the repository files (this repo's root and subfolders). Use the files under `harness/`, `docs/`, and `grant_req_templates/` as canonical sources for UI and requirement content.
- Deployment: see [README.md](README.md) for Netlify deployment and local smoke-test commands.

Quick commands
- Local smoke test: `python3 -m http.server 8000 --directory harness`
- Publish: pushes to `main` trigger GitHub Actions to deploy `docs/` to Netlify (see `netlify.toml`).

Key files and directories
- [docs/](docs/) — static site exported to Netlify and GitHub Pages; primary UI harness files.
- [docs/](docs/) — documentation and static pages used by the project.
- [grant_req_templates/](grant_req_templates/) — templates and canonical requirement definitions.
- `netlify.toml` — Netlify publish config (publishes from `harness`).

Conventions & expectations for agents
- Link, don't copy: when referring to longer docs, link to the file in-repo instead of duplicating content.
- Preserve existing documentation: update only to correct or clarify; do not remove historical context without clear reason.
- Minimal edits by default: prefer small, focused PRs that preserve repo style.
- When adding or changing runnable code, include a minimal test or a local verification step and update `README.md` or `AGENTS.md` with the run instructions.

When in doubt
- Ask the user for clarification before making large changes (e.g., changing deployment flow, rewriting documentation). Point them to this file for agent behaviour expectations.

Next suggested customizations
- Add a `.github/copilot-instructions.md` with repo-specific linting or PR expectations if you want GitHub-specific guidance.
- Create small agent skills for common tasks like "update harness page" or "add new grant template" linking tests and run commands.

Created: AGENTS.md — concise guidance linking to repository sources.
