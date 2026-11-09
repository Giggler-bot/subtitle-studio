# Subtitle Studio — API Design

**Document:** 11 — API Design  
**Status:** Draft conventions and proposed routes  
**Version:** 0.1

---

## 1. Purpose

Establish API conventions for the future FastAPI backend. The first browser-local SRT editor MVP does not require these endpoints.

## 2. API principles

- Version public APIs, initially under `/api/v1`.
- Use resource-oriented routes.
- Validate request and response schemas.
- Use consistent error response structures.
- Keep long-running processing asynchronous.
- Return job identifiers and expose job status.
- Apply authentication and authorization when user/project persistence is introduced.
- Do not expose private object-storage paths.

## 3. Proposed route groups

### Health
- `GET /api/v1/health`

### Projects
- `POST /api/v1/projects`
- `GET /api/v1/projects`
- `GET /api/v1/projects/{project_id}`
- `PATCH /api/v1/projects/{project_id}`
- `DELETE /api/v1/projects/{project_id}`

### Media
- `POST /api/v1/projects/{project_id}/media`
- `GET /api/v1/media/{media_id}`
- `DELETE /api/v1/media/{media_id}`

### Subtitles
- `POST /api/v1/projects/{project_id}/subtitle-tracks`
- `GET /api/v1/subtitle-tracks/{track_id}`
- `PATCH /api/v1/subtitle-tracks/{track_id}`
- `POST /api/v1/subtitle-tracks/{track_id}/validate`
- `GET /api/v1/subtitle-tracks/{track_id}/export`

### Transcription
- `POST /api/v1/projects/{project_id}/transcriptions`
- `GET /api/v1/transcriptions/{transcription_id}`

### Translation
- `POST /api/v1/translations`
- `GET /api/v1/translations/{translation_id}`
- `PATCH /api/v1/translations/{translation_id}`

### Dubbing
- `POST /api/v1/projects/{project_id}/dubbing-jobs`
- `GET /api/v1/dubbing-jobs/{job_id}`
- `POST /api/v1/dubbing-jobs/{job_id}/retry`
- `GET /api/v1/dubbing-jobs/{job_id}/output`

### Jobs
- `GET /api/v1/jobs/{job_id}`

These routes are proposals and should be refined with resource schemas, authorization rules and error cases before implementation.

## 4. Asynchronous job behavior

A processing request should normally:
1. Validate the request.
2. Create a job record.
3. Enqueue the job.
4. Return an accepted response with a job identifier.
5. Allow the client to poll or receive job status updates.
6. Expose structured progress and failure information.

Suggested job states:
- queued
- validating
- processing
- awaiting_review
- completed
- failed
- cancelled

## 5. Error response convention

Use a consistent structure with:
- Stable error code.
- Human-readable message.
- Optional field-level details.
- Request or correlation identifier.

Do not return stack traces or secret provider details to clients.

## 6. Upload security

- Enforce file type and size limits.
- Verify file content rather than trusting filename extensions.
- Use private storage by default.
- Use short-lived upload/download authorization.
- Record ownership and retention.
- Protect against path traversal and malicious media.

## 7. Open decisions

- Authentication method.
- Pagination standard.
- Job status delivery: polling, server-sent events or WebSockets.
- Upload strategy for large media.
- Idempotency requirements.
- Public library download authorization.
