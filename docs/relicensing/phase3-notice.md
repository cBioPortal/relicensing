# RFC86 Phase 3 — Community Feedback & 30-Day Notice Period

**Status:** Notice posted 2026-09-02. Comment period open through **2026-09-20 (23:59 UTC)**. Tracked in [relicensing#4](https://github.com/cBioPortal/relicensing/issues/4).

**Notice issue (public):** [cBioPortal/cbioportal#12328](https://github.com/cBioPortal/cbioportal/issues/12328)

---

## Notice of Proposed License Change: AGPL-3.0-or-later → Apache-2.0

### Comment period

**Open:** September 2, 2026
**Close:** September 20, 2026 (23:59 UTC)

> **Timing note:** The original target opening was August 21. The notice was posted on Sep 2 because Phase 2 outreach reached the 95% threshold only recently. The Sep 20 closing date is maintained to preserve the sign-off gate timeline (Sep 20–23) and the Switch Commit window (Sep 23–30).

---

## 1. License target and rationale

Proposed change: **AGPL-3.0-or-later → Apache-2.0**, across all cBioPortal-owned components in the active distribution.

Rationale:
- Funder requirements (NCI ITCR, CZI) — permissive license required for grant renewals
- Adoption barriers — AGPL reputation deters corporate/institutional adopters even where technically unwarranted
- Patent clarity — Apache 2.0 provides an explicit patent grant + retaliation clause, required by many legal teams

---

## 2. Scope

| Repository | Current license | Action |
|---|---|---|
| `cBioPortal/cbioportal` | AGPL-3.0-or-later | Relicensed to Apache-2.0 |
| `cBioPortal/cbioportal-frontend` | AGPL-3.0-or-later | Relicensed to Apache-2.0 |
| `cBioPortal/session-service` | None | Apache-2.0 added |
| `cBioPortal/cbioportal-core` | None | Apache-2.0 added |
| `cBioPortal/cbioportal-docker-compose` | None | Apache-2.0 added |
| `cBioPortal/cbioportal-helm` | None | Apache-2.0 added |

Out of scope: `datahub` (data licensing), `cbioportal-test` (already MIT), adjacent AGPL tooling not bundled in the main distribution.

---

## 3. Pre-switch history vs. post-switch code

- Code before the Switch Commit: contributed under AGPL-3.0-or-later. Historical AGPL rights for existing recipients are preserved.
- Code at or after the Switch Commit: distributed under Apache-2.0.
- A `NOTICE` file (required by Apache-2.0) will be added to each repo at the Switch Commit, preserving AGPL-era attributions.

---

## 4. Switch timing and criteria

No specific release version pinned. The Switch Commit will be tied to the release immediately following:

1. Phase 2 consent ≥95% per component (or confirmed rewrite/remove plan for the gap)
2. Phase 1 GPL-3.0 frontend dependencies replaced (react-column-resizer, react-json-to-table)
3. This comment period (Sep 20 close)
4. Pre-switch sign-off gate ([relicensing#5](https://github.com/cBioPortal/relicensing/issues/5))

**Target:** Switch Commit on or before **2026-09-30**.

---

## 5. Dependency decisions (Phase 1)

Full audit: [`docs/relicensing/dependency-audit.md`](dependency-audit.md)

**Frontend blockers being removed:**
- `react-column-resizer` (GPL-3.0-only) — reimplemented in-house ([cbioportal#12266](https://github.com/cBioPortal/cbioportal/issues/12266))
- `react-json-to-table` (GPL-3.0-only) — reimplemented in-house ([cbioportal#12267](https://github.com/cBioPortal/cbioportal/issues/12267))

**Backend:**
- `mysql-connector-j` (GPL-2.0 + Universal FOSS Exception) — UFE permits use alongside Apache-2.0; pending legal confirmation
- Dead Flash `cytoscape_web` (LGPL) — removed ([cbioportal#12269](https://github.com/cBioPortal/cbioportal/issues/12269))
- Full transitive Maven scan — still pending

---

## 6. Consent coverage (Phase 2)

Full board: [`docs/relicensing/contributor-consent-status.md`](contributor-consent-status.md)

As of 2026-09-02:
- **Team leads:** 7/8 agreed (MSKCC, DFCI, The Hyve, PMCC, SE4BIO, Bilkent U, Caris). CHOP pending.
- **Overall coverage:** 95.8% (24,162 / 25,227 commits)
- Two components below 95%: frontend (93.7%), session-service (91.8%)
- Remaining gap: CHOP (675 commits) + unaffiliated individuals (373 commits)
- **Rewrite/remove plan:** Code from non-consenting contributors as of Sep 20 will be rewritten or removed before the Switch Commit.

---

## 7. Go/no-go

**Decision by:** September 20, 2026
**Decision-maker:** cBioPortal core team (coordinated by Nikolaus Schultz, MSKCC)
**Criteria:**
- No unresolved substantive legal or technical objection
- Phase 1 cleanup complete (or on a committed schedule)
- Per-component consent ≥95% or confirmed rewrite/remove plan
- CHOP consent received or CHOP-attributed code rewrite plan confirmed

**Decision published in:** [relicensing#4](https://github.com/cBioPortal/relicensing/issues/4) and [relicensing#5](https://github.com/cBioPortal/relicensing/issues/5)

---

## Announcement checklist

- [x] Formal notice issue posted in cbioportal/cbioportal: [cbioportal#12328](https://github.com/cBioPortal/cbioportal/issues/12328) (2026-09-02)
- [ ] Mailing list announcement (link to notice issue)
- [ ] Slack announcement (#cbioportal channel)
- [ ] Google Groups / community channels
