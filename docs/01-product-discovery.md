# Subtitle Studio — Product Discovery

**Document:** 01 — Product Discovery  
**Status:** Draft for review  
**Version:** 0.1  
**Last updated:** 7 November 2026

---

## 1. Executive summary

Subtitle Studio is a proposed multilingual media-localization platform. Its long-term purpose is to help people discover, create, edit, translate, synchronize and distribute subtitles, while also enabling AI-generated voice dubbing.

The product combines four related capabilities:

1. **Subtitle Library** — a community-oriented library for discovering, contributing and downloading subtitles.
2. **Subtitle Studio** — tools for creating, editing, synchronizing, translating and exporting subtitle files.
3. **AI Dubbing Studio** — a workflow for turning dialogue in a source video into spoken dialogue in a selected target language using AI-generated voices.
4. **Community and Filmmaker Workspace** — project collaboration, translator contributions, review workflows and, eventually, professional localization services.

The initial language strategy gives particular attention to Ghanaian and other African languages. Twi is the first language we intend to investigate for AI dubbing, while the architecture should be extensible to additional African and international languages.

The first implementation milestone is deliberately smaller than the long-term vision: a working SRT editor that can upload, display, edit, shift, preview and export subtitle files.

## 2. Product background

Subtitles and dubbing make video content accessible across language and listening preferences. However, these are different localization needs:

- Some viewers prefer reading subtitles while retaining the original audio.
- Some viewers understand a spoken language but find reading it difficult or inconvenient.
- Some viewers prefer watching content fully dubbed in their preferred language.
- Filmmakers and content creators need practical ways to localize their work for different audiences.

Subtitle Studio is intended to address these needs through a connected set of tools rather than a single-purpose subtitle editor.

## 3. Problem statement

People who need subtitles or localized video content may encounter several problems:

- Finding subtitles that match the correct film, episode, release and video version can be difficult.
- Existing subtitle files may contain timing errors, spelling mistakes or incomplete dialogue.
- Editing subtitle timing and content can require specialized software.
- Creating subtitles manually is time-consuming.
- Translating dialogue requires context, language knowledge and review.
- AI transcription and translation quality varies by language, accent, audio conditions and subject matter.
- Many viewers would benefit more from spoken localization than written subtitles.
- Low-resource languages may have fewer reliable speech-recognition, translation and text-to-speech options.

These are discovery hypotheses and product problems to validate with target users. They should not be treated as quantified market findings.

## 4. Product opportunity

Subtitle Studio can create value by connecting subtitle creation, subtitle discovery and spoken localization.

### 4.1 Subtitle discovery and contribution

A searchable library can help users find subtitles by title, language, episode and release information. Community contributions can improve coverage, corrections and language availability.

### 4.2 Practical subtitle editing

An accessible editor can let users correct text and timing, preview subtitles against video, and export standard formats.

### 4.3 AI-assisted localization

AI can help generate transcripts, translate dialogue and synthesize speech. Human review remains important, especially for languages and dialects where model quality is uncertain.

### 4.4 African-language accessibility

The product can investigate and gradually support languages such as Asante Twi, Akuapem Twi, Ewe, Ga, Fante, Hausa and other African languages. International languages can be added through the same extensible architecture.

Language support must be capability-based: a language should not be advertised as fully supported merely because one provider can translate text into it. Transcription, translation, speech generation, alignment and quality review must be evaluated separately.

## 5. Product vision

Build a multilingual media-localization platform that makes video content easier to understand and distribute across languages through subtitles and AI-assisted dubbing.

The product should serve viewers, subtitle contributors, translators, filmmakers and content creators.

## 6. Product pillars

### 6.1 Subtitle Library

Potential capabilities:

- Search movies, television series and episodes.
- Search and filter subtitles by language.
- Match subtitles to releases and versions.
- Upload and download SRT and VTT files.
- Submit corrections and replacement versions.
- Rate, review and report contributions.
- Display provenance and review status, such as AI-generated, community-reviewed or professionally verified.
- Maintain clear licensing, attribution and takedown information.

### 6.2 Subtitle Studio

Potential capabilities:

- Upload and parse SRT and VTT files.
- Edit subtitle text and timestamps.
- Shift subtitle timing forward or backward.
- Preview subtitles against video.
- Validate subtitle structure and timing.
- Transcribe audio into timestamped text.
- Translate subtitles.
- Export SRT, VTT and, later, ASS.

### 6.3 AI Dubbing Studio

Potential capabilities:

- Upload authorized audio or video.
- Extract audio and inspect media metadata.
- Transcribe source dialogue.
- Identify and diarize speakers where supported.
- Translate dialogue into a target language.
- Generate speech using selected voice profiles.
- Maintain consistent voice assignments across a project.
- Synchronize generated dialogue with the video.
- Preserve or replace background audio through suitable audio-mixing workflows.
- Preview and revise generated segments.
- Export a dubbed video.
- Explore lip synchronization as a later capability.

AI voice generation must respect voice ownership, consent and applicable rights. Voice similarity or cloning should not be assumed to be available or authorized for every speaker.

### 6.4 Community and Filmmaker Workspace

Potential capabilities:

- Translator and contributor profiles.
- Collaborative subtitle projects.
- Review and approval workflows.
- Contribution history and attribution.
- Filmmaker workspaces.
- Professional translation and localization services in a later phase.

## 7. Target users

Initial user groups to investigate:

| User group | Main need |
|---|---|
| Movie and TV viewers | Find accurate subtitles or watch content in a preferred spoken language |
| Subtitle contributors | Upload, correct and maintain subtitle files |
| Translators | Translate and review dialogue in context |
| Independent filmmakers | Localize films for additional audiences |
| Content creators | Produce accessible and multilingual video content |
| Localization teams | Coordinate translation, review, dubbing and delivery |

These are provisional personas. Interviews and usability tests should refine their goals, constraints and priorities.

## 8. Initial use cases

1. A viewer finds and downloads a subtitle file that matches a particular film release.
2. A user uploads an SRT file, corrects its dialogue and timing, previews it with a video and exports the corrected file.
3. A creator generates subtitles from an audio or video file.
4. A translator reviews an AI-generated translation.
5. A filmmaker creates a Twi-dubbed version of a film they have the rights to localize.
6. A contributor uploads a reviewed subtitle file to the community library.

## 9. Language and localization strategy

### 9.1 Starting point

Twi is the first language selected for focused AI-dubbing investigation. Asante and Akuapem varieties must be considered explicitly rather than treating Twi as a single undifferentiated voice and translation target.

### 9.2 Expansion direction

Potential Ghanaian languages include Asante Twi, Akuapem Twi, Ewe, Ga, Fante, Dagbani, Dagaare and Gonja.

Potential wider African languages include Hausa, Yoruba, Igbo, Swahili, Zulu, Xhosa, Amharic, Wolof, Shona and Kinyarwanda.

Potential international languages include English, French, Spanish, Portuguese, German, Arabic, Chinese, Japanese, Korean and Hindi.

This is a strategic target list, not a statement that all listed languages are currently supported by available providers.

### 9.3 Language capability model

For each language and variety, track capabilities independently:

- Speech recognition / transcription
- Speaker diarization
- Translation from and into the language
- Text-to-speech
- Forced alignment or timestamp alignment
- Pronunciation and vocabulary controls
- Human review availability
- Evaluation status
- Provider and model licensing
- Commercial-use permission

A language should have a transparent support status such as experimental, limited, reviewed or production-ready.

### 9.4 Quality principles

- Evaluate native-speaker intelligibility and naturalness.
- Test dialect and accent variation.
- Preserve meaning, tone, idioms and cultural context.
- Keep original transcripts and translations separately.
- Make AI-generated content identifiable.
- Provide human correction and approval workflows.
- Do not claim parity with major international languages without evidence.

## 10. Product principles

1. **Build incrementally:** deliver a small working product before expanding into complex AI workflows.
2. **Human review matters:** AI output should be editable and its review status visible.
3. **Provider independence:** transcription, translation, speech generation and alignment should be replaceable components.
4. **Language honesty:** communicate actual capability and quality limitations.
5. **Privacy by design:** minimize retention of uploaded media and make retention policies clear.
6. **Rights-aware operation:** users must have appropriate rights to upload, process and distribute media.
7. **Cost awareness:** use quotas, duration limits, estimates and background processing for expensive workloads.
8. **Accessible workflows:** support both written subtitles and spoken dubbing.

## 11. Initial MVP direction

The first MVP is a focused subtitle-editing tool, not the entire platform.

A user should be able to:

1. Upload an SRT file.
2. View and edit subtitle entries.
3. Shift subtitle timing forward or backward.
4. Preview subtitles alongside a video.
5. Download the corrected SRT file.

This MVP validates core subtitle data handling, timestamp logic, editing experience, video preview and export.

The MVP does not require AI transcription, AI translation, AI dubbing, a community library, user accounts, or cloud-based media processing.

See `16-mvp-definition.md` for detailed scope and acceptance criteria.

## 12. Risks and assumptions

| Risk or assumption | Implication | Response |
|---|---|---|
| Twi speech generation may be limited | Dubbing quality may not meet expectations | Build a provider evaluation prototype and involve native speakers |
| Translation may be overly literal | Dialogue can sound unnatural | Context-aware translation and human review |
| Speaker diarization may confuse characters | Incorrect voice assignments | Editable speaker mapping and confidence indicators |
| Original dialogue may overlap music and effects | Replacing the full audio track can remove important sound | Investigate dialogue separation and separate music-and-effects tracks |
| Processing can be expensive | Long videos may create high costs | Duration limits, estimates, quotas and background jobs |
| Copyright and voice rights may be unclear | Legal and platform risk | Rights declarations, permissions, reporting and takedown workflows |
| Large media files require storage and processing | Infrastructure complexity | Temporary storage, lifecycle rules and asynchronous workers |

## 13. Discovery questions still to validate

- Which user group should be prioritized after the first editor milestone?
- How do viewers currently find subtitles that match their video release?
- Which subtitle formats and editing actions matter most?
- Which Twi variety should be prioritized for the first speech-generation evaluation?
- Which Twi voices are understandable and natural to native speakers?
- Should the first dubbing workflow require translation approval before speech generation?
- What media duration and file-size limits are acceptable for an initial service?
- Which use cases have clear rights to upload and process source media?

## 14. Product discovery exit criteria

Product discovery is sufficiently mature to proceed into detailed requirements when:

- The product problem and target users are documented.
- The product pillars and long-term direction are agreed.
- The first MVP is explicitly separated from later capabilities.
- Major risks and assumptions are visible.
- Open decisions have owners or planned validation activities.
- The MVP requirements and acceptance criteria are ready for review.

## 15. Current decisions and status

| Topic | Current position | Status |
|---|---|---|
| Product direction | Multilingual subtitle and media-localization platform | Proposed |
| First practical milestone | SRT editor with video preview and export | Agreed direction |
| AI dubbing | Major future capability | Strategic direction |
| First dubbing language | Twi | Selected for investigation |
| Future languages | Other African and international languages | Strategic direction |
| Backend direction | Python and FastAPI | Proposed |
| Frontend direction | React and Next.js | Proposed |
| Architecture | Modular monolith | Proposed |
| AI providers | Not selected | Open |
| Twi voice strategy | Natural voices vs authorized voice similarity | Open |
| Twi variety priority | Asante, Akuapem or both | Open |
| Translation approval workflow | Mandatory, optional or automatic | Open |

---

**Document maintenance:** Update this document when discovery evidence, product scope or major decisions change. Record unresolved assumptions rather than silently treating them as facts.
