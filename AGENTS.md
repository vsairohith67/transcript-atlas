# AGENTS.md — Transcript Atlas

## Mission
Build Transcript Atlas V1 as a private/local-first feasibility prototype for public YouTube transcript retrieval, REST API access, MCP access, caching, exports, and reference benchmarking.

## Non-negotiable scope
V1 includes only the transcript/API/MCP feasibility layer. Do not implement public SaaS billing, multi-tenant accounts, Notion ingestion, AI summaries, embeddings, fine-tuning, proxy rotation, or restricted-content access.

## Clean-room rule
Use publicly documented external behavior only as a compatibility reference. Do not copy proprietary source code, branding, protected visual assets, or documentation wording. Implement everything independently.

## Development workflow
1. Plan before coding.
2. Keep `docs/PRODUCT_SPEC.md`, `docs/V1_SCOPE.md`, `docs/PARITY_MATRIX.md`, `docs/ARCHITECTURE.md`, `docs/API_CONTRACT.md`, `docs/MCP_DESIGN.md`, `docs/PROVIDER_DESIGN.md`, `docs/SECURITY.md`, `docs/TEST_STRATEGY.md`, `docs/BENCHMARK_PLAN.md`, `docs/DECISIONS.md`, and `docs/STATUS.md` synchronized.
3. Implement one bounded V1 goal after the plan is reviewed.
4. Run automated tests before claiming completion.
5. Benchmark before discussing Version 2.
6. Final V1 decision must be one of: `PROCEED`, `KEEP LOCAL`, `INVESTIGATE`, `STOP`.

## Security
- Never commit secrets, API keys, cookies, access tokens, or private credentials.
- Keep `.env` files untracked.
- Bind local services to localhost by default.
- Redact secrets from logs.
- Reject unsupported/restricted-content workflows instead of attempting bypasses.

## Engineering preferences
- Prefer simple, testable local architecture over premature scale.
- Use provider interfaces so upstream caption/metadata providers can be replaced.
- Cache successful normalized transcripts.
- Make retries bounded and observable.
- Keep REST and MCP backed by the same service layer.
- Preserve source video ID, language, transcript type, segments, timestamps, provider, retrieval time, and content hash.

## Proposed stack
Plan and validate before implementation:
- Next.js + TypeScript: local web UI
- Python + FastAPI: API/orchestration
- Official Python MCP SDK: MCP transports
- SQLite + local files: V1 persistence/cache
- Docker Compose: local packaging
- Pytest + Playwright: testing

## Public repository hygiene
This repository is public. Treat every committed byte as publicly visible. Never place real credentials or private data in examples, fixtures, issues, logs, screenshots, or documentation.
