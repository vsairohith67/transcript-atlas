# Transcript Atlas — Codex Plan Mode Master Prompt

PLAN MODE ONLY. DO NOT IMPLEMENT APPLICATION CODE YET.

## Project
**Transcript Atlas** — *Map every word in a video.*

## Objective
Plan Version 1 of a public-repository, local-first, independently implemented YouTube transcript API, web application, cache, export layer and MCP server.

V1 is a feasibility prototype. Its purpose is to determine whether public YouTube caption/transcript acquisition can be reliable enough to justify a later AI knowledge system.

Use `AGENTS.md`, `README.md`, `docs/V1_SCOPE.md`, `docs/STATUS.md`, and `docs/CODEX_WORKFLOW.md` as authoritative project context.

## Clean-room boundary
Use publicly documented behavior of relevant reference products only as a compatibility specification. Do not copy proprietary source code, branding, logos, illustrations, protected assets, site copy, documentation wording, or private implementation details. Do not probe private systems.

## Reference behavior to research
Review current public documentation for TranscriptAPI, including its REST API and MCP capabilities, only to understand externally documented behavior and create our parity matrix.

## Required V1 REST capabilities
Plan independent equivalents of:
1. GET /youtube/transcript
2. GET /youtube/info
3. GET /youtube/search
4. GET /youtube/channel/resolve
5. GET /youtube/channel/search
6. GET /youtube/channel/videos
7. GET /youtube/channel/latest
8. GET /youtube/playlist/videos

For each, capture public inputs, outputs, language behavior, timestamps, metadata, pagination, cache semantics, errors, and unresolved ambiguities in `docs/PARITY_MATRIX.md`.

Our own local base URL should be designed under:
`http://localhost:8000/api/v1`

## MCP V1
Plan these six compatibility-oriented tools:
- get_youtube_transcript
- search_youtube
- get_channel_latest_videos
- search_channel_videos
- list_channel_videos
- list_playlist_videos

Also plan private diagnostics where useful, such as:
- list_transcript_languages
- get_transcript_atlas_status

Support local STDIO MCP and Streamable HTTP MCP, both backed by the same service layer as REST.

## Provider architecture
Design replaceable provider interfaces. Evaluate:
- maintained public-caption libraries for public caption tracks;
- yt-dlp as a reviewed subtitle/metadata fallback where appropriate;
- official YouTube Data API for supported metadata/search functions;
- YouTube RSS for recent uploads where appropriate.

Do not make TranscriptAPI a runtime dependency. It may be used only by a separate benchmark harness as a reference service.

Do not implement:
- private videos;
- members-only or paid content;
- access-control bypasses;
- login-cookie harvesting;
- age/geographic restriction bypasses;
- proxy rotation in V1;
- automatic audio/video downloading for speech-to-text;
- anti-bot bypass mechanisms.

If public captions are unavailable, the system should return a clear structured result/error rather than attempting a restriction bypass.

## V1 product requirements
Plan:
- original local web UI;
- transcript playground;
- search/channel/playlist explorers;
- API documentation page;
- MCP setup page;
- request history;
- cache/system status;
- settings;
- JSON, text, Markdown, SRT and VTT exports where appropriate;
- local cache and transcript archive;
- deterministic normalized data model;
- structured errors and bounded retries;
- safe local bearer-token option;
- localhost binding by default.

## Proposed stack
Evaluate and refine, preferring simplicity:
- Next.js + TypeScript frontend
- Python + FastAPI backend
- official Python MCP SDK
- SQLite
- local filesystem transcript cache
- OpenAPI/Swagger
- Docker Compose
- Pytest
- Playwright
- structured JSON logging
- Windows Docker Desktop / WSL2 support

Do not introduce enterprise infrastructure without a concrete V1 need.

## Public-repository security
The repo is public. Plan strict controls:
- `.env` and secrets never committed;
- no real tokens in fixtures/docs/screenshots;
- no credentials in frontend bundles;
- log redaction;
- URL/input validation;
- SSRF defenses;
- safe subprocess execution;
- dependency scanning;
- response/resource limits;
- safe example credentials only.

## Cache/data requirements
Every normalized transcript record should preserve, where available:
- video ID;
- source URL;
- requested language priority;
- selected language;
- manual/automatic caption status;
- provider used;
- transcript segments;
- start/duration timestamps;
- retrieval timestamp;
- transcript hash;
- metadata;
- provider attempts/errors.

Repeated compatible requests should use local cache.

## Version 2 boundary
Do not implement AI Brain, Notion transcript ingestion, embeddings, fine-tuning, or automatic monitoring in V1.

Reserve only clean interfaces/disabled flags if architecturally useful:
- ENABLE_AI_BRAIN=false
- ENABLE_NOTION_SYNC=false
- ENABLE_EMBEDDINGS=false
- ENABLE_CHANNEL_MONITORING=false

V2 may consume a future `transcript.completed` event without changing V1 acquisition internals.

## Benchmark plan
Design an automated side-by-side benchmark against TranscriptAPI using an optional environment variable such as `TRANSCRIPTAPI_BENCHMARK_KEY`. It must never be needed for ordinary operation.

Design a representative ~30-video corpus covering:
- manual English captions;
- automatic English captions;
- Hindi;
- Telugu or mixed language;
- Shorts;
- podcasts/long interviews;
- livestream replays;
- no-caption/unavailable cases.

Compare:
- success agreement;
- selected language;
- caption type;
- normalized text similarity;
- word/segment counts;
- timestamp deviation;
- metadata completeness;
- uncached latency;
- cached latency;
- error classification.

Initial decision targets to validate/refine:
- all 8 REST contracts tested;
- all 6 parity MCP tools tested;
- at least 90% success where the reference succeeds;
- at least 98% median normalized text similarity when the same track is selected;
- at least 95% correct language selection;
- cached local requests roughly under 250 ms;
- no systemic IP blocking during conservative low-rate testing.

## Required planning documents
Create/update:
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
- `docs/STATUS.md`
- `docs/GOAL_V1.md`

## Planning rules
- Do not implement application code during this Plan Mode task.
- Record assumptions and contradictory public reference behavior instead of guessing.
- Break implementation internally into bounded milestones, but produce one self-contained `GOAL_V1.md` so the user does not need hundreds of prompts.
- Every milestone must have acceptance criteria, tests, documentation/status updates, and rollback guidance.
- Keep V2 blocked.

## Final Plan Mode output
Finish with:
1. architecture recommendation;
2. unresolved risks;
3. external credentials/tools eventually required;
4. benchmark acceptance criteria;
5. complete `docs/GOAL_V1.md`;
6. exact next instruction for Goal Mode.
