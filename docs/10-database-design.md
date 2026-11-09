# Subtitle Studio — Database Design

**Document:** 10 — Database Design  
**Status:** Conceptual proposal; not implementation-ready  
**Version:** 0.1

---

## 1. Purpose

Describe the likely data entities and relationships for the platform. The first local SRT editor MVP does not require a database.

## 2. Design principles

- Separate source media, subtitle content, translations and generated audio.
- Preserve provenance and version history.
- Store timestamps in a consistent, precise representation.
- Represent language and variety explicitly.
- Keep AI provider details and job status.
- Avoid storing large media binaries directly in relational tables; store object references and metadata.

## 3. Proposed entities

### Identity and collaboration
- User
- Workspace
- WorkspaceMember
- Project
- ProjectMember
- Task

### Media
- MediaAsset
- MediaMetadata
- MediaUpload
- MediaRetentionRecord

### Subtitle content
- SubtitleTrack
- SubtitleEntry
- SubtitleVersion
- SubtitleContribution
- SubtitleReview

### Language
- Language
- LanguageVariant
- ProviderLanguageCapability

### AI processing
- ProcessingJob
- ProcessingJobAttempt
- Transcript
- TranscriptSegment
- Speaker
- Translation
- TranslationVersion
- VoiceProfile
- GeneratedAudio
- DubbedOutput

### Library
- MediaTitle
- Series
- Season
- Episode
- Release
- LibrarySubtitle
- DownloadRecord
- Report

## 4. Key relationship proposals

- A Project can contain multiple MediaAssets.
- A Project can contain multiple SubtitleTracks.
- A SubtitleTrack contains ordered SubtitleEntries.
- A Transcript contains TranscriptSegments.
- A TranscriptSegment may reference a Speaker.
- A Translation references a source segment and target Language/Variant.
- A GeneratedAudio record references a Translation version and VoiceProfile.
- A DubbedOutput references a project and its selected generated audio assets.
- A ProcessingJob records one processing stage and its attempts.

## 5. Timestamp representation

For subtitle editing, use integer milliseconds as the canonical application representation. Database storage may use integer milliseconds or an appropriate precise interval representation, but the choice must be consistent.

Avoid floating-point values for canonical subtitle timestamps.

## 6. Provenance and versioning

Record:
- Who or what created a record.
- Source/provider/model where applicable.
- Created and updated timestamps.
- Human review status.
- Version relationships.
- Applicable licence and rights metadata.

Do not overwrite the only copy of a reviewed translation when regenerating it.

## 7. Storage boundaries

PostgreSQL stores structured metadata and relationships. Object storage holds media files, audio segments, exports and other large binary assets.

## 8. Open decisions before schema implementation

- ORM selection for FastAPI.
- ID strategy.
- Soft deletion requirements.
- Subtitle versioning model.
- Multi-tenant workspace boundaries.
- Library title and release metadata source.
- Retention and deletion model.
- Whether generated audio is stored per segment or in grouped assets.
