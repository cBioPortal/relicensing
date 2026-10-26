# DRAFT — Announcement: cBioPortal is now Apache-2.0

> Draft for review. Items marked **[TBD]** need a decision or a fact only the team can supply. Intended channels: cBioPortal blog/news, mailing list, Slack, GitHub Discussion, and a closing comment on [relicensing#21](https://github.com/cBioPortal/relicensing/issues/21).

---

## cBioPortal is moving from AGPL-3.0 to Apache-2.0

**Date:** [TBD — publication date]

cBioPortal's core software is now licensed under the **Apache License 2.0**. This completes [RFC 86](https://github.com/cBioPortal/relicensing/issues/8), which we opened for public comment from September 18 to October 17, 2026.

### What changed

| Repository | Before | Now |
|---|---|---|
| `cbioportal` (backend) | AGPL-3.0 | Apache-2.0 |
| `cbioportal-frontend` | AGPL-3.0 | Apache-2.0 |
| `cbioportal-core` (data importer) | no license | Apache-2.0 |
| `session-service` | no license | Apache-2.0 |
| `cbioportal-docker-compose` | no license | Apache-2.0 |
| `cbioportal-helm` | no license | Apache-2.0 |

The new license applies to code from the switch commit onward, in release **[TBD — first release containing the switch]**. Releases published before that remain available under the license they were distributed with (AGPL-3.0 for the backend and frontend). Nothing about those earlier releases changes.

### Why

- **Funder requirements.** NCI ITCR and the Chan Zuckerberg Initiative require permissive licenses.
- **Adoption.** AGPL's reputation has deterred pharma, biotech and tech adopters, even where its obligations would not have applied to them.
- **Patent clarity.** Apache-2.0 includes an explicit patent grant and a retaliation clause, which many corporate legal teams require.
- **Lower competitive risk.** The original reason for AGPL, preventing competitive forks, is now judged low-risk.

### How we got consent

cBioPortal has never had a contributor license agreement, so we asked the copyright holders directly:

- **All 8 contributing teams** gave written consent through their team lead: MSKCC, DFCI, PMCC (via UHN Legal Counsel), CHOP, The Hyve, SE4BIO, Bilkent University and Caris.
- **Individual contributors** were invited to consent publicly on [relicensing#24](https://github.com/cBioPortal/relicensing/issues/24). 83 of 209 contributors have consented personally or through their team.
- Together these cover **98.7% of commits** across the five repositories (24,925 of 25,242), above the 95% "best effort" target. The remaining 1.3% (contributors who could not be reached or did not respond) is accepted under that best-effort standard.
- The per-contributor record is public: [consent status board](https://github.com/cBioPortal/relicensing/blob/main/docs/relicensing/contributor-consent-status.md).

Team-lead consent was collected at the team-lead level rather than through formal institutional legal review, to meet the timeline. This was a deliberate choice and is recorded in the sign-off record. The exception is PMCC, whose consent came from UHN Legal Counsel.

### Dependencies

Our audit found two GPL-3.0 frontend dependencies in use, `react-column-resizer` and `react-json-to-table`. Both have been replaced with in-house implementations ([#22](https://github.com/cBioPortal/relicensing/issues/22), [#23](https://github.com/cBioPortal/relicensing/issues/23)). The full audit is in [dependency-audit.md](https://github.com/cBioPortal/relicensing/blob/main/docs/relicensing/dependency-audit.md).

### What this means for you

- **Running cBioPortal or building on it:** you may use, modify and redistribute under Apache-2.0, including in proprietary products, with attribution and the license text. The patent grant applies.
- **Contributing:** contributions are accepted under Apache-2.0. We plan to adopt a Developer Certificate of Origin (DCO) sign-off requirement and will announce it when it is enforced.
- **Using a pre-switch release:** it remains AGPL-3.0. Combined distributions, such as a Docker image mixing components, are governed by the most restrictive component license until every component has switched.

### Not covered

`datahub` (study data licensing) and adjacent tooling repositories such as `cancerhotspots` and `clinical-data-dictionary` are out of scope for this change and keep their current terms. A later wave may cover them.

### Thank you

Thanks to the contributors and team leads who responded, and to everyone who followed the notice period. Questions: [TBD — contact address or discussion link].

— The cBioPortal team

---

### Short version for Slack / mailing list

> cBioPortal (backend, frontend, importer, session service, docker-compose) is now Apache-2.0, completing RFC 86. All 8 contributing teams consented and 98.7% of commits are covered. Pre-switch releases remain AGPL. Details: [TBD link]

### Closing comment for relicensing#21

> The comment period closed 2026-10-17. No public comments or objections were received during the period. The relicense has been executed (PRs merged 2026-10-20/21). Full announcement: [TBD link]. Record: [`signoff-record.md`](https://github.com/cBioPortal/relicensing/blob/main/docs/relicensing/signoff-record.md).
