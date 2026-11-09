# Subtitle Studio — Language & Localization Strategy

**Document:** 09 — Language & Localization Strategy  
**Status:** Draft  
**Version:** 0.1

---

## 1. Purpose

Define how Subtitle Studio will represent, evaluate and expand language support across transcription, translation, subtitle generation and speech synthesis.

## 2. Strategic principle

Twi is the first language selected for focused AI-dubbing investigation. The product architecture should support additional African and international languages without assuming that every provider supports every capability equally well.

## 3. Language capability dimensions

Track each capability independently:

- Speech recognition / transcription.
- Speaker diarization.
- Translation into the language.
- Translation from the language.
- Text-to-speech.
- Forced alignment.
- Pronunciation controls.
- Human review availability.
- Commercial licensing and usage rights.

## 4. Initial language priorities

### Ghanaian language investigation
- Asante Twi.
- Akuapem Twi.
- Ewe.
- Ga.
- Fante.
- Dagbani.
- Dagaare.
- Gonja.

### Wider African expansion candidates
- Hausa.
- Yoruba.
- Igbo.
- Swahili.
- Zulu.
- Xhosa.
- Amharic.
- Wolof.
- Shona.
- Kinyarwanda.

### International expansion candidates
- English.
- French.
- Spanish.
- Portuguese.
- German.
- Arabic.
- Chinese.
- Japanese.
- Korean.
- Hindi.

These lists are candidates, not provider-support claims.

## 5. Language and variety model

A language may have multiple varieties, dialects, scripts or regional conventions. Store language identity separately from the selected variety.

Potential fields:

- BCP 47 language tag where applicable.
- Display name.
- Native display name.
- Script.
- Variety identifier.
- Locale and region.
- Text direction.
- Provider-specific language identifier.
- Capability status.

Do not assume that a language code alone captures dialect or pronunciation requirements.

## 6. Twi evaluation plan

Evaluate Asante and Akuapem Twi separately where appropriate.

Test:
- Common vocabulary.
- Tone and pronunciation.
- Natural conversational speech.
- Names and place names.
- English loanwords and code-switching.
- Idioms and humour.
- Different speaker ages and speaking styles.
- Noisy and clean audio.
- Short dialogue and longer passages.

Use native-speaker reviewers and documented evaluation samples.

## 7. Support maturity levels

Suggested statuses:

- **Research:** feasibility is being investigated.
- **Experimental:** prototype works but quality is not assured.
- **Limited:** supported for specified tasks or varieties with known limitations.
- **Reviewed:** evaluated by qualified human reviewers against documented criteria.
- **Production-ready:** meets defined quality, reliability, rights and operational standards.

A language can have different maturity levels for transcription, translation and speech generation.

## 8. Translation quality principles

- Preserve meaning rather than translating mechanically word for word.
- Use surrounding dialogue for context.
- Preserve speaker intent, register and character voice.
- Handle idioms and culturally specific references carefully.
- Keep original and translated text linked but independently editable.
- Provide human review for high-impact or uncertain content.

## 9. Provider evaluation

For each provider/model, record:
- Supported language and variety.
- Supported task.
- Quality evidence.
- Latency and cost.
- Data retention and privacy terms.
- Commercial usage rights.
- Model/version.
- Known limitations.

## 10. Open decisions

- First Twi variety for the TTS prototype.
- Native-speaker evaluation panel and rubric.
- Minimum thresholds for each support maturity level.
- Which language should be evaluated after Twi.
