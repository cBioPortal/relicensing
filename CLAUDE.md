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
- **Team lead consent**: Written approval from the **team lead** of the cBioPortal team at each contributing organization — MSKCC, DFCI, PMCC, CHOP, Hyve, SE4BIO, Bilkent University, Caris — at the team-lead level rather than routed through formal legal/tech-transfer review, to fit the timeline. Consent collected via [cbioportal#12282](https://github.com/cBioPortal/cbioportal/issues/12282). See Decisions section below.
- **Individual contributor outreach**: Standardized outreach to all contributors in git history, and to top individual contributors regardless of organizational affiliation
- "Best Effort" standard: reach 95% of codebase by volume; rewrite remaining 5% if needed
- Maintain a **public consent status board** (per-contributor agreed/pending/declined/unreachable, no raw contact info) — precedent: [mpv's LGPL relicensing](https://github.com/mpv-player/mpv/issues/2033) used a public wiki page for this. The redacted "Vanish List" is a filtered view of this board (unreachable rows only), not a separate artifact.
- **Board published (2026-07-10):** [`docs/relicensing/contributor-consent-status.md`](docs/relicensing/contributor-consent-status.md) — 209 contributors across all 5 in-scope repos, built from public data only (no private contact info). Enriched with contribution-time names (from public git commit history) and organizations (from commit-email domains — institution name only, never the raw email).
- **Public consent-collection issue (2026-07-10, opened early):** [cBioPortal/cbioportal#12271](https://github.com/cBioPortal/cbioportal/issues/12271), mirroring mpv's approach directly — a single public issue where any contributor can comment their consent, in addition to replying individually. Hosted in the main `cbioportal` repo (not `relicensing`) for maximum organic visibility, same reasoning as mpv.

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
| Phase 2 — Team lead consent | launch Jul 31, deadline Aug 31 | Team-lead sign-off via [cbioportal#12282](https://github.com/cBioPortal/cbioportal/issues/12282); runs in parallel with Phase 3 tail |
| Phase 2 — Individual contributor outreach | launch Jul 28, deadline Sep 20 | Runs in parallel with Phase 3; closes when notice period ends |
| Phase 3 (30-day notice) | Aug 21 – Sep 20 | Runs in parallel with tail of Phase 2 outreach; fixed at 30 days |
| Sign-off Gate | Sep 20–23 | Fast if the record is assembled continuously through Phases 1–3, not started here |
| Phase 4 (Switch Commit) | Sep 23–30 | Fast if SPDX header scripts/tooling are dry-run tested during the Phase 1 window |

**Critical path:** Phase 3's 30-day window is fixed (Aug 21 – Sep 20) and cannot be compressed. Phase 2 individual outreach runs in parallel and closes Sep 20; any non-responder by that date defaults to rewrite/remove. Team lead consent (deadline Aug 31) provides an additional coverage layer before the notice period ends.

## Key Risks

| Risk | Notes |
|------|-------|
| Upstream AGPL dependency | If cBioPortal depends on AGPL libraries it doesn't own, those modules may need to stay AGPL or be replaced |
| Contributor consent | Some contributors may be unreachable; "best effort" + rewrite strategy applies |
| **Aggressive timeline** | Hard 2026-09-30 deadline vs. mpv's 4-year precedent for a comparable effort; critical path is now Phase 1 cleanup + individual contributor outreach — see Timeline section |
| **Team-lead sign-off authority** | Team lead consent is collected directly (not formal legal/tech-transfer review) — faster, but weaker legal footing if a lead lacks actual authority to bind their team's contributions. See Decisions. |
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
- **Team lead sign-off level (2026-07-10, updated 2026-07-31):** Get team lead consent from each cBioPortal team lead/PI directly, rather than routing through formal legal/tech-transfer review. Collected via public GitHub issue [cbioportal#12282](https://github.com/cBioPortal/cbioportal/issues/12282) (same mechanism as individual contributor consent — terms and consent statement are inline in the issue body). Rationale: non-commercial, mission-aligned open source tool; team leads can respond far faster than a legal department — necessary to hit the 2026-09-30 deadline. Trade-off: a team lead may not have actual authority to bind their organization; mitigated by an explicit authority attestation in their consent comment. Revisit for any team where this basis feels shaky.
- **Adjacent AGPL tooling out of scope (2026-07-10):** `cancerhotspots`, `datahub-study-curation-tools`, `clinical-data-normalization`, `fmi-converter`, and `clinical-data-dictionary` — real, actively-maintained, currently-AGPL cBioPortal repos, but not bundled into the docker-compose/Helm deployment — are kept separate from RFC86. They stay AGPL (or unlicensed) for now; candidates for a possible future relicensing wave, not this one. See `docs/relicensing/component-manifest.md`.
- **Repo stays public; sensitive originals go elsewhere (2026-07-11):** Considered and rejected making `cBioPortal/relicensing` private to hold sensitive records. Reasons: the live public consent issues ([cbioportal#12282](https://github.com/cBioPortal/cbioportal/issues/12282) for Tier 1 team leads, [cbioportal#12271](https://github.com/cBioPortal/cbioportal/issues/12271) for Tier 2 individuals) link directly into this repo; Phase 3 already commits to a public 30-day notice period; and the whole Phase 2 design deliberately mirrors mpv/VLC/Dolphin's public-transparency approach. Instead, any legal correspondence and other documents with sensitive details are stored in a private Google Drive folder: https://drive.google.com/drive/folders/1pGq4cS1S_gKhCsOsIO7sTEo5IQ9i4pTI — the public record (sign-off gate, relicensing#5) links to this folder as the location of record, without embedding the documents themselves.
- **Live consent records are sensitive (2026-07-31):** Treat `cbioportal#12282`, `cbioportal#12271`, and `docs/relicensing/contributor-consent-status.md` as live records. Preserve recorded consents exactly; make only surgical edits when needed, and avoid broad rewrites that could alter or obscure existing consent entries.
- **Current live entries (2026-07-31):** Initial recorded consents include Nikolaus Schultz in `cbioportal#12282` and JJ Gao in `cbioportal#12271`. Preserve those entries exactly when making future edits.
- **PMCC team lead consent via institutional legal counsel (2026-09-01):** UHN (University Health Network — PMCC's parent institution) sent written consent by email rather than commenting on `cbioportal#12282` directly, using the issue's stated "email instead" option. Consent came from Michael Migus, UHN Legal Counsel, dated 2026-08-27, cc'ing team lead Trevor Pugh, citing UHN's IP Protection & Commercialization Policy (UHN owns/manages IP from its personnel, so UHN — not the individual team lead — has authority to consent). This is a *stronger* legal basis than the direct team-lead-attestation mechanism used for other orgs (see the team-lead sign-off risk above), since it comes from an entity with explicit institutional authority rather than a lead's own attestation. Recorded publicly via a summary comment posted on the user's behalf: [cbioportal#12282 comment](https://github.com/cBioPortal/cbioportal/issues/12282#issuecomment-5497278496) (content only — the original email itself was not committed to the public repo, per the sensitive-originals decision above; the user has since moved the source PDF to the gitignored `data/` folder locally — no upload tool available for Claude to push it to the private Drive folder directly, so final Drive archival is still on the user). Status board and issue body both updated to reflect PMCC as agreed, including the two PMCC individual contributors (jagnathan, morungos), whose consent is covered by this team-lead-level agreement.
- **Comprehensive consent reconciliation pass (2026-09-01):** Swept every consent channel (both GitHub issues in full, and the full `#relicensing-consent` Slack channel history — 50 messages, 2026-08-17 to 2026-08-26) against the board and the private `data/contributor_matrix.tsv`. Real deltas found and applied: Bilkent U team lead consent (Ugur Dogrusoz, `cbioportal#12282` comment `5350502520`, was sitting unreflected in both the issue table and the board — user caught this one directly), which also covers 3 individual Bilkent U contributors; a genuine new individual consent for Charles Haynes (CHOP, via Slack — CHOP still has no team-lead consent); and a few corroborating citations added where someone had a personal consent in addition to team-lead coverage. **Methodology finding:** the GitHub `search/commits?q=author-email:...` API is unreliable for verifying whether a Slack consent-responder is an actual contributor — it returned 0 hits even for a contributor with 141 real commits. The reliable check is the plain per-repo `GET /repos/{owner}/{repo}/commits?author=<email>` endpoint across all 5 in-scope repos. Using the reliable method, ~34 Slack/GitHub consent-responders across two reconciliation passes (2026-08-18 and 2026-09-01) were confirmed to have **zero commits** in any in-scope repo — people from partner institutions who joined the outreach channel and consented without ever having contributed code (see `data/consent-processing-checkpoint.json` and `data/consent-responders-not-on-board.md`, both private/gitignored). No board changes made for these — nothing on record for them to consent to.
- **Caris added as an 8th team-lead org (2026-09-01):** Priti Kumari (Director, Scientific Data Management, Caris Life Sciences) consented on behalf of Caris in `cbioportal#12282` ([comment](https://github.com/cBioPortal/cbioportal/issues/12282#issuecomment-5500479290)) — the user added the row to the issue body directly. Propagated everywhere the 7-org list appeared: `cbioportal#12282` table (pending → agreed), `relicensing#3`, this file's org list (which was also separately missing Bilkent University — fixed at the same time), and `docs/relicensing/outreach-individual-template.md`. Found one existing board contributor genuinely affiliated with Caris — `qlu-cls` (Qi-Xuan Lu, `qlu@carisls.com`, 32 commits) — now covered via the team-lead consent; reassigned their Team column from blank to `Caris`. Priti Kumari's own board row (`priti88`, 10 commits, 2015-2016) was left labeled `DFCI` (her historical GitHub-company-field affiliation at contribution time — not reassigned, per the "don't touch historical labels without evidence" convention) but marked consented individually, since her comment is in substance her own attestation for her own past contributions regardless of which org box it's filed under. The user separately confirmed Priti is also partly DFCI (consistent with the above — no change needed), and that `kalletlak` (Karthik Kalletla, CHOP, 663 commits — the single largest pending individual contributor) is partly Caris and partly CHOP; his commits are all under a personal Gmail address with no institutional domain, so there's no way to split Caris-era vs. CHOP-era commits from git history alone. **Resolved 2026-09-01:** user decided to assign him to CHOP outright ("vast majority of his work were at chop") rather than pursue a formal split. He stays `pending`/CHOP — CHOP still has no team-lead consent, so this is unaffected by the Caris consent; still needs CHOP's team lead (Adam Resnick) or Karthik's own individual consent.
- **DFCI and SE4BIO team-lead consent; 95% threshold crossed (2026-09-02):** James Lindsay (Senior Director, Knowledge Systems Group, Dept. of Data Science, DFCI) consented for DFCI in [cbioportal#12282](https://github.com/cBioPortal/cbioportal/issues/12282#issuecomment-5514014842), and Pieter Lukasse consented for SE4BIO ([comment](https://github.com/cBioPortal/cbioportal/issues/12282#issuecomment-5511327507), scoped to contributions "for which SE4BIO has the copyright"). Team leads now **7/8 agreed — only CHOP (Adam Resnick) remains**. This closed 1,601 uncovered commits at once (DFCI 1,355 + SE4BIO 246) and pushed overall commit-volume coverage from 89.4% to **95.8% (24,162/25,227) — the first time the RFC's 95% "best effort" target has been met**. Caveat: two components are still individually below 95% (frontend 93.7%, session-service 91.8%, docker 94.6%), so the aggregate number should not be read as per-component sign-off. Remaining gap is CHOP's 675 uncovered commits (663 of them `kalletlak` alone) plus 373 from unaffiliated individuals — CHOP team-lead consent is now the single highest-leverage remaining item. Slack `#relicensing-consent` was **not** swept this run (the claude.ai Slack MCP connector was unauthenticated), so its checkpoint is unchanged and the next run should re-check from ts `1787765627.664229`.

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

## Consent Update Playbook

When asked to "update consent" (or similar), run this end-to-end — no need to re-scope the task from scratch:

1. **Pull every consent source since the last run.** Check `data/consent-processing-checkpoint.json` (gitignored) for `last_processed_ts` (Slack) and `last_processed_at`/`last_processed_comment_id` (GitHub) from the most recent run, then fetch only what's newer:
   - `cbioportal#12282` (team lead) — `gh api repos/cBioPortal/cbioportal/issues/12282/comments`
   - `cbioportal#12271` (individual) — `gh api repos/cBioPortal/cbioportal/issues/12271/comments`
   - Slack `#relicensing-consent` (channel ID `C0BQW0PPASV`) — search or read the channel for messages after the checkpoint's `last_processed_ts`
   - Also check for a direct email (PDF/forward) if the user mentions one, per the PMCC/UHN precedent
2. **Match each new consent to a contributor.** Use `data/contributor_matrix.tsv` (gitignored — `email`/`slack_email` columns) to resolve a name/email to a GitHub login. If no match, don't guess — verify with `gh api "repos/cBioPortal/<repo>/commits?author=<email-or-login>"` across all 5 in-scope repos (`cbioportal`, `cbioportal-frontend`, `cbioportal-docker-compose`, `cbioportal-core`, `session-service`).
   - **Do not use `gh api search/commits` with an `author-email:` filter** — confirmed unreliable (false negatives even for real contributors with 100+ commits; see the "Comprehensive consent reconciliation pass" entry in Decisions above). Use the plain per-repo `commits?author=` endpoint instead.
   - A genuine team-lead consent covers every individual contributor from that org (update their row's `Effective Consent` to `yes²`, citing the team-lead comment).
   - Zero commits across all 5 repos → not an in-scope contributor. No board row. Log them in `data/consent-responders-not-on-board.md` instead so they aren't re-checked next time.
3. **Apply surgical edits only** to `docs/relicensing/contributor-consent-status.md` and the two GitHub issue bodies (team-lead table in `#12282`) — per the "live consent records are sensitive" decision, don't do broad rewrites.
4. **Recompute and refresh the Summary section** at the top of the board (organization table → coverage-by-commit-volume table → individual contributor consent counts, in that order) and the two progress-count lines in `README.md` ("Team leads: X/7 agreed", "Individual contributors: Y/208 agreed").
5. **Update the checkpoint file** (`data/consent-processing-checkpoint.json`) with the new `last_processed_ts`/`last_processed_at` and a summary of what changed, so the next run only looks at the delta.
6. **Before publishing:** run a privacy scan (regex for email-shaped strings) on the public board file — it must stay clean.
7. **Ship it as a PR** (branch off `main`, commit, push, `gh pr create`) rather than committing straight to `main` — matches how the last two rounds were done (PR #14, #15).
