# <PROJECT_NAME> Skill Authoring Policy

## Purpose
- Keep skills focused, composable, and minimal-context.
- Ensure reproducible quality gates for all skill changes.

## Required Workflow
1. Create/update skill with built-in `skill-creator` and this governance skill.
2. Apply repository checklist before merge.
3. Run validation and trigger tests.
4. Record outcomes in repo session/changelog notes.

## Scope Rules
- One skill should serve one workflow family.
- Avoid one-skill-per-component unless strongly justified.
- Split skills when trigger vocabulary, dependencies, or safety posture diverge.

## SKILL.md Rules
- Keep trigger-oriented and concise.
- Include purpose, trigger conditions, required inputs, expected outputs, and safety notes.
- Move deep procedures into `references/`.

## Validation Gate
- `npm run skills:validate`
- `npm run skills:test-triggers`
- Optional fixture/CI checks if present
