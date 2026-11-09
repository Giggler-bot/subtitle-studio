# Subtitle Studio — User Journey Maps

**Document:** 06 — User Journeys  
**Status:** Draft  
**Version:** 0.1

---

## 1. Purpose

Describe the main user workflows and identify the decisions, system responses and failure states that the product must support.

## 2. Journey A — Correct an SRT file (first MVP)

1. User opens the editor.
2. User selects an SRT file.
3. Application parses the file.
4. Application displays entries or reports parsing errors.
5. User edits text and timestamps.
6. User optionally loads a local video.
7. User previews playback and subtitle synchronization.
8. User shifts the full track if required.
9. User exports corrected SRT.
10. User can reopen the exported file.

**Key failure states:** malformed SRT, unsupported encoding, invalid timestamp, negative shift result, unsupported video codec, export failure.

## 3. Journey B — Find a subtitle (later)

1. Visitor searches a movie or series.
2. Visitor selects the correct title and episode.
3. Visitor filters by language.
4. Results show release match, format, contributor and review status.
5. Visitor reviews licence and details.
6. Visitor downloads a permitted subtitle.

**Key failure states:** no exact match, uncertain release match, reported file, unavailable download.

## 4. Journey C — Generate translated subtitles (later)

1. User creates a project.
2. User uploads media they are authorized to process.
3. System validates media and creates a processing job.
4. Worker extracts audio and transcribes dialogue.
5. User reviews transcript.
6. User selects target language and variety.
7. Translation provider generates segments.
8. User or reviewer corrects translations.
9. User exports subtitle files.

**Key failure states:** unsupported language, low-confidence transcript, provider timeout, partial translation, quota exceeded.

## 5. Journey D — Create a Twi dub (later)

1. User creates a dubbing project and uploads authorized media.
2. User selects Twi and a supported variety.
3. System extracts audio and transcribes dialogue.
4. System identifies speakers where possible.
5. User corrects speaker assignments.
6. Translation engine creates Twi dialogue.
7. Reviewer approves or edits dialogue.
8. User assigns voice profiles.
9. Speech provider generates audio segments.
10. User previews and regenerates selected segments.
11. System synchronizes dialogue and mixes suitable background audio.
12. User reviews the complete output.
13. System exports the dubbed video.

**Key failure states:** unsupported dialect, poor translation, incorrect speaker mapping, unavailable voice, timing overflow, missing music/effects separation, render failure.

## 6. Journey design principles

- Show progress for long-running tasks.
- Preserve completed stages when a later stage fails.
- Make AI-generated content distinguishable from human-reviewed content.
- Let users correct errors at the smallest practical unit.
- Explain failures in actionable language.
- Avoid retaining uploaded media longer than necessary.

## 7. Open questions

- Should users be able to edit while a background job is running?
- How should partial job completion be presented?
- Which stages require explicit approval?
- How should users recover from a failed render?
