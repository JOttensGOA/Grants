# GitHub Copilot Instructions — Grants

Purpose: Short, GitHub-focused guidance for AI agents operating on PRs and repository changes.

Quick links
- Repository overview: [README.md](../README.md)
- Agent guidance: [AGENTS.md](../AGENTS.md)

Behavior guidelines
- Small, focused PRs: prefer minimal, reversible changes. Describe intent in the PR title.
- Link rather than copy: reference existing docs and templates instead of duplicating them.
- Preserve UX: when editing `harness/` files, verify changes render with the local smoke test below.

Verification
- Local smoke test (run before opening PR):
```
python3 -m http.server 8000 --directory harness
# then open http://localhost:8000
```
- If you modify deployment-related files (`netlify.toml`, CI workflow), include a brief note about required secrets (`NETLIFY_AUTH_TOKEN`, `NETLIFY_SITE_ID`).

Commit & PR expectations
- Use descriptive commit messages and include a brief testing note (what you ran to verify).
- Add files to the PR description that an engineer should review (e.g., links to changed harness pages, screenshots if UI changed).

When to ask the human
- If a change affects deployment, production content, or user-facing wording in `grant_req_templates/`, request confirmation before merging.

Created to complement AGENTS.md with GitHub/PR-specific practices.
