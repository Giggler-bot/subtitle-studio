# Subtitle Studio — System Architecture

**Document:** 12 — System Architecture  
**Status:** Proposed target architecture  
**Version:** 0.1

---

## 1. Architectural direction

Start with a modular monolith. Do not introduce microservices before there is a demonstrated operational or scaling need.

## 2. Proposed technology stack

| Layer | Proposed technology | Responsibility |
|---|---|---|
| Web frontend | React / Next.js | User interface and editor |
| Backend API | Python / FastAPI | Application and domain APIs |
| Database | PostgreSQL | Structured data |
| Media processing | FFmpeg | Audio/video inspection and manipulation |
| Background broker | Redis | Job coordination |
| Worker | Celery or evaluated equivalent | Long-running processing |
| Object storage | S3-compatible storage | Media, audio and exports |
| Version control | Git / GitHub | Source history and collaboration |

Technology choices remain subject to implementation needs and provider evaluation.

## 3. First MVP architecture

The first SRT editor can run locally in the browser:

- Browser reads the selected SRT file.
- Frontend parser creates subtitle entries.
- Editor updates local application state.
- Browser video element previews a selected local video.
- Subtitle renderer follows playback time.
- Serializer generates a downloadable SRT file.

No API, database, Redis, Celery or cloud storage is required for this initial workflow.

## 4. Future target architecture

```text
Browser / Next.js
       |
       v
FastAPI modular monolith
       |
       +------ PostgreSQL
       |
       +------ Object storage
       |
       +------ Redis job broker
                    |
                    v
              Background workers
                    |
       +------------+-------------+
       |            |             |
     FFmpeg      AI providers   Rendering
       |       ASR / Translate   / Mixing
       |          / TTS
       +------------+-------------+
                    |
                    v
             Generated assets
```

## 5. Processing architecture

- API requests validate and create jobs.
- Workers execute long-running stages.
- Each stage records status and output references.
- A failed stage can be retried without rerunning unrelated completed stages where safe.
- Provider adapters isolate external AI services.
- Media assets remain private unless explicitly published.

## 6. Modular monolith boundaries

Potential backend modules:
- projects
- media
- subtitles
- library
- transcription
- speakers
- translations
- voices
- dubbing
- jobs
- collaboration
- accounts

Introduce modules when their functionality is required; avoid empty scaffolding.

## 7. Deployment direction

Development can begin locally. Production deployment decisions should consider:
- API hosting.
- Worker hosting.
- PostgreSQL hosting.
- Redis hosting.
- Object storage region and lifecycle rules.
- FFmpeg resource requirements.
- AI provider network access and data policies.
- Monitoring, logging and backups.

## 8. Observability

Track:
- Request latency and errors.
- Job duration and state transitions.
- Provider/model and usage.
- Media duration and file size.
- Worker failures and retries.
- Storage usage.
- Cost per processing stage.

## 9. Open decisions

- Hosting provider.
- S3-compatible storage provider.
- Celery versus another worker system.
- ORM and migration tooling.
- Authentication provider or implementation.
- Deployment topology and environment strategy.
