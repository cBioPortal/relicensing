# cBioPortal Relicensing (RFC 86)

This repository is the public coordination record for relicensing core cBioPortal software from **AGPL-3.0** to **Apache-2.0**.

## What is changing

RFC86 proposes Apache-2.0 relicensing for the in-scope repositories:

- `cBioPortal/cbioportal`
- `cBioPortal/cbioportal-frontend`
- `cBioPortal/cbioportal-docker-compose`
- `cBioPortal/cbioportal-core`
- `cBioPortal/session-service`

## Why this is being done

- Key funders require permissive licensing.
- Apache-2.0 reduces adoption friction for downstream users.
- Apache-2.0 includes explicit patent terms.

## FAQ

### Is cBioPortal still open source after this?
Yes. This is a license transition, not a move to closed source.

### Is this only a docs change, or does it affect releases?
It affects release licensing and requires a defined switch commit, contributor consent coverage, and notice/sign-off steps.

### Where can contributors publicly give consent?
Public consent collection issue: https://github.com/cBioPortal/cbioportal/issues/12271

### Are signed institutional documents public?
Templates and status are public. Signed originals with signatures/sensitive details are stored privately; public records reference status/evidence.

### Where is the full process documented?
Process details are tracked in the docs below and in the phase issue set.

## Current status (high level)

- Phase 0 completed
- Phase 1 and Phase 2 in progress
- Phase 3+ pending prior phases

## Where to read details

- Scope and combined-distribution model: [`docs/relicensing/component-manifest.md`](docs/relicensing/component-manifest.md)
- Dependency/license audit: [`docs/relicensing/dependency-audit.md`](docs/relicensing/dependency-audit.md)
- Public consent board: [`docs/relicensing/contributor-consent-status.md`](docs/relicensing/contributor-consent-status.md)
- Tier 1 institutional consent sheet: [`docs/relicensing/outreach-tier1-letter.md`](docs/relicensing/outreach-tier1-letter.md)
- Tier 2 individual outreach template: [`docs/relicensing/outreach-tier2-template.md`](docs/relicensing/outreach-tier2-template.md)
- Original proposal source: [`RFC86.docx`](RFC86.docx)

## Tracking issues

Tracked in [`cBioPortal/relicensing`](https://github.com/cBioPortal/relicensing):

- Epic: [#8](https://github.com/cBioPortal/relicensing/issues/8)
- Phase 0: [#1](https://github.com/cBioPortal/relicensing/issues/1)
- Phase 1: [#2](https://github.com/cBioPortal/relicensing/issues/2)
- Phase 2: [#3](https://github.com/cBioPortal/relicensing/issues/3)
- Phase 3: [#4](https://github.com/cBioPortal/relicensing/issues/4)
- Pre-Switch Gate: [#5](https://github.com/cBioPortal/relicensing/issues/5)
- Phase 4: [#6](https://github.com/cBioPortal/relicensing/issues/6)
- Phase 5: [#7](https://github.com/cBioPortal/relicensing/issues/7)

## Assistant guidance

Repository-specific Copilot instructions:
- [`.github/copilot-instructions.md`](.github/copilot-instructions.md)
