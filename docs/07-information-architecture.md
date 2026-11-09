# Subtitle Studio — Information Architecture

**Document:** 07 — Information Architecture  
**Status:** Proposed  
**Version:** 0.1

---

## 1. Purpose

Define the high-level organization of product areas and navigation. This is a product-level proposal, not a final UI specification.

## 2. Proposed top-level navigation

- Home / Dashboard
- Subtitle Library
- Subtitle Studio
- AI Dubbing Studio
- My Projects
- Community
- Help / Documentation
- Account and Settings (when accounts are introduced)

## 3. Subtitle Library hierarchy

- Search
  - Movies
  - TV series
  - Seasons
  - Episodes
- Title details
  - Available subtitle languages
  - Release/version matches
  - File format and metadata
  - Licence and contributor
  - Review status
- Contribution
  - Upload subtitle
  - Edit metadata
  - Submit correction
  - Report content

## 4. Subtitle Studio hierarchy

- New subtitle project
- Import subtitle
- Editor
  - Video preview
  - Subtitle entry list
  - Text and timing editor
  - Track-level timing adjustment
  - Validation
  - Export

## 5. AI Dubbing Studio hierarchy

- New dubbing project
- Media upload
- Source-language and target-language settings
- Transcript review
- Speaker management
- Translation review
- Voice assignment
- Audio generation
- Synchronization and mixing
- Preview
- Export

## 6. Community and filmmaker workspace

- Workspaces
- Projects
- Members and roles
- Tasks
- Translation/review queues
- Contribution history
- Project assets and deliverables

## 7. MVP navigation

The first MVP should be simpler than the long-term navigation:

- Subtitle Editor
- Open SRT
- Load Video
- Export SRT

Do not expose unfinished product areas as active navigation items in the first release.

## 8. Navigation principles

- Keep the primary editing task easy to reach.
- Avoid mixing library discovery with project editing.
- Make project status visible.
- Keep language and review status visible where relevant.
- Introduce account and workspace navigation only when those capabilities exist.

## 9. Open decisions

- Should Library and Studio be separate top-level destinations?
- Should the editor be a standalone tool or project-based workspace?
- Which navigation is appropriate for desktop and mobile?
