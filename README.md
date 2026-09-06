# Transcript Atlas

**Map every word in a video.**

Transcript Atlas is a clean-room, local-first feasibility project for retrieving **public YouTube captions/transcripts and metadata**, exposing them through an original web UI, REST API, and MCP server for tools such as Codex and ChatGPT.

## Current stage

**V1 planning / repository setup. Application implementation has not started yet.**

The first goal is not to build a public SaaS. It is to answer one engineering question:

> Can an independently implemented transcript engine retrieve and organize public YouTube captions reliably enough to justify building a larger AI knowledge system on top of it?

## Version 1 target

V1 will aim to provide compatibility-oriented equivalents for:

- Video transcript retrieval
- Video information and caption-language discovery
- YouTube search
- Channel resolution
- Search within a channel
- Paginated channel uploads
- Latest channel uploads
- Paginated playlist videos
- Six core MCP tools for transcript/search/channel/playlist access
- Local caching and exports
- Original local web UI
- Docker-based local startup
- Automated benchmark against TranscriptAPI as a reference service

## Deliberately excluded from V1

- Public SaaS accounts or billing
- Notion transcript ingestion
- AI summaries
- Embeddings/RAG
- Fine-tuning
- Proxy rotation
- Restricted/private/members-only content access
- Automatic audio/video downloading for speech recognition

These remain future work only if V1 passes the reliability benchmark.

## Development method

We use **Codex Plan Mode → review gate → bounded Goal Mode → benchmark → go/no-go decision** instead of hundreds of small prompts.

See `AGENTS.md` and `docs/` for the project source of truth.

## Status

- Product name: **Transcript Atlas**
- Repository: `vsairohith67/transcript-atlas`
- Visibility: public
- V1 status: planning
- AI Brain / Notion V2: blocked until V1 decision

## Safety and clean-room boundary

Transcript Atlas is independently implemented. Public product behavior may be studied as a compatibility target, but proprietary source code, branding, protected assets, documentation wording, and private implementation details must not be copied.

V1 supports only public content and must not implement mechanisms intended to bypass access controls or restrictions.
