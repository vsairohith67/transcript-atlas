# Codex Workflow

## Why this project uses Plan → Goal
Transcript Atlas has one high-risk technical unknown: reliable transcript acquisition. We therefore avoid both hundreds of tiny prompts and one unbounded build request.

## Step 1 — Plan Mode
Codex should inspect this repository, review the authoritative project documents, research public reference behaviour, and create/update:

- `docs/PRODUCT_SPEC.md`
- `docs/PARITY_MATRIX.md`
- `docs/USER_JOURNEYS.md`
- `docs/ARCHITECTURE.md`
- `docs/API_CONTRACT.md`
- `docs/MCP_DESIGN.md`
- `docs/PROVIDER_DESIGN.md`
- `docs/DATA_MODEL.md`
- `docs/CACHE_DESIGN.md`
- `docs/SECURITY.md`
- `docs/LEGAL_AND_POLICY_RISK.md`
- `docs/TEST_STRATEGY.md`
- `docs/BENCHMARK_PLAN.md`
- `docs/IMPLEMENTATION_PLAN.md`
- `docs/DECISIONS.md`
- `docs/GOAL_V1.md`

Plan Mode must not implement application code.

## Step 2 — Review gate
Review the plan for:
- correct V1 boundary;
- provider replaceability;
- public-repo security;
- testability;
- legal/policy boundaries;
- benchmark design;
- no accidental V2 scope.

## Step 3 — Goal Mode
Only after approval, execute the single bounded V1 goal in `docs/GOAL_V1.md`. Codex may internally work through milestones, tests and commits without requiring one user prompt per milestone.

## Step 4 — Benchmark gate
Compare Transcript Atlas with the reference service on a representative corpus and record results.

## Step 5 — Decision
Choose: `PROCEED`, `KEEP LOCAL`, `INVESTIGATE`, or `STOP`.
