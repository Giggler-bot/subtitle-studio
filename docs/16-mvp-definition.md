# Subtitle Studio — MVP Definition

**Document:** 16 — MVP Definition  
**Status:** Draft for review  
**Version:** 0.1  
**Last updated:** 7 November 2026

---

## 1. Purpose

This document defines the first practical release of Subtitle Studio.

The long-term product includes a subtitle library, AI subtitle generation, translation, AI dubbing, community contributions and filmmaker workspaces. Attempting to build all of those capabilities in the first release would create unnecessary technical and product risk.

The MVP therefore focuses on one complete, testable workflow:

**Upload an SRT file → inspect and edit subtitles → shift timing → preview against a video → export a corrected SRT file.**

The MVP should demonstrate that Subtitle Studio can reliably parse, represent, edit, synchronize and serialize subtitle data.

## 2. MVP goal

Enable a user to correct an existing SRT subtitle file and produce a usable corrected SRT file without needing a separate subtitle-editing application.

## 3. Target MVP user

The initial target user is someone who already has:
- An SRT subtitle file.
- A corresponding video file available locally.
- A need to correct subtitle text or timing.

The MVP is not initially aimed at users who need automatic transcription, translation or online subtitle discovery.

## 4. Core user journey

1. Open Subtitle Studio.
2. Select an SRT file from the local device.
3. The application parses and validates the file.
4. The user sees subtitle entries in an editable list or table.
5. The user edits text or timestamps.
6. The user optionally loads a local video for preview.
7. The user shifts all subtitle entries forward or backward by a specified offset.
8. The user previews the video with subtitles displayed at the appropriate timestamps.
9. The user exports the corrected SRT file.
10. The user can reopen the exported file in another compatible player or editor.

## 5. In-scope functional requirements

### MVP-01: SRT upload

The application must:
- Allow the user to select an SRT file.
- Read the selected file locally.
- Validate basic SRT structure.
- Display a useful error when the file cannot be parsed.
- Avoid silently discarding invalid or unrecognized subtitle content.
- Preserve the original file until the user chooses to export.

**Acceptance criteria**
- A valid SRT file can be loaded.
- Subtitle entries are parsed into separate records.
- Invalid input produces a clear error.
- Empty or malformed files do not crash the application.

### MVP-02: Subtitle entry display

The application must display each entry with:
- Entry number or stable internal identifier.
- Start timestamp.
- End timestamp.
- Subtitle text.

**Acceptance criteria**
- All parsed entries can be inspected.
- Entries are presented in chronological order.
- Multiline subtitle text is preserved.
- The user can identify the entry being edited.

### MVP-03: Subtitle text editing

The user must be able to edit the text of an individual subtitle entry.

**Acceptance criteria**
- Changes appear in the editor.
- Multiline text remains supported.
- Editing one entry does not unexpectedly change another.
- Updated text is included in the exported SRT.

### MVP-04: Timestamp editing

The user must be able to change the start and end timestamps of an individual entry.

**Acceptance criteria**
- Timestamps are validated.
- Start time must not be later than end time.
- Invalid timestamp input is clearly reported.
- Valid changes are reflected in preview and export.

### MVP-05: Global timing adjustment

The user must be able to shift all subtitle entries forward or backward by a specified offset.

Examples:
- `+2000 ms` shifts subtitles two seconds later.
- `-1500 ms` shifts subtitles 1.5 seconds earlier.

**Acceptance criteria**
- Positive and negative offsets are supported.
- All entries are shifted consistently.
- No timestamp becomes negative.
- Invalid adjustments are rejected or clearly reported.
- The application provides a clear way to undo or reverse an adjustment.
- Exported timestamps reflect the adjustment.

### MVP-06: Local video preview

The user must be able to load a corresponding local video file and preview subtitles during playback.

**Acceptance criteria**
- The video can be selected independently of the SRT file.
- The video plays using browser-supported playback capabilities.
- The subtitle corresponding to the current playback time is displayed.
- Subtitles appear and disappear according to their timestamps.
- Seeking updates the displayed subtitle.
- Editing subtitle timing is reflected in preview.

The first version does not need to permanently merge subtitles into the video.

### MVP-07: SRT export

The user must be able to export edited subtitle data as an SRT file.

**Acceptance criteria**
- The exported file uses valid SRT structure.
- Entries have valid sequential numbering.
- Timestamps use `HH:MM:SS,mmm`.
- Multiline text is preserved.
- The exported file can be loaded again by the application.
- The user can download the corrected file.

## 6. MVP subtitle data model

```typescript
type SubtitleEntry = {
  id: string;
  index: number;
  startTimeMs: number;
  endTimeMs: number;
  text: string;
};
```

Design notes:
- Use milliseconds as the internal time representation.
- Convert to and from SRT timestamp strings at file boundaries.
- Keep a stable internal ID separate from the SRT sequence number.
- Do not use floating-point seconds as the canonical timestamp representation.
- Preserve line breaks in subtitle text.
- Define validation behavior for overlapping entries without automatically changing user data.

## 7. MVP non-functional requirements

### Reliability
- Invalid files must not crash the editor.
- Editing and timing operations must be deterministic.
- Exported files must be parseable by the application's own parser.

### Performance
- The first version should handle ordinary subtitle files without noticeable editing delays.
- File-size and entry-count limits should be considered and documented.
- Large-file performance should be tested before increasing supported limits.

### Privacy
- The first MVP should process subtitle and video files locally in the browser where practical.
- Do not upload local media to a server without an explicit future product requirement and user disclosure.
- Do not retain user media by default.

### Accessibility and usability
- Controls should have clear labels.
- Keyboard navigation should be considered.
- Timestamp and validation errors should be understandable.
- The editor should remain usable at common desktop screen sizes.

## 8. Explicitly out of scope for this MVP

- User registration and authentication.
- Cloud subtitle storage.
- Public subtitle library.
- Movie and episode metadata search.
- Community ratings, reviews and contributor profiles.
- Automatic speech recognition.
- AI transcription.
- AI translation.
- Twi translation.
- Text-to-speech.
- AI dubbing and voice cloning.
- Speaker diarization.
- Dialogue separation.
- Audio mixing and video rendering.
- Lip synchronization.
- ASS export.
- Collaborative editing.
- Payments and subscriptions.
- Professional localization marketplace.

These features remain part of the broader product vision and can be introduced through later milestones.

## 9. Proposed implementation approach

### Frontend
React with Next.js. The frontend handles local SRT file selection and parsing, subtitle state and editing, local video selection and playback, subtitle synchronization and SRT serialization/download.

### Backend
The first MVP does not require a backend API. A browser-based implementation is sufficient for the initial local editing workflow. FastAPI can be introduced when server-side project persistence, accounts, AI providers, background processing or cloud workflows are required.

### Media processing
Use native browser video playback for the first preview workflow. FFmpeg can be introduced later for server-side media inspection, audio extraction, audio mixing and final video rendering. It is not required merely to display subtitles over a locally played video.

### Persistence
The initial MVP can operate without a database. Persistence and project recovery can be evaluated after the core editing workflow is tested.

## 10. MVP testing plan

### Parser tests
- Valid single-entry SRT.
- Valid multi-entry SRT.
- Multiline subtitle text.
- Empty file.
- Malformed timestamps.
- Missing separators.
- Unicode text.
- Large subtitle file.

### Timing tests
- Positive shift.
- Negative shift.
- Zero shift.
- Shift that would create a negative timestamp.
- Entries with different durations.
- Overlapping entries.
- Very large timestamp values.

### Editor tests
- Edit one entry.
- Edit multiline text.
- Edit start and end times.
- Verify other entries remain unchanged.
- Verify preview updates after edits.

### Preview tests
- Subtitle appears at its start time.
- Subtitle disappears at its end time.
- Seeking updates subtitle display.
- Playback pauses and resumes correctly.
- Timing adjustments affect preview.

### Export tests
- Export a valid file.
- Re-import the exported file.
- Compare entry count and text.
- Compare timestamps.
- Verify multiline text and Unicode characters.

## 11. MVP completion criteria

The MVP is complete when:
1. A user can load a valid SRT file.
2. The application correctly displays all entries.
3. A user can edit subtitle text.
4. A user can edit individual timestamps.
5. A user can shift all subtitle timings forward and backward.
6. A user can preview subtitles against a local video.
7. A user can export a corrected SRT file.
8. The exported file can be reopened without losing its content.
9. Core parser, timing, preview and export tests pass.

## 12. Suggested milestone breakdown

| Milestone | Deliverable |
|---|---|
| M1 | Project setup and SRT parser |
| M2 | Subtitle entry display and text editing |
| M3 | Individual timestamp editing and validation |
| M4 | Global timing adjustment |
| M5 | Local video preview and synchronization |
| M6 | SRT export and round-trip tests |
| M7 | Usability review and MVP acceptance testing |

## 13. What follows the MVP

1. Improve subtitle editing and add VTT support.
2. Introduce backend project persistence when justified.
3. Add audio transcription through a replaceable provider interface.
4. Add subtitle translation and human review.
5. Evaluate Twi text-to-speech using native-speaker testing.
6. Build multi-speaker AI dubbing.
7. Add synchronization, dialogue mixing and video export.
8. Develop the subtitle library and community contribution workflows.
9. Expand language coverage based on measured quality and provider capability.

This sequence is provisional and should be revisited after each milestone.

## 14. Decisions requiring confirmation

| Decision | Current proposal | Status |
|---|---|---|
| First MVP | Local SRT editor | Agreed direction |
| Initial subtitle format | SRT | Agreed direction |
| Video preview | Local browser playback | Proposed |
| Initial processing | Browser-side | Proposed |
| Backend required for first MVP | No | Proposed |
| Initial target platform | Desktop web | Proposed |
| VTT support | Later milestone | Proposed |
| Database persistence | Later milestone | Proposed |
| AI dubbing | Outside first MVP | Agreed scope separation |

---

**Document maintenance:** Update this document when MVP scope, acceptance criteria or implementation decisions change. Any feature added to the MVP should have an explicit reason and updated testing criteria.
