# Agent Creator Workflows

## Workflow A: Create Role from Short Prompt (Default)
1. Determine target scope (`.codex/` or `~/.codex/`).
2. Select template (currently: `artist`).
3. Infer missing fields using defaults; record assumptions.
4. Generate/patch:
   - role registration in config
   - role TOML config
   - instructions block/file
5. Enforce TOML compatibility:
   - only known top-level keys
   - put policy constraints in `developer_instructions` unless runtime key support is explicit
6. Validate config parse (for example `codex features list`).
7. Detect runtime role-spawn capability:
   - if dynamic role spawn is supported, run spawn + close smoke test
   - if not supported, mark spawn as manual verification required
8. Return report:
   - files changed
   - assumptions
   - validation results
   - residual risks
   - manual verification steps (if capability gap exists)
   - validation matrix (`parse_check`, `spawn_check`, `format_check`, `policy_check`)
   - capability-scoped verification summary

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
- Spawn smoke test passes, or is explicitly marked manual-only due to runtime/tool capability.
- Role-specific sample prompt returns structured handoff format.
- Report includes required Assumption Warning Block when any manual verification remains.
- Verdict aligns with reported failure triggers and allowed verdict enum.

## Quality Checklist
- Role id and config path are valid and stable.
- Role has explicit operations contract.
- Role has explicit read/write scope and mutation policy.
- Delegation policy is explicit.
- Handoff schema is present.
- No secrets/environment-private values in instructions.
- No unrecognized top-level TOML keys are emitted.
- Runtime dynamic-role spawn capability is checked and reported.
- Assumption Warning Block is present when capability constraints prevent full automation.
- Validation matrix is present in final report.
