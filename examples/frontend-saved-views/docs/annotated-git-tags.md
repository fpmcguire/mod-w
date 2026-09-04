# Annotated Git Tags - Frontend Saved Views

This document describes the git tagging convention used in this pseudo-MOD-W example project to mark the completion of each Moderated AI Development Workflow step.

---

## Convention

Each completed step is tagged at the commit where its accepted artifacts were merged. Tags follow the format:

```text
step/NN-short-title
```

The tag annotation includes:

- Step number and title
- Date completed
- Moderator who accepted the step
- QA role or tester who verified the step
- Summary of what was produced

---

## Tags in This Example

### `step/01-saved-views-list`

```bash
git tag -a step/01-saved-views-list -m "Step 01: Saved Views List (Read-only)

Completed: 2026-01-20
Moderator: Jordan Rivera
QA: Sam Okafor

Produced:
- src/components/SavedViewsList.tsx
- src/components/Dashboard.tsx
- src/state/savedViews.ts
- src/tests/SavedViewsList.test.tsx
- src/tests/Dashboard.test.tsx

All Level 2 quality gate criteria met for the frontend-only read-only Step 01 scope.
See examples/frontend-saved-views/mod-w/review.md and examples/frontend-saved-views/mod-w/qa.md for details."
```

---

## Why Tag Steps?

Annotated git tags serve several purposes in a Moderated AI Development Workflow project:

1. **Traceability** - Any commit can be related back to the Moderated AI Development Workflow step that produced it.
2. **Rollback points** - If a later step introduces a regression, the team can quickly identify the last known-good step boundary.
3. **Audit trail** - The tag annotation records who moderated and accepted the step, providing a permanent record alongside the code.
4. **Team communication** - Tags make progress visible to anyone browsing the repository, without needing to read every commit message.

---

## Creating Tags

After a step is accepted (`mod-w/review.md` decision = Accept) and QA passes (`mod-w/qa.md` result = Pass):

```bash
git tag -a step/NN-short-title -m "$(cat <<'EOF'
Step NN: Full Step Title

Completed: YYYY-MM-DD
Moderator: Name
QA: Name

Produced:
- path/to/file1
- path/to/file2

[Quality gate level and summary]
EOF
)"

git push origin step/NN-short-title
```

---

MOD-W v5 - Moderated AI Development Workflow - https://github.com/fpmcguire/mod-w
