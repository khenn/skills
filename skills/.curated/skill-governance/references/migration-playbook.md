# Skill Governance Migration Playbook

## Goal
Move skill-quality enforcement into a reusable Codex skill package while preserving existing behavior.

## Phases
1. Create `skills/skill-governance` with templates + scripts.
2. Repoint repo scripts to skill-owned scripts.
3. Keep compatibility wrappers only if needed.
4. Re-run validators and trigger tests.
5. Update roadmap/session notes with migration outcome.

## Verification
- Scaffold command works.
- Validator passes valid fixtures and fails invalid fixtures.
- Trigger tests pass.
- CI workflow remains green.
