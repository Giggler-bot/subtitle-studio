# Subtitle Studio — Security, Privacy & Safety

**Document:** 14 — Security & Safety  
**Status:** Draft  
**Version:** 0.1

---

## 1. Purpose

Define security, privacy, rights and operational safeguards for a platform that accepts user-provided subtitle and media files and may use external AI services.

## 2. Media rights and copyright

- Users must have appropriate rights or authorization to upload and process media.
- Do not distribute copyrighted movies or television episodes without appropriate rights.
- Subtitle contributions need clear licence and attribution information.
- Provide a process for rights-holder notices, reports and takedowns.
- Keep source media private by default.
- Distinguish processing a user's authorized media from redistributing it.

Legal requirements vary by jurisdiction; obtain qualified legal advice before public launch.

## 3. Voice rights and consent

- Do not assume a user may clone any actor or speaker in an uploaded recording.
- Require appropriate authorization for voice cloning or identity imitation.
- Provide clear disclosure when audio is AI-generated.
- Keep synthetic voice profiles separate from real-person identity claims.
- Establish a complaint and removal process for misuse.

## 4. Upload security

- Validate file size, extension and actual file content.
- Use allowlists for supported media formats.
- Store uploads outside the application executable path.
- Generate safe internal object names.
- Prevent path traversal.
- Scan files where appropriate.
- Restrict access to private media.
- Avoid executing uploaded files or trusting embedded metadata.

## 5. Privacy and retention

- Explain what files are uploaded to the server and which external providers receive them.
- Minimize retention of source media.
- Define configurable retention and deletion policies.
- Avoid retaining user media by default beyond the disclosed processing need.
- Ensure deletion covers object storage and derived assets where required.
- Do not use private user uploads for model training without an appropriate lawful basis and clear permission.

## 6. Secrets and access control

- Keep API keys and credentials in environment or secret-management systems.
- Never commit `.env` files or secrets.
- Apply authorization checks to projects, media and generated outputs.
- Use short-lived signed URLs where appropriate.
- Rate-limit sensitive and expensive endpoints.

## 7. AI provider risk

Before selecting a provider, review:
- Data retention.
- Data residency where relevant.
- Training use of submitted data.
- Commercial-use terms.
- Output rights.
- Language support claims.
- Security controls.
- Availability and rate limits.

## 8. Abuse prevention

Potential safeguards:
- User quotas and duration limits.
- Upload and generation rate limits.
- Reporting and takedown process.
- Voice-cloning authorization checks.
- Audit trail for sensitive operations.
- Review of suspicious or abusive activity.

## 9. Operational safeguards

- Log job identifiers and errors without unnecessarily logging private media content.
- Avoid returning internal stack traces to users.
- Back up structured data.
- Test deletion and recovery procedures.
- Monitor storage and processing costs.

## 10. Open decisions

- Retention defaults and deletion timeframes.
- Rights declaration wording.
- Voice cloning consent evidence.
- Moderation responsibility.
- Incident response process.
- Applicable privacy and copyright obligations for launch markets.
