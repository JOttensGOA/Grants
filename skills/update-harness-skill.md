# Skill: update-harness

Purpose
- Provide a short, repeatable agent workflow for safely updating files under the `docs/harness/` directory and opening a minimal PR.

When to use
- UI/content tweaks to pages in `docs/harness/` (text, links, minor layout changes) that require a preview and small, reviewable PR.

Trigger phrases
- "update harness page"
- "edit harness file and open PR"

Agent workflow (step-by-step)
1. Inspect the target file in `docs/harness/` and the related template in `grant_req_templates/` if content changes affect requirements.
2. Make a minimal, focused change. Keep styling and structure consistent with nearby files.
3. Run the local smoke test to verify render:
```
python3 -m http.server 8000 --directory harness
# open http://localhost:8000 to visually confirm
```
4. Add a descriptive commit message and include a one-line testing note (what you checked locally).
5. Push to a feature branch and open a PR. In the PR description include links to the changed page(s) (path under `harness/`) and the local verification steps.

Example prompt for the skill
"Update the heading and wording on `harness/stage_1_grant_requirements_harness.html` to clarify eligibility — keep layout unchanged. Verify locally and prepare a PR with testing notes."

PR checklist for the agent to populate automatically
- Files changed: list
- Local smoke test run: yes/no
- Screenshots or link to preview: optional (encourage screenshot when UI changes are non-trivial)
- Notes for reviewer: short testing instructions and reasoning

Safety & escalation
- If the change touches `netlify.toml`, CI workflows, or deployment secrets, stop and ask a human before proceeding.
- For content affecting `grant_req_templates/`, prefer human confirmation for wording that changes policy or eligibility criteria.

Usage examples
- Quick edit: change text in `harness/*.html`; run smoke test; open PR.
- Template sync: when updating a template in `grant_req_templates/`, run a grep to find pages that reference it and include that list in PR.

Created: lightweight, actionable skill for harness edits.
