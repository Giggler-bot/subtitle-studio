# Subtitle Studio — Development Roadmap

**Document:** 15 — Development Roadmap  
**Status:** Proposed sequence  
**Version:** 0.1  
**Last updated:** 7 November 2026

---

## 1. Roadmap principles

- Deliver working increments.
- Test each milestone before moving forward.
- Learn technologies when they become necessary to the product.
- Avoid building infrastructure before a feature requires it.
- Revisit priorities using user feedback and technical evidence.
- Keep AI capabilities and language claims evidence-based.

## 2. Phase 0 — Product definition

**Objective:** Establish what we are building and why.

Deliverables:
- Product discovery.
- Product vision.
- Product requirements.
- User personas and stories.
- MVP definition.
- Initial architecture and risk documentation.

Exit criteria:
- MVP scope agreed.
- Open decisions recorded.
- First milestone acceptance criteria understood.

## 3. Phase 1 — SRT editor MVP

**Objective:** Build a useful local subtitle editor.

Milestones:
1. Project setup and SRT parser.
2. Subtitle entry display.
3. Text editing.
4. Timestamp editing and validation.
5. Global timing shift.
6. Local video preview.
7. SRT export and round-trip tests.
8. Usability and acceptance testing.

Exit criteria: all MVP acceptance criteria pass.

## 4. Phase 2 — Editor improvements

Potential additions:
- VTT import/export.
- Undo/redo.
- Search and navigation.
- Better validation.
- Keyboard shortcuts.
- Project save/reopen.
- Accessibility and usability improvements.

## 5. Phase 3 — Backend foundations

Introduce when persistent projects or server-side processing are needed:
- Python application structure.
- FastAPI.
- PostgreSQL.
- Data models and migrations.
- Project and media APIs.
- Authentication and authorization.
- Object storage.

## 6. Phase 4 — Transcription

- Evaluate ASR providers.
- Build provider adapter.
- Extract and normalize audio.
- Generate transcript segments.
- Review and correct transcript.
- Track timestamps and provenance.

## 7. Phase 5 — Translation

- Evaluate translation approaches.
- Preserve source/target segment relationships.
- Add language and variety settings.
- Build human review workflow.
- Measure translation quality.

## 8. Phase 6 — Twi TTS feasibility

- Evaluate candidate Twi TTS models and providers.
- Verify licences and commercial rights.
- Build a small text-to-audio prototype.
- Recruit native-speaker reviewers.
- Evaluate Asante/Akuapem fit, pronunciation and naturalness.
- Decide whether to use, adapt or replace candidate technology.

Do not proceed to production dubbing until quality and rights requirements are met.

## 9. Phase 7 — Multi-speaker dubbing

- Speaker diarization.
- Speaker correction.
- Voice profile assignment.
- Segment-level speech generation.
- Timing adjustment.
- Preview and regeneration.

## 10. Phase 8 — Audio mixing and video export

- Investigate dialogue separation or separate music-and-effects stems.
- Mix generated dialogue.
- Preserve appropriate background audio.
- Render output.
- Validate output and expose download.

## 11. Phase 9 — Subtitle Library

- Title and episode metadata.
- Search and filters.
- Release matching.
- Subtitle uploads and downloads.
- Contribution and review.
- Moderation and rights workflows.

The exact position of this phase may change based on user validation and product priorities.

## 12. Phase 10 — Community and language expansion

- Translator profiles.
- Collaborative projects.
- Review queues.
- Additional African languages.
- International language support.
- Professional localization workflows.

## 13. Development workflow

For each milestone:
1. Explain the concepts.
2. Define the task and acceptance criteria.
3. Implement a small increment.
4. Run tests.
5. Review architecture and code.
6. Update documentation and progress.

## 14. Progress tracking

Maintain a project status record with:
- Current phase.
- Completed milestones.
- Active task.
- Blockers.
- Technical decisions.
- Next milestone.
- Documentation requiring updates.

## 15. Open decisions

- Whether library work should precede or follow AI features.
- First backend hosting approach.
- AI provider selection.
- Twi TTS feasibility outcome.
- Product pricing and quota model.
