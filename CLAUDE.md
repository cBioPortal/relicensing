# cBioPortal Relicensing — RFC 86

## Project Goal

Transition cBioPortal's open source license from **AGPL** to **Apache 2.0**.

## Why

- **Funder requirements**: NCI ITCR and Chan Zuckerberg Initiative (CZI) explicitly require permissive licenses (Apache 2.0, MIT, BSD). This was flagged ~4 years ago at award renewal.
- **Adoption barriers**: AGPL's "viral" reputation has deterred pharma, biotech, and tech adopters even when the concern is not technically warranted.
- **Patent clarity**: Apache 2.0 includes an explicit patent grant + retaliation clause, which is required by many corporate legal teams. MIT is silent on patents.
- **Competitive risk reassessed**: The original AGPL rationale (prevent competitive forks) is considered low risk given current ecosystem dynamics and cheaper software generation.

## License Choice: Apache 2.0

Chosen over MIT because Apache 2.0 provides explicit patent grants — critical for corporate/industry adoption. Kubernetes and similar large platforms use it.

## Implementation Phases

### Phase 0 — Release & Component Scope
- Define a public component/release manifest
- Scope spans: backend repo, `cbioportal-frontend`, Docker images, `cbioportal-docker-compose`, docs/site, sample/test data, DB scripts
- The SBOM denominator (Phase 1) and contributor-consent denominator (Phase 2's ≥95%) must cover all in-scope repos/components
- Combined distribution (e.g., Docker image bundling Apache backend + AGPL frontend) remains AGPL until all components relicense

### Phase 1 — Compliance & Dependency Audit
- Full Software Bill of Materials (SBOM) of all third-party dependencies
- Identify any upstream AGPL-licensed libraries ("infection" risk)
- Identify/remove obsolete code from unreachable contributors
- Preliminary analysis: https://github.com/cBioPortal/cbioportal/pull/12125

### Phase 2 — Contributor Outreach & Consent
- No prior CLA exists — must get consent from all copyright holders
- **Tier 1**: Formal written approval from lead institutions: MSKCC, DFCI, PMCC, CHOP, Hyve, SE4BIO, top individual contributors
- **Tier 2**: Standardized outreach to all contributors in git history
- "Best Effort" standard: reach 95% of codebase by volume; rewrite remaining 5% if needed
- Maintain a public "Vanish List" of unreachable contributors

### Phase 3 — Community Feedback & Notice Period
- 30-day public RFC / "Notice and Comment" period on GitHub + mailing list
- Allow downstream users and community to raise concerns

### Pre-Switch Sign-off Gate
- Hard blocker before Phase 4
- Consolidates the signed relicensing record
- Must assert an **effective license for the combined/served distribution**, not only per-artifact licenses

### Phase 4 — Technical Execution
- Define a "Switch Commit" tied to a specific release (e.g., v6.0)
- Code before the commit = AGPL; code after = Apache 2.0
- Run automated script to update license headers in all source files
- Update: LICENSE file, README.md, project website, CI/CD metadata
- Create NOTICE file (required by Apache 2.0) preserving original AGPL attributions

### Phase 5 — Future Governance
- Adopt **Developer Certificate of Origin (DCO)** with GitHub CI enforcement
- Integrate automated license scanning (FOSSA or Snyk) into CI pipeline

## Key Risks

| Risk | Notes |
|------|-------|
| Upstream AGPL dependency | If cBioPortal depends on AGPL libraries it doesn't own, those modules may need to stay AGPL or be replaced |
| Contributor consent | Some contributors may be unreachable; "best effort" + rewrite strategy applies |
| Stakeholder pushback | Some may perceive license change as loss of control |
| Legal/compliance complexity | Careful legal review required |
| AI authorship claims | `Co-Authored-By: Claude` tags in git history (e.g., PR #12014) — current US Copyright Office guidance: AI cannot hold copyright, but warrants monitoring |

## Key References

- RFC document: `RFC86.docx` (in this folder)
- Preliminary SBOM/dependency PR: https://github.com/cBioPortal/cbioportal/pull/12125
- AI authorship PR: https://github.com/cBioPortal/cbioportal/pull/12014

## GitHub Issues

Tracked in [cBioPortal/relicensing](https://github.com/cBioPortal/relicensing) (moved 2026-07-10 from cBioPortal/cbioportal via native GitHub issue transfer — old cbioportal issue URLs auto-redirect to the new location; comments, labels, and the epic/sub-issue hierarchy were preserved).

| Issue | # |
|-------|---|
| Epic | [#8](https://github.com/cBioPortal/relicensing/issues/8) |
| Phase 0: Release & Component Scope | [#1](https://github.com/cBioPortal/relicensing/issues/1) |
| Phase 1: Compliance & Dependency Audit | [#2](https://github.com/cBioPortal/relicensing/issues/2) |
| Phase 2: Contributor Outreach & Consent | [#3](https://github.com/cBioPortal/relicensing/issues/3) |
| Phase 3: Community Feedback & Notice Period | [#4](https://github.com/cBioPortal/relicensing/issues/4) |
| Pre-Switch Sign-off Gate | [#5](https://github.com/cBioPortal/relicensing/issues/5) |
| Phase 4: Technical Execution | [#6](https://github.com/cBioPortal/relicensing/issues/6) |
| Phase 5: Future Governance | [#7](https://github.com/cBioPortal/relicensing/issues/7) |

## Decisions

- **AI authorship (2026-05-19):** Treat AI-assisted commits (e.g. `Co-Authored-By: Claude` tags) as human-authored for contributor outreach. Most conservative/comprehensive baseline. Revisit only if legal review suggests otherwise.

## Current Status

- [x] Project setup complete (CLAUDE.md, memory)
- [x] GitHub Epic + 7 phase/gate issues created
- [x] Issues moved to dedicated cBioPortal/relicensing repo (2026-07-10)
- [ ] Phase 0: Release & Component Scope (#1) — not started
- [ ] Phase 1: Compliance & Dependency Audit (#2) — blocked on Phase 0
- [ ] Phase 2: Contributor Outreach & Consent (#3) — blocked on Phase 1
- [ ] Phase 3: Community Feedback (#4) — blocked on Phase 2
- [ ] Pre-Switch Sign-off Gate (#5) — blocked on Phase 3
- [ ] Phase 4: Technical Execution (#6) — blocked on sign-off gate
- [ ] Phase 5: Future Governance (#7) — blocked on Phase 4

## Working Conventions

- Track GitHub issues with an Epic for the overall relicensing + child issues per phase
- Report progress to the team via Slack
- Store decisions and status updates in memory and in this file
