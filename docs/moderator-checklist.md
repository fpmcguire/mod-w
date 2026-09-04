# Moderator Checklist – MOD-W

Use this checklist for every Step in the MOD-W workflow.

---

## 1. Before Engaging AI

- [ ] `roadmap.md`: next Step chosen and clearly named.
- [ ] `step-xx.md`: goal, scope, inputs, required changes, acceptance checks, and risks filled in.
- [ ] `domain-language.md`: key terms for this Step defined or updated.
- [ ] `product.md` / `architecture.md`: still accurate for this Step.
- [ ] `CLAUDE.md` and `AGENTS.md`: current at repo root (regenerate via Tech Lead if `architecture.md` has changed).
- [ ] `.codex/config.toml`, `.claude/settings.json`, and `.mcp.json`: present and valid at repo root.

---

## 2. Tech Lead Planning Session (Codex)

Trigger a Tech Lead Planning Session when starting a new project phase or when `architecture.md`, `roadmap.md`, or `step-xx.md` needs to be generated or updated.

- [ ] Open a Codex session — `AGENTS.md` loads automatically.
- [ ] Provide `product.md` and existing `architecture.md` (if present).
- [ ] Ask Tech Lead to generate or update:
  - `architecture.md`
  - `domain-language.md`
  - `roadmap.md`
  - `step-xx.md` for the current Step
  - `CLAUDE.md` and `AGENTS.md` (from `architecture.md` and the MOD-W templates)
  - `cross-validation.md`, `.codex/config.toml`, `.claude/settings.json`, and `.mcp.json` when missing or stale
- [ ] Review all artifacts and iterate until Moderator-approved.
- [ ] Confirm `CLAUDE.md`, `AGENTS.md`, and root tool config files are committed before briefing the Development Team.

---

## 3. Brief the Development Team (Claude Code)

- [ ] Open a Claude Code session in the project root — `CLAUDE.md` loads automatically.
- [ ] State the active Step at session start, e.g.: `The current Step is STEP-02.md`
- [ ] Ask the Development Team to restate the goal and scope in their own words.
- [ ] Confirm the restatement is correct before proceeding. Correct any misunderstandings now.

---

## 4. Implementation Options Gate

- [ ] Development Team enters Plan Mode: reads relevant files, proposes implementation plan. No files written yet.
- [ ] Review the proposed plan.
- [ ] Optionally request:
  - `options` — 2–3 implementation paths with trade-offs and a recommendation
  - `ramifications` — technical debt risks, side effects, and likely pain points
- [ ] Approve the plan explicitly before any code is written.
- [ ] If the plan reveals scope or architectural concerns, pause and return to the Tech Lead before proceeding.

---

## 5. Implementation and Build Gate

Claude Code edits files directly in the repo — no pull or paste required.

- [ ] Monitor progress and respond to any clarifying questions from the Development Team.
- [ ] After implementation, confirm the Development Team has run and passed the build gate:
  - `{{BUILD_COMMAND}}`
  - `{{TEST_COMMAND}}`
- [ ] Review the diff in the Workbench (VS Code). The diff is the source of truth, not the summary.

If issues are significant:

- [ ] Summarize problems clearly.
- [ ] Return feedback to the Development Team and repeat until acceptance checks are met.

---

## 6. QA + Product Owner SubAgents

The Development Team spawns these automatically after the build gate passes.

- [ ] Review `qa.md` produced by the QA SubAgent:
  - acceptance check outcomes
  - manual checks requiring human or browser verification
  - known limitations
- [ ] Review the Product Owner SubAgent sign-off.
- [ ] Perform any manual checks flagged by the QA SubAgent (UX, visual, edge cases) in the Workbench.
- [ ] If acceptance checks are not met, return findings to the Development Team.

---

## 7. Tech Lead Review Session (Codex)

- [ ] Open a Codex Review Session — `AGENTS.md` loads automatically.
- [ ] Ask the Tech Lead to review the implementation against the active `step-xx.md`.
- [ ] Codex reads the changed files and `qa.md` directly — no handoff packet required.
- [ ] Review `review.md` findings:
  - **Must-fix** items return to the Development Team.
  - **Could-fix-later** items are logged for a future Step.
- [ ] Repeat the Development Team → Build Gate → QA → Tech Lead loop until all must-fix items are resolved.

---

## 8. Tag and Advance

- [ ] Confirm all acceptance checks pass.
- [ ] Confirm `review.md` and `qa.md` are complete.
- [ ] Create an **annotated Git tag** for the Step, including:
  - Step identifier (e.g., `step-01-saved-views-list`)
  - Short description
  - References to `step-xx.md`, `review.md`, `qa.md`
  - Notable decisions or caveats
- [ ] Push the tag to the remote repository.
- [ ] Update `product.md` if behaviour or UX changed meaningfully.
- [ ] Update `architecture.md` if design decisions changed.
- [ ] Update `roadmap.md` to mark the Step complete and adjust future Steps if needed.
- [ ] If `architecture.md` was updated, ask the Tech Lead to regenerate `CLAUDE.md` for the next Step.
- [ ] Select the next Step from `roadmap.md` and return to section 1.

---

This checklist should be lightweight enough to use for every Step but strict enough to preserve MOD-W's multi-layer validation and traceability.

---

MOD-W v5.0.0 · Moderated AI Development Workflow · https://github.com/fpmcguire/mod-w
