# Subtitle Studio — AI & Media Processing Architecture

**Document:** 13 — AI & Media Processing  
**Status:** Proposed architecture and research plan  
**Version:** 0.1

---

## 1. Purpose

Describe the future AI and media-processing pipeline. The first SRT editor MVP does not implement these capabilities.

## 2. Processing stages

Keep the following stages logically independent:

1. Media validation and metadata extraction.
2. Audio extraction and normalization.
3. Speech recognition / transcription.
4. Speaker diarization.
5. Timestamp alignment or forced alignment.
6. Translation.
7. Human review.
8. Voice selection and assignment.
9. Text-to-speech generation.
10. Timing adjustment and synchronization.
11. Dialogue separation and audio mixing.
12. Video rendering and output validation.

## 3. Transcription

The ASR adapter should accept prepared audio and return normalized transcript segments.

Store:
- Text.
- Start and end time.
- Speaker reference where available.
- Confidence where provided.
- Provider/model.
- Language and detected language.
- Processing metadata.

Transcription and alignment must remain separate so the provider can be changed and timestamps can be refined independently.

## 4. Speaker diarization

Diarization estimates which speaker is active at different times. It does not automatically identify the visible character in the video or reliably infer a person's age or gender.

Requirements:
- Allow speaker merge/split and correction.
- Preserve confidence or uncertainty where available.
- Keep speaker identity separate from synthetic voice assignment.
- Avoid presenting inferred demographic attributes as certain facts.

## 5. Translation

Translation should:
- Use source dialogue and nearby context.
- Preserve segment links to the source.
- Support language variety and style settings where validated.
- Preserve idioms and intent rather than literal word order.
- Allow human correction.
- Store model/provider and version information.

## 6. Twi speech generation investigation

Twi is the first focused TTS evaluation target.

Evaluate:
- Asante and Akuapem varieties where supported.
- Pronunciation and tonal accuracy.
- Naturalness and intelligibility.
- Voice consistency.
- Speaking rate and emotional delivery.
- Names, loanwords and code-switching.
- Commercial-use licensing.
- Data handling and provider terms.

An existing model or repository is a research candidate only until its output, licence, maintenance and commercial rights are verified.

## 7. Voice assignment

A speaker can be assigned a synthetic voice profile. Voice profiles should contain provider-specific references, supported controls and licence/consent metadata.

Voice cloning or close imitation requires appropriate authorization. Do not assume the uploader has rights to clone every voice in an uploaded film.

## 8. Synchronization

Generated speech may differ in duration from the original dialogue.

Potential techniques:
- Translation adaptation to fit a timing window.
- Controlled speech-rate adjustment.
- Segment timing adjustment.
- Pause preservation.
- Human timeline editing.

Do not time-stretch speech beyond quality limits without review.

## 9. Background audio

Replacing the entire original audio track can remove music and sound effects.

Potential approaches:
- Use a supplied music-and-effects stem.
- Use authorized dialogue separation.
- Mix generated dialogue with preserved background audio.
- Allow manual review where separation artifacts are audible.

Dialogue separation is imperfect and should not be promised as lossless.

## 10. Background jobs

Long-running stages should run asynchronously. Each stage should:
- Have an explicit input and output contract.
- Record job state and attempts.
- Be idempotent where practical.
- Store output asset references.
- Support retry and cancellation where safe.
- Expose progress to the frontend.

## 11. Provider abstraction

Define independent interfaces for:
- Transcription.
- Diarization.
- Alignment.
- Translation.
- Text-to-speech.
- Dialogue separation where used.

Provider adapters should normalize responses into internal domain models.

## 12. Quality evaluation

Use native-speaker review for Twi. Evaluate transcription, translation and TTS separately.

Record:
- Intelligibility.
- Naturalness.
- Meaning preservation.
- Pronunciation.
- Dialect fit.
- Speaker consistency.
- Timing fit.
- Reviewer corrections.

## 13. Open decisions

- Initial ASR provider.
- Twi translation strategy.
- First TTS model/provider.
- Speaker diarization provider.
- Alignment approach.
- Dialogue separation strategy.
- Audio rendering pipeline.
- Consent and voice-rights workflow.
