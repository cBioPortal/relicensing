# cBioPortal Relicensing — RFC 86

This repository is the coordination and public record for relicensing cBioPortal from **AGPL-3.0** to **Apache-2.0**.

## Goal

Complete a legally and operationally sound AGPL → Apache-2.0 transition for the in-scope cBioPortal release components by **2026-09-30**.

## Why Apache-2.0

- Meets current funder requirements for permissive licensing (NCI ITCR, CZI).
- Reduces enterprise adoption friction tied to AGPL concerns.
- Provides explicit patent grant/retaliation terms needed by many institutional and industry legal teams.

## Scope

RFC86 scope tracks relicensing for the release/distribution path centered on:

- `cbioportal` (backend)
- `cbioportal-frontend`
- `cbioportal-docker-compose`
- `cbioportal-core` (importer)
- `session-service`

Detailed denominator, distribution caveats, and component-level findings are maintained in:
- [`docs/relicensing/component-manifest.md`](docs/relicensing/component-manifest.md)

## Phase model

1. **Phase 0** — Release & component scope
2. **Phase 1** — Compliance & dependency audit
3. **Phase 2** — Contributor outreach & consent
4. **Phase 3** — 30-day public notice/comment
5. **Pre-Switch Gate** — consolidated relicensing sign-off record
6. **Phase 4** — Technical switch commit and license updates
7. **Phase 5** — Future governance (DCO + automated license scanning)

## Timeline (target)

| Track | Window |
|---|---|
| Phase 0 | Jul 10–17 |
| Phase 1 | Jul 10–28 |
| Phase 2 Tier 1 | launch Jul 13, target resolved Jul 24 |
| Phase 2 Tier 2 | launch Jul 28, deadline Aug 18, reconcile by Aug 20 |
| Phase 3 (fixed 30 days) | Aug 21 – Sep 20 |
| Pre-Switch Gate | Sep 20–23 |
| Phase 4 Switch Commit | Sep 23–30 |

## Current status

- [x] Project setup complete
- [x] Epic + phase issues created
- [x] Issues transferred to `cBioPortal/relicensing`
- [x] Phase 0 closed (manifest published)
- [ ] Phase 1 in progress (dependency audit follow-ups open)
- [ ] Phase 2 in progress
- [ ] Phase 3 blocked on Phase 2
- [ ] Pre-Switch Gate blocked on Phase 3
- [ ] Phase 4 blocked on gate
- [ ] Phase 5 blocked on Phase 4

## Key artifacts in this repo

- [`docs/relicensing/component-manifest.md`](docs/relicensing/component-manifest.md) — Phase 0 scope and distribution model
- [`docs/relicensing/dependency-audit.md`](docs/relicensing/dependency-audit.md) — Phase 1 dependency/license findings
- [`docs/relicensing/contributor-consent-status.md`](docs/relicensing/contributor-consent-status.md) — public consent board
- [`docs/relicensing/outreach-tier1-letter.md`](docs/relicensing/outreach-tier1-letter.md) — institutional lead template
- [`docs/relicensing/outreach-tier2-template.md`](docs/relicensing/outreach-tier2-template.md) — individual contributor template
- [`RFC86.docx`](RFC86.docx) — proposal source document

## Issue tracking

Tracked in [`cBioPortal/relicensing`](https://github.com/cBioPortal/relicensing):

| Issue | # |
|---|---|
| Epic | [#8](https://github.com/cBioPortal/relicensing/issues/8) |
| Phase 0 | [#1](https://github.com/cBioPortal/relicensing/issues/1) |
| Phase 1 | [#2](https://github.com/cBioPortal/relicensing/issues/2) |
| Phase 2 | [#3](https://github.com/cBioPortal/relicensing/issues/3) |
| Phase 3 | [#4](https://github.com/cBioPortal/relicensing/issues/4) |
| Pre-Switch Gate | [#5](https://github.com/cBioPortal/relicensing/issues/5) |
| Phase 4 | [#6](https://github.com/cBioPortal/relicensing/issues/6) |
| Phase 5 | [#7](https://github.com/cBioPortal/relicensing/issues/7) |

## Working conventions

- Keep this README and phase docs in sync when decisions/status change.
- Use the issue hierarchy above as the canonical execution tracker.
- Keep private contact/signature material out of public docs; publish only redacted/public-safe status.
- Keep this repo focused on RFC86 coordination and records; implementation changes belong in component repos.

## Assistant guidance

Repository-specific Copilot instructions are in:
- [`.github/copilot-instructions.md`](.github/copilot-instructions.md)