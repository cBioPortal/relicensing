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
- **Draft v1 manifest published (2026-07-10):** [`docs/relicensing/component-manifest.md`](docs/relicensing/component-manifest.md), based on direct repo inspection (docker-compose image pins, backend `pom.xml`, its generated `OPEN-SOURCE-DOCUMENTATION` file, contributor counts). Headline findings: `session-service` and `cbioportal-core` (the data importer) have **no license at all** today, independent of AGPL/Apache; 5 vendored copyleft components (3 GPL, 2 LGPL, no AGPL) found in legacy webapp assets; several docs/manual/API-spec repos are stale and marked historical only; `datahub` tracked as a separate data-licensing question, out of this scope. See the manifest for open follow-ups.

### Phase 1 — Compliance & Dependency Audit
- Full Software Bill of Materials (SBOM) of all third-party dependencies
- Identify any upstream AGPL-licensed libraries ("infection" risk)
- Identify/remove obsolete code from unreachable contributors
- Preliminary analysis: https://github.com/cBioPortal/cbioportal/pull/12125 (closed 2026-07-10, superseded by the audit doc below — findings fully incorporated)
- **Draft v1 audit published (2026-07-10):** [`docs/relicensing/dependency-audit.md`](docs/relicensing/dependency-audit.md). Two real GPL-3.0-only frontend blockers confirmed in use (`react-column-resizer` in the core `LazyMobXTable` component, `react-json-to-table` in one tooltip) — resolution decided: reimplement in-house, tracked as [cbioportal#12266](https://github.com/cBioPortal/cbioportal/issues/12266) and [#12267](https://github.com/cBioPortal/cbioportal/issues/12267). Backend's flagged `mysql-connector-j` (GPL+Universal FOSS Exception) likely isn't an actual blocker. The backend's own `OPEN-SOURCE-DOCUMENTATION` third-party report is stale (4 of 5 previously-flagged copyleft entries no longer exist in the repo) — needs regeneration. `cbioportal-core`/`session-service` dependency trees are clean. Full transitive Maven dependency resolution has still never actually been completed for the backend.

### Phase 2 — Contributor Outreach & Consent
- No prior CLA exists — must get consent from all copyright holders
- **Tier 1**: Written approval from the **institutional/team lead** of the cBioPortal team at each lead institution — MSKCC, DFCI, PMCC, CHOP, Hyve, SE4BIO — signed at the team-lead level rather than routed through formal legal/tech-transfer review, to fit the timeline. Letter explicitly invites the lead to redirect to legal if their institution requires it. See Decisions section below.
- **Tier 2**: Standardized outreach to all contributors in git history, and to top individual contributors regardless of institutional affiliation
- "Best Effort" standard: reach 95% of codebase by volume; rewrite remaining 5% if needed
- Maintain a **public consent status board** (per-contributor agreed/pending/declined/unreachable, no raw contact info) — precedent: [mpv's LGPL relicensing](https://github.com/mpv-player/mpv/issues/2033) used a public wiki page for this. The redacted "Vanish List" is a filtered view of this board (unreachable rows only), not a separate artifact.

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

## Timeline

**Hard deadline: 2026-09-30.** This is aggressive relative to precedent — mpv's comparable GPL→LGPL relicensing ([mpv-player/mpv#2033](https://github.com/mpv-player/mpv/issues/2033)) took 4+ years on a smaller codebase. Hitting it requires running phases in parallel rather than the strictly serial chain the phase numbering implies, plus firm deadlines on contributor outreach. Backward-planned schedule from the 82-day budget (2026-07-10 → 2026-09-30):

| Track | Window | Notes |
|---|---|---|
| Phase 0 (scope) | Jul 10–17 | Fast — scope is largely already known |
| Phase 1 (SBOM/audit) | Jul 10–28 | Starts in parallel with Phase 0 on known components |
| Phase 2 — Tier 1 outreach | launch Jul 13, target resolved Jul 24 | Team-lead sign-off (not formal legal review, see Decisions) — should turn around in ~1-2 weeks since leads are already engaged collaborators |
| Phase 2 — Tier 2 outreach | launch Jul 28, firm deadline Aug 18, reconciliation by Aug 20 | Firm 3-week window; non-responders default to rewrite/remove, not indefinite waiting |
| Phase 3 (30-day notice) | Aug 21 – Sep 20 | Fixed at 30 days — not compressible, everything else fits around this |
| Sign-off Gate | Sep 20–23 | Fast if the record is assembled continuously through Phases 1–3, not started here |
| Phase 4 (Switch Commit) | Sep 23–30 | Fast if SPDX header scripts/tooling are dry-run tested during the Phase 1 window |

**Critical path risk:** with Tier 1 moved to team-lead sign-off, the remaining critical path is **Phase 1 cleanup finishing on time (Jul 28) and Tier 2's firm 3-week outreach window (Jul 28 – Aug 18)** — those now gate Phase 3's fixed 30-day window, which cannot be compressed to absorb a slip. The Jul 24–Aug 20 gap also now acts as schedule buffer for any Tier 1 straggler or minor Tier 2 slippage.

## Key Risks

| Risk | Notes |
|------|-------|
| Upstream AGPL dependency | If cBioPortal depends on AGPL libraries it doesn't own, those modules may need to stay AGPL or be replaced |
| Contributor consent | Some contributors may be unreachable; "best effort" + rewrite strategy applies |
| **Aggressive timeline** | Hard 2026-09-30 deadline vs. mpv's 4-year precedent for a comparable effort; critical path is now Phase 1 cleanup + Tier 2 outreach — see Timeline section |
| **Team-lead sign-off authority** | Tier 1 consent is signed by institutional/team leads, not formal legal/tech-transfer review — faster, but weaker legal footing if a lead lacks actual authority to bind their institution. See Decisions. |
| Stakeholder pushback | Some may perceive license change as loss of control |
| Legal/compliance complexity | Careful legal review required |
| AI authorship claims | Larger footprint than the single PR #12014 example: 31/52/1/0 `Co-Authored-By: Claude` commits and 31/42/1/0 Copilot-authored PRs across cbioportal/cbioportal-frontend/cbioportal-core/session-service respectively (per Phase 1 audit, 2026-07-10). Current US Copyright Office guidance: AI cannot hold copyright, but warrants monitoring. Policy now explicitly covers all AI tools, not just Claude — see Decisions. |

## Key References

- RFC document: `RFC86.docx` (in this folder)
- Preliminary SBOM/dependency PR: https://github.com/cBioPortal/cbioportal/pull/12125 (closed 2026-07-10, superseded by `docs/relicensing/dependency-audit.md`)
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

- **AI authorship (2026-05-19, extended 2026-07-10):** Treat AI-assisted commits as human-authored for contributor outreach. Originally scoped to `Co-Authored-By: Claude` tags; **extended 2026-07-10 to cover all AI coding tools** (confirmed footprint includes GitHub Copilot — 31/42/1/0 Copilot-authored PRs across cbioportal/cbioportal-frontend/cbioportal-core/session-service, per the Phase 1 audit — plus Claude, and any other AI agent found later). Most conservative/comprehensive baseline. Revisit only if legal review suggests otherwise.
- **Tier 1 sign-off level (2026-07-10):** Get Tier 1 institutional consent from each institution's cBioPortal team lead/PI directly, rather than routing through formal legal/tech-transfer review. Rationale: this is a non-commercial, mission-aligned open source tool, not a contested IP matter, and team leads can turn around a signature far faster than a legal department — necessary to hit the 2026-09-30 deadline. Trade-off: a team lead may not have actual authority to bind their institution; mitigated by having the letter (`outreach_tier1_letter.md`) explicitly invite redirection to legal if the lead's institution requires it, and by an explicit authority attestation in the signed consent. Revisit for any institution where this basis feels shaky.
- **Adjacent AGPL tooling out of scope (2026-07-10):** `cancerhotspots`, `datahub-study-curation-tools`, `clinical-data-normalization`, `fmi-converter`, and `clinical-data-dictionary` — real, actively-maintained, currently-AGPL cBioPortal repos, but not bundled into the docker-compose/Helm deployment — are kept separate from RFC86. They stay AGPL (or unlicensed) for now; candidates for a possible future relicensing wave, not this one. See `docs/relicensing/component-manifest.md`.

## Current Status

- [x] Project setup complete (CLAUDE.md, memory)
- [x] GitHub Epic + 7 phase/gate issues created
- [x] Issues moved to dedicated cBioPortal/relicensing repo (2026-07-10)
- [x] Phase 0: Release & Component Scope (#1) — closed 2026-07-10. Manifest at `docs/relicensing/component-manifest.md`. Two non-blocking product decisions remain open (cbioportal-core version pinning, Helm chart currency vs. docker-compose)
- [ ] Phase 1: Compliance & Dependency Audit (#2) — draft v1 audit published 2026-07-10 (`docs/relicensing/dependency-audit.md`). Code-change follow-ups tracked as cbioportal#12266–12269. Non-code follow-ups (npm scan, full Maven transitive resolution, mysql-connector-j legal confirmation) remain, proceeding in parallel with Phase 2 rather than blocking it
- [ ] Phase 2: Contributor Outreach & Consent (#3) — starting 2026-07-10 in parallel with Phase 1's remaining non-code follow-ups
- [ ] Phase 3: Community Feedback (#4) — blocked on Phase 2
- [ ] Pre-Switch Sign-off Gate (#5) — blocked on Phase 3
- [ ] Phase 4: Technical Execution (#6) — blocked on sign-off gate
- [ ] Phase 5: Future Governance (#7) — blocked on Phase 4

## Working Conventions

- Track GitHub issues with an Epic for the overall relicensing + child issues per phase
- Report progress to the team via Slack
- Store decisions and status updates in memory and in this file
