# Subtitle Studio — User Stories

**Document:** 05 — User Stories  
**Status:** Draft backlog  
**Version:** 0.1

---

## 1. Purpose

Translate product requirements into user-centered, testable stories. Stories are grouped by product area. Only the SRT editor stories are candidates for the first MVP.

## 2. SRT editor — MVP stories

### US-ED-001: Import an SRT file
As a user, I want to select an SRT file so that I can edit its subtitle entries.

**Acceptance criteria**
- A valid file is parsed.
- Entries are displayed in chronological order.
- Malformed input produces a clear error.
- Multiline and Unicode text are preserved.

### US-ED-002: Edit subtitle text
As a user, I want to edit an entry's text so that I can correct spelling or dialogue.

**Acceptance criteria**
- Only the selected entry changes.
- Line breaks are retained.
- The updated text is included in export.

### US-ED-003: Edit entry timing
As a user, I want to change start and end times so that an individual subtitle is synchronized.

**Acceptance criteria**
- Times are validated.
- Start time cannot exceed end time.
- Preview and export reflect valid changes.

### US-ED-004: Shift all subtitles
As a user, I want to shift all entries by an offset so that I can correct a consistently early or late subtitle track.

**Acceptance criteria**
- Positive and negative offsets work.
- Negative resulting timestamps are prevented.
- The operation can be reversed or undone.

### US-ED-005: Preview against video
As a user, I want to load a local video and see subtitles during playback.

**Acceptance criteria**
- Subtitle display follows playback time.
- Seeking updates the active entry.
- Edited timings are reflected.

### US-ED-006: Export corrected SRT
As a user, I want to download the corrected file so that I can use it in a media player.

**Acceptance criteria**
- Output uses valid SRT timestamp syntax.
- Entry numbering is sequential.
- Text and timing survive a parse-export-parse round trip.

## 3. Subtitle Library stories — later

- As a viewer, I want to search by title so that I can find subtitles.
- As a viewer, I want to filter by language so that I can find a readable or spoken language option.
- As a viewer, I want release details so that I can choose a matching subtitle.
- As a contributor, I want to upload a subtitle with licence information.
- As a moderator, I want to review reports and remove infringing or abusive contributions.

## 4. AI subtitle stories — later

- As a creator, I want to transcribe an authorized media file.
- As a translator, I want to review a generated translation beside its source.
- As a user, I want to regenerate or correct one segment without rerunning the entire job.
- As a reviewer, I want to see model provenance and review status.

## 5. AI dubbing stories — later

- As a filmmaker, I want to select a target language and variety.
- As a reviewer, I want to correct dialogue before voice generation.
- As a user, I want to assign a consistent voice to each speaker.
- As a user, I want to preview and regenerate an individual dialogue segment.
- As a filmmaker, I want to export a dubbed version of media I am authorized to process.

## 6. Story readiness checklist

A story is ready for implementation when:
- Its user and value are clear.
- Scope is bounded.
- Acceptance criteria are testable.
- Dependencies are known.
- Privacy, rights and failure cases have been considered.

## 7. Backlog status

All stories in this document are proposed. The MVP stories should be refined into implementation tasks before coding.
