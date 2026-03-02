# Agent Creator Workflows

## Workflow A: Create Role from Short Prompt (Default)
1. Determine target scope (`.codex/` or `~/.codex/`).
2. Select template (currently: `artist`).
3. Infer missing fields using defaults; record assumptions.
4. Generate/patch:
   - role registration in config
   - role TOML config
   - instructions block/file
5. Validate config parse (for example `codex features list`).
6. Smoke test role spawn and close.
7. Return report:
   - files changed
   - assumptions
   - validation results
   - residual risks

## Workflow B: Update Existing Role Safely
1. Lock current role behavior notes.
2. Update one dimension at a time:
   - persona/tone
   - permissions/scope
   - delegation
   - quality gates
3. Re-run parse + smoke test.
4. Return diff summary and residual risk.

## Workflow C: Collision and Naming Policy
- Default behavior: update existing role id if present.
- Create new role id only on explicit user request.
- For template-generated role ids, apply template normalization and collision rules.

## Validation Gate (Required)
- Parse check passes.
- Spawn smoke test passes.
- Role-specific sample prompt returns structured handoff format.

## Quality Checklist
- Role id and config path are valid and stable.
- Role has explicit operations contract.
- Role has explicit read/write scope and mutation policy.
- Delegation policy is explicit.
- Handoff schema is present.
- No secrets/environment-private values in instructions.
