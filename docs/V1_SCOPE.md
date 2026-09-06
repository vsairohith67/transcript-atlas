# Transcript Atlas — Version 1 Scope

## Objective
Prove whether a clean-room, local-first transcript engine can reliably retrieve and organize public YouTube captions, expose them through REST and MCP, and match a reference service closely enough to justify further development.

## V1 must include

### REST capabilities
1. `/youtube/transcript`
2. `/youtube/info`
3. `/youtube/search`
4. `/youtube/channel/resolve`
5. `/youtube/channel/search`
6. `/youtube/channel/videos`
7. `/youtube/channel/latest`
8. `/youtube/playlist/videos`

### MCP capabilities
1. `get_youtube_transcript`
2. `search_youtube`
3. `get_channel_latest_videos`
4. `search_channel_videos`
5. `list_channel_videos`
6. `list_playlist_videos`

Private diagnostic tools may include transcript-language inspection and system status.

### Local product
- Original local web UI
- FastAPI REST API
- STDIO MCP
- Streamable HTTP MCP
- SQLite/local-file cache
- JSON, text, Markdown, SRT and VTT exports where appropriate
- Docker Compose startup
- Request/error history
- Automated tests
- Reference benchmark

## V1 must not include
- Public SaaS accounts or payments
- AI summaries
- Notion transcript ingestion
- Embeddings/vector database
- Fine-tuning
- Automatic channel monitoring
- Proxy-rotation infrastructure
- Access-control/restriction bypasses
- Private, paid, members-only or otherwise restricted-content acquisition
- Automatic audio/video downloading for speech recognition

## Provider architecture
Use replaceable interfaces. Initial implementation candidates may include reviewed public-caption libraries, subtitle/metadata fallbacks, official YouTube APIs where appropriate, and RSS for recent uploads. No single upstream implementation should be hard-wired into the public service layer.

## V1 decision gate
After tests and a representative benchmark, issue exactly one decision:

- **PROCEED** — reliability is strong enough to build V2.
- **KEEP LOCAL** — useful locally, but hosting/distribution introduces unacceptable reliability constraints.
- **INVESTIGATE** — promising but one or more provider/reliability gaps require focused research.
- **STOP** — core transcript acquisition is not reliable enough to justify further work.
