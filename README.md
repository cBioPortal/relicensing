# cBioPortal Relicensing (RFC 86)

This repository is the public coordination record for relicensing core cBioPortal software from **AGPL-3.0** to **Apache-2.0**.

## What is changing

RFC86 relicensed the in-scope repositories to Apache-2.0 (switch merged 2026-10-20/21; first release with the switch is `v7.2.2`, 2026-10-27; `cbioportal-helm` followed on 2026-10-26). Releases before `v7.2.2`, including `v7.2.1`, remain AGPL-3.0:

- `cBioPortal/cbioportal`
- `cBioPortal/cbioportal-frontend`
- `cBioPortal/cbioportal-docker-compose`
- `cBioPortal/cbioportal-core`
- `cBioPortal/session-service`
- `cBioPortal/cbioportal-helm` (Apache-2.0; its two contributors have consented)

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
- Public consent collection issue: https://github.com/cBioPortal/relicensing/issues/24 (formerly `cbioportal#12271`, moved via issue transfer)
- Team lead consent issue: https://github.com/cBioPortal/relicensing/issues/25 (formerly `cbioportal#12282`, moved via issue transfer)

### Where can the public give feedback?
- Formal notice + 30-day comment period: https://github.com/cBioPortal/relicensing/issues/21

## Current status (high level)

- Phase 0: Release & Component Scope [completed]
- Phase 1: Compliance & Dependency Audit [completed]
- Phase 2: Contributor Outreach & Consent [completed 2026-10-28; individual consents still welcome on #24]
  - Public consent board: [`docs/relicensing/contributor-consent-status.md`](docs/relicensing/contributor-consent-status.md)
  - Team leads: 8/8 agreed
  - Individual contributors: 126/209 agreed

- Phase 3: Community Feedback & Notice Period [completed; no public comments] — notice: [`relicensing#21`](https://github.com/cBioPortal/relicensing/issues/21)
- Pre-Switch Sign-off Gate [signed retroactively 2026-10-28]: [`docs/relicensing/signoff-record.md`](docs/relicensing/signoff-record.md)
- Phase 4: Technical Execution [completed 2026-10-28; releases of core, session-service, docker-compose and Helm, and updated image pins, still pending]
- Phase 5: Future Governance [open: DCO and license scanning not done]

## Where to read details

- RFC86 source document: https://docs.google.com/document/d/1X4lrW4Foi23hoplIUd_jcy7Vn0MwoIOyDchum2vqn0w/edit?tab=t.0#heading=h.btohl122j9ni
- Scope and combined-distribution model: [`docs/relicensing/component-manifest.md`](docs/relicensing/component-manifest.md)
- Dependency/license audit: [`docs/relicensing/dependency-audit.md`](docs/relicensing/dependency-audit.md)
- Process details are tracked in [the phase issue set](https://github.com/cBioPortal/relicensing/issues/8)
