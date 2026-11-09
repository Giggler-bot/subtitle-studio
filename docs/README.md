# Subtitle Studio — Documentation

This directory contains the working product and technical documentation for Subtitle Studio.

**Documentation status:** Initial working drafts  
**Version:** 0.1  
**Last updated:** 7 November 2026

## Document index

| No. | Document | Purpose |
|---|---|---|
| 01 | [Product Discovery](01-product-discovery.md) | Problem, opportunity, users, product pillars and assumptions |
| 02 | [Product Vision](02-product-vision.md) | Long-term direction, positioning and strategic objectives |
| 03 | [Product Requirements](03-product-requirements.md) | Functional and non-functional product requirements |
| 04 | [User Personas](04-user-personas.md) | Initial user groups, goals and pain points |
| 05 | [User Stories](05-user-stories.md) | User needs and testable acceptance criteria |
| 06 | [User Journeys](06-user-journeys.md) | End-to-end workflows |
| 07 | [Information Architecture](07-information-architecture.md) | Product navigation and content organization |
| 08 | [Feature Architecture](08-feature-architecture.md) | Product modules and feature boundaries |
| 09 | [Language & Localization Strategy](09-language-localization-strategy.md) | Language coverage, dialects and quality standards |
| 10 | [Database Design](10-database-design.md) | Proposed entities, relationships and data rules |
| 11 | [API Design](11-api-design.md) | API conventions and proposed endpoints |
| 12 | [System Architecture](12-system-architecture.md) | Application architecture and infrastructure |
| 13 | [AI & Media Processing](13-ai-media-processing.md) | Transcription, translation, dubbing and media workflows |
| 14 | [Security & Safety](14-security-safety.md) | Privacy, media rights, security and operational safeguards |
| 15 | [Development Roadmap](15-development-roadmap.md) | Phases, dependencies and delivery sequence |
| 16 | [MVP Definition](16-mvp-definition.md) | First release scope and acceptance criteria |

## How to maintain these documents

- Treat decisions marked **Proposed** as recommendations, not final commitments.
- Treat **Open** items as decisions that still need discussion or validation.
- Update documents when product scope or architecture changes.
- Keep the MVP separate from the long-term product vision.
- Record the reason for significant architectural decisions.
- Do not claim a language or AI capability is supported until it has been tested.

## Current product direction

Subtitle Studio is planned as a multilingual media-localization platform combining a subtitle library, subtitle editing tools, AI-assisted transcription and translation, AI dubbing, and collaboration workflows.

The first practical milestone is a local SRT editor that can upload, display, edit, shift, preview and export subtitles. The initial MVP does not require AI, user accounts, cloud storage or a backend API.
