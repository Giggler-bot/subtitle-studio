# Subtitle Studio — Feature Architecture

**Document:** 08 — Feature Architecture  
**Status:** Proposed  
**Version:** 0.1

---

## 1. Purpose

Define product feature boundaries so that related capabilities can evolve without creating one tightly coupled application module.

## 2. Product modules

### 2.1 Subtitle Library
Responsibilities:
- Title and episode discovery.
- Subtitle metadata and release matching.
- Upload, download and version management.
- Contribution, moderation and review status.

### 2.2 Subtitle Editor
Responsibilities:
- File parsing and serialization.
- Subtitle entry state.
- Text and timestamp editing.
- Track-level offset operations.
- Video preview synchronization.
- Validation and export.

### 2.3 Media Management
Responsibilities:
- Media metadata.
- Upload validation.
- Storage lifecycle.
- Temporary assets.
- Access control.

### 2.4 Transcription
Responsibilities:
- Audio input preparation.
- ASR provider interface.
- Transcript segments.
- Confidence and provenance.
- Transcript correction.

### 2.5 Speaker Management
Responsibilities:
- Speaker identities.
- Diarization results.
- Human corrections.
- Speaker-to-voice mapping.

### 2.6 Translation
Responsibilities:
- Language and variety selection.
- Translation provider interface.
- Context and terminology.
- Translation review and versioning.

### 2.7 Speech Generation
Responsibilities:
- TTS provider interface.
- Voice profiles.
- Segment generation.
- Audio asset management.
- Regeneration and provider metadata.

### 2.8 Synchronization and Rendering
Responsibilities:
- Timing and duration checks.
- Audio placement.
- Dialogue and background mix.
- Render jobs.
- Output validation.

### 2.9 Collaboration
Responsibilities:
- Workspaces and membership.
- Task assignment.
- Review workflows.
- Contribution history.

## 3. Architectural boundaries

- Transcription must not own translation logic.
- Translation must not own speech generation.
- Speaker identity must be separate from a selected synthetic voice.
- Generated audio must reference the translation version used to create it.
- Media assets must have explicit ownership, access and retention metadata.
- Long-running processing must be coordinated through jobs rather than synchronous web requests.

## 4. MVP boundary

The first SRT editor can be a frontend-only application. Its core subtitle parsing, timing and export logic should be kept in reusable modules so a backend can use equivalent contracts later.

## 5. Future modular-monolith organization

Proposed backend module areas:

```text
backend/
  app/
    modules/
      projects/
      media/
      subtitles/
      transcription/
      speakers/
      translations/
      voices/
      dubbing/
      jobs/
      library/
      collaboration/
```

This is a future direction, not a requirement to create all modules before they are needed.

## 6. Open decisions

- Which modules should be separate Python packages?
- Should provider adapters live inside each module or a shared integrations layer?
- What events or job messages should connect processing stages?
