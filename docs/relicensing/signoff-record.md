# DRAFT — RFC 86 Pre-Switch Sign-off Record (retroactive)

> **This record is retroactive.** The gate ([relicensing#5](https://github.com/cBioPortal/relicensing/issues/5)) was meant to be signed Oct 17–20 before the switch. The switch PRs were merged on 2026-10-20 and 2026-10-21 while #5 was still open, and the docker-compose PR was titled "DO NOT MERGE before relicensing#5". This document consolidates the record after the fact and states that plainly. Items marked **[TBD]** need a decision or evidence before signing.

**Record date:** 2026-10-25 · **Epic:** [relicensing#8](https://github.com/cBioPortal/relicensing/issues/8) · **Private originals:** [Drive folder](https://drive.google.com/drive/folders/1pGq4cS1S_gKhCsOsIO7sTEo5IQ9i4pTI)

## 1. Switch execution (what actually happened)

| Repository | Switch PR | Merged (UTC) |
|---|---|---|
| `cbioportal-frontend` | [#5748](https://github.com/cBioPortal/cbioportal-frontend/pull/5748) | 2026-10-20 20:04 |
| `cbioportal-core` | [#197](https://github.com/cBioPortal/cbioportal-core/pull/197) | 2026-10-21 14:41 |
| `session-service` | [#61](https://github.com/cBioPortal/session-service/pull/61) | 2026-10-21 14:43 |
| `cbioportal-docker-compose` | [#100](https://github.com/cBioPortal/cbioportal-docker-compose/pull/100) | 2026-10-21 14:45 |
| `cbioportal` | [#12392](https://github.com/cBioPortal/cbioportal/pull/12392) | 2026-10-21 16:28 |

**Switch release:** [TBD]. The latest releases seen were published before these merges (backend/frontend v7.2.1 on 2026-10-20 05:35 UTC; core v1.0.17, session-service v0.6.5 earlier), so no published release yet contains the switch. Decide the version, tag it (signed, pointing at this record) and record it here.

## 2. Gate checklist ([relicensing#5](https://github.com/cBioPortal/relicensing/issues/5))

| Item | Status | Evidence |
|---|---|---|
| Component/release manifest, incl. combined-distribution effective license | Done | [component-manifest.md](component-manifest.md) |
| Final SBOM / dependency resolution | Done, with open follow-ups | [dependency-audit.md](dependency-audit.md); GPL frontend deps replaced ([frontend#5746](https://github.com/cBioPortal/cbioportal-frontend/pull/5746), [#5747](https://github.com/cBioPortal/cbioportal-frontend/pull/5747)). Open: full Maven transitive scan, `mysql-connector-j` confirmation, stale OPEN-SOURCE-DOCUMENTATION ([#12268](https://github.com/cBioPortal/cbioportal/issues/12268)) |
| Consent matrix and ≥95% reconciliation | Done | [contributor-consent-status.md](contributor-consent-status.md): 98.7% overall (24,925 / 25,242 commits), every component above 95% |
| Final consent board snapshot | Done | [Board as of 2026-10-25](https://github.com/cBioPortal/relicensing/blob/main/docs/relicensing/contributor-consent-status.md) (final snapshot: link the merge commit of PR #29) |
| Unreachable-contributor disposition | Done | 126 of 209 contributors pending (about 317 commits, 1.3%). Decision: accept under the RFC's best-effort standard (98.7% coverage, above the 95% target); no rewrite or removal |
| AI-authorship determination | Done as policy; no legal opinion | Policy: treat AI-assisted commits (Claude, GitHub Copilot, any other tool) as human-authored for outreach (CLAUDE.md Decisions). **No formal legal opinion was obtained.** |
| Community notice + feedback summary, go/no-go | Done | Notice [relicensing#21](https://github.com/cBioPortal/relicensing/issues/21), Sep 18 – Oct 17. No public comments or objections received. Go decision made by JJ Gao (RFC 86 owner), executed with the switch merges on 2026-10-20/21; no separate written go/no-go was recorded before the merges |
| DCO live in CI | **Not met** | DCO is not live. Required by the gate and Phase 4; tracked as a post-switch follow-up ([relicensing#7](https://github.com/cBioPortal/relicensing/issues/7)) |
| Switch release/commit decision record | **Open** | See §1 |
| Reference to private records | Done | Drive folder above |

## 3. Team-lead consent (named signatories)

Consent was obtained **at the team-lead level, not through formal institutional legal/tech-transfer review**. This is a documented, deliberate choice made to fit the timeline (CLAUDE.md Decisions). The trade-off is that a lead may lack authority to bind their organization; each comment carries an authority attestation. PMCC is the exception, with consent from UHN Legal Counsel.

| Team | Signatory | Date | Evidence |
|---|---|---|---|
| MSKCC | Nikolaus Schultz | 2026-07-31 | [comment](https://github.com/cBioPortal/relicensing/issues/25#issuecomment-5682138010) |
| The Hyve | Henk-Jan van den Ham | 2026-08-19 | [comment](https://github.com/cBioPortal/relicensing/issues/25#issuecomment-5682138143) |
| Bilkent U | Ugur Dogrusoz | 2026-08-20 | [comment](https://github.com/cBioPortal/relicensing/issues/25#issuecomment-5682138218) |
| PMCC | Michael Migus, UHN Legal Counsel (cc Trevor Pugh) | 2026-08-27 | [summary comment](https://github.com/cBioPortal/relicensing/issues/25#issuecomment-5682138303); original in private Drive |
| Caris | Priti Kumari | 2026-09-01 | [comment](https://github.com/cBioPortal/relicensing/issues/25#issuecomment-5682138385) |
| SE4BIO | Pieter Lukasse (scoped to contributions SE4BIO owns) | 2026-09-02 | [comment](https://github.com/cBioPortal/relicensing/issues/25#issuecomment-5682138454) |
| DFCI | James Lindsay | 2026-09-02 | [comment](https://github.com/cBioPortal/relicensing/issues/25#issuecomment-5682138532) |
| CHOP | Yuankun Zhu | 2026-09-21 | [comment](https://github.com/cBioPortal/relicensing/issues/25#issuecomment-5765069676) |

Note: CHOP's lead was previously recorded as Adam Resnick. Yuankun Zhu has been confirmed as the CHOP team lead for this purpose.

## 4. Effective license of the combined/served distribution

After the switch, the served distribution bundles the Apache-2.0 backend, frontend, importer and session service. The vendored copyleft assets found in legacy webapp assets (3 GPL, 2 LGPL; see the manifest) have been removed or excluded, so the combined distribution is Apache-2.0 plus permissively licensed third-party code. Add the removal evidence (PR or commit links) here before signing.

## 5. Known deviations and follow-ups

- Switch merged before this gate was signed (see top).
- Docker-compose PR carried a "DO NOT MERGE before relicensing#5" label when merged.
- `cbioportal-helm` is in scope (listed in the notice) and was switched via [cbioportal-helm#26](https://github.com/cBioPortal/cbioportal-helm/pull/26), merged 2026-10-26. It is outside the five repos on the consent board; its two contributors (`zainasir`, `inodb`) have both consented.
- Leftover AGPL headers found by a repo-wide grep were fixed in [cbioportal#12452](https://github.com/cBioPortal/cbioportal/pull/12452) and [cbioportal-core#210](https://github.com/cBioPortal/cbioportal-core/pull/210) [TBD — confirm merged].
- The notice promised a `NOTICE` file at the switch commit. None was created; Apache-2.0 does not require one. The notice text should be corrected.
- Phase 5: DCO, license scanning in CI ([relicensing#7](https://github.com/cBioPortal/relicensing/issues/7)).

## 6. Sign-off

| Name | Role | Date |
|---|---|---|
| JJ Gao | RFC 86 owner | 2026-10-25 |
