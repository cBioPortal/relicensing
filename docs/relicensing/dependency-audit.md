# RFC86 Phase 1 — Compliance & Dependency Audit (Draft v1)

**Status:** Draft — first pass based on direct inspection of `pom.xml`/`package.json`/`requirements.txt` files, the backend's generated `OPEN-SOURCE-DOCUMENTATION`, npm registry metadata, and the preliminary analysis in [cBioPortal/cbioportal#12125](https://github.com/cBioPortal/cbioportal/pull/12125) (closed 2026-07-10, superseded by this document — its findings are fully incorporated here). Tracked in [relicensing#2](https://github.com/cBioPortal/relicensing/issues/2). Builds on the Phase 0 manifest ([relicensing#1](https://github.com/cBioPortal/relicensing/issues/1), `component-manifest.md`).

## Summary

Two real, confirmed-in-use GPL-3.0-only dependencies in the frontend are the main blockers found so far — both resolved to a decided path: **reimplement in-house** (each is under ~130 lines, zero non-React dependencies, narrow usage). The backend's one flagged dependency (`mysql-connector-j`) is very likely resolvable via its license exception, not a true blocker. `cbioportal-core` and `session-service` are clean. The backend's own third-party license report is stale and should not be trusted as-is. AI authorship (both Claude and GitHub Copilot) is a larger footprint than previously tracked — the policy has been extended to cover all AI tools (2026-07-10).

## 1) Backend (`cbioportal`)

### Confirmed dependency: `com.mysql:mysql-connector-j:8.2.0`
- Declared license: **GPL-2.0 with the Universal FOSS Exception 1.0 (UFE)**.
- Still an active, unconditional `pom.xml` dependency (verified directly, not stale from PR #12125's original finding).
- **Likely not an actual blocker.** Oracle created the UFE specifically to allow using MySQL Connector/J alongside software under other OSI-approved licenses (including Apache-2.0), as long as the connector itself isn't modified in a way that would need to carry a conflicting license. cBioPortal uses it as an unmodified upstream dependency, which is exactly the case UFE covers.
- **Resolution path:** confirm with legal that the UFE conditions are met (should be straightforward), and add the required UFE notice into the project's `NOTICE` file (Apache-2.0 requires this either way for redistributed dependencies). Owner: TBD. Not a "replace or exclude" situation like the Phase 0 manifest's copyleft webapp assets.

### Other dual/multi-licensed transitive dependencies (from PR #12125)
Jakarta API and some Jersey/RabbitMQ-related transitive artifacts have multi-license declarations (e.g. EPL/GPL or LGPL/MPL alternatives). These are generally consumable under a permissive option but weren't individually re-verified in this pass — flagged for legal confirmation, same as PR #12125 recommended.

### Audit methodology limitation (carried over from PR #12125)
PR #12125's backend audit was **not** a full transitive Maven dependency resolution — `mvn install`/`integration-test` in that environment was blocked by an unreachable Shibboleth-hosted OpenSAML artifact host (`build.shibboleth.net`), so its findings are based on direct dependency declarations, the effective POM, and Maven Central license metadata for resolvable artifacts only. This pass didn't have network access to re-attempt full resolution either, so **the backend's transitive dependency tree has still never been fully/automatically resolved and scanned** — only the specific items already flagged (mysql-connector-j, Jakarta/Jersey/RabbitMQ) have been checked directly. This is a real gap, not just a formality — a full scan could surface additional transitive copyleft dependencies neither audit pass would have seen.

### E2E JavaScript package (from PR #12125, not independently re-verified)
`src/e2e/js/package.json` declares license `ISC`; its dependencies are common permissive packages (`axios`, `lodash`, `chai`, `mocha`, etc.). No Apache-2.0 compatibility concern.

### The backend's own `OPEN-SOURCE-DOCUMENTATION` file is stale
Of the 5 copyleft components flagged from this file in the Phase 0 manifest (3 GPL, 2 LGPL), **4 no longer exist anywhere in the current repo tree** (verified via direct git tree listing, not just code search, which can miss binary/minified files): `jquery.popeye-2.1.min`, `jslab-stdlib`, `packery.pkgd.min`, and `corejmoljsv.z` are gone. Only `cytoscape_web`'s files remain (`src/main/resources/webapp/swf/CytoscapeWeb.swf`, `cytoscapeweb.js`, and supporting ActionScript source).
- **This means the generated doc reflects a much older snapshot of the codebase and cannot be used as-is for the final SBOM.** It needs to be regenerated from the current dependency tree (whatever tool produced it originally — likely a Maven/license-report plugin — should be re-run in CI, not hand-maintained).
- The remaining `cytoscape_web` asset (LGPL) powers `netviz.jsp`'s Flash-based network visualization (referenced Java code confirmed via `src/main/resources/webapp/netviz.jsp`). **This is very likely fully dead**: Flash Player was end-of-lifed in December 2020 and removed from all major browsers — a `.swf` file cannot run anywhere today regardless of whether the JSP page is still technically reachable. Strong candidate for outright removal (Phase 1's "codebase cleanup" task) — this simultaneously resolves the one real remaining flagged copyleft asset and removes dead code.

**Recommended action:** regenerate the `OPEN-SOURCE-DOCUMENTATION` report from current `pom.xml` state (machine-readable SBOM), and separately confirm no other stale entries hide additional now-removed or now-added dependencies beyond the ones checked here.

## 2) Frontend (`cbioportal-frontend`)

The frontend does **not** have an equivalent automated full dependency-license report (its own `OPEN-SOURCE-DOCUMENTATION` file only documents two small bundled assets — a ColorBrewer color scheme and a font-detection script, both Apache-licensed — not the npm dependency tree). PR #12125's findings were spot-checked against the current `package.json` and confirmed still present:

| Package | License | Used? | Assessment |
|---|---|---|---|
| `react-column-resizer` | **GPL-3.0-only** (confirmed via npm registry) | **Yes** — `src/shared/components/lazyMobXTable/LazyMobXTable.tsx`, 2 call sites, both just `<ColumnResizer className="..." minWidth={0} />` | **Real blocker — resolution: reimplement in-house.** Inspected the actual upstream source (`nik-m2/react-column-resizer`): ~100 lines total, zero non-React dependencies. It renders a thin draggable `<td>` divider between two sibling cells and directly mutates `previousSibling.style.width`/`nextSibling.style.width` on `mousemove`/`touchmove`. cBioPortal's usage only ever passes `className` and `minWidth={0}` — never uses the library's `disabled` prop. A tailored internal component replicating exactly this behavior is low-risk, low-effort, and removes the dependency entirely (better than sourcing and vetting a third-party replacement's own license/dependency tree). |
| `react-json-to-table` | **GPL-3.0** (confirmed via npm registry) | **Yes** — `src/shared/components/studyTagsTooltip/StudyTagsTooltip.tsx`, exactly 1 call site: `<JsonToTable json={this.studyMetadata.result} />` | **Real blocker, narrow — resolution: reimplement in-house.** Inspected the actual upstream source (`thehyve/react-json-to-table` — maintained by The Hyve, one of cBioPortal's own Tier 1 institutions): ~130 lines total across 2 files, recursively renders an arbitrary JS object/array into nested HTML `<table>`s, zero non-React dependencies. The actual data passed here (study tag metadata) is a flat key-value map, so a from-scratch replacement can likely be simpler than the general-purpose original. Reimplementing is faster than a licensing negotiation given the Sep 30 deadline, even with a friendly Tier-1-adjacent maintainer. |
| `jszip` | Dual-licensed **(MIT OR GPL-3.0-or-later)** | Yes | **Not a blocker** — the project can explicitly elect the MIT option. Needs a NOTICE entry documenting that choice. |
| `webpack-raphael` (fork of `raphael`) | Upstream `raphael` is **MIT** | Yes | **Not a blocker**, assuming cBioPortal's build-tooling fork doesn't add restrictive terms (no indication it does). |
| `svg2pdf.js` (cBioPortal's patched fork) | Upstream is **MIT** (already resolved in Phase 0) | Yes | Not a blocker. |
| `swagger-js-codegen` | **Apache-2.0** (already resolved in Phase 0) | Used in tooling | Not a blocker. |

**Recommended action:** run a proper automated license scan of the full frontend npm dependency tree (e.g. `license-checker` or equivalent) rather than relying on spot-checks of the handful PR #12125 already flagged — there may be others not yet surfaced.

## 3) `cbioportal-core` (data importer)

Checked `pom.xml` (Java) and `requirements.txt` (Python). All dependencies are standard, well-known permissively-licensed libraries: Spring (Apache-2.0), Jackson (Apache-2.0), Guava (Apache-2.0), Commons Lang/IO/Text/Collections (Apache-2.0), ClickHouse JDBC (Apache-2.0), JUnit (EPL-1.0, doesn't affect distribution), `requests`/`PyYAML`/`Jinja2`/`MarkupSafe`/`dsnparse` (all Apache-2.0/MIT/BSD family). **No copyleft flags found.** Still needs the LICENSE-file gap from Phase 0 resolved (this repo has no license of its own today), but that's independent of dependency compatibility.

## 4) `session-service`

Checked `pom.xml`. Standard Spring Boot stack (Spring Boot, Spring Security, Spring Data MongoDB — all Apache-2.0), Sentry SDK (MIT/BSD family), Hibernate Validator, springdoc-openapi. **No copyleft flags found.** Same pre-existing LICENSE-file gap as `cbioportal-core`, independent of this audit.

## 5) AI authorship inventory

Broader than previously tracked (CLAUDE.md's Key Risks previously only named PR #12014 as an example):

| Repo | `Co-Authored-By: Claude` commits | Copilot-authored PRs (`app/copilot-swe-agent`) |
|---|---|---|
| cbioportal | 31 | 31 |
| cbioportal-frontend | 52 | 42 |
| cbioportal-core | 1 | 1 |
| session-service | 0 | 0 |

The preliminary dependency-audit PR referenced above (#12125) is itself entirely Copilot-authored (all 4 commits by `app/copilot-swe-agent`) — a concrete example of AI-agent-authored content directly feeding into RFC86 itself.

**Decided 2026-07-10:** the AI-authorship policy now explicitly covers all AI coding tools (Claude, GitHub Copilot, and any other AI agent found later), not just Claude. See CLAUDE.md Decisions.

## Open follow-ups

- [ ] Legal confirmation that `mysql-connector-j`'s Universal FOSS Exception conditions are met (likely yes, low risk)
- [ ] **Implement** the `react-column-resizer` reimplementation in `cbioportal-frontend` — tracked in [cBioPortal/cbioportal#12266](https://github.com/cBioPortal/cbioportal/issues/12266) (owner TBD)
- [ ] **Implement** the `react-json-to-table` reimplementation in `cbioportal-frontend` — tracked in [cBioPortal/cbioportal#12267](https://github.com/cBioPortal/cbioportal/issues/12267) (owner TBD)
- [ ] Regenerate the backend's `OPEN-SOURCE-DOCUMENTATION` from current dependency state — tracked in [cBioPortal/cbioportal#12268](https://github.com/cBioPortal/cbioportal/issues/12268)
- [ ] Run a full automated npm license scan of `cbioportal-frontend` (only PR #12125's spot-checked subset has been verified so far)
- [ ] Confirm the other dual/multi-licensed transitive backend dependencies flagged by PR #12125 (Jakarta/Jersey/RabbitMQ-adjacent artifacts)
- [ ] Run a **full transitive Maven dependency resolution** for the backend from a network environment that can reach `build.shibboleth.net` (neither PR #12125 nor this pass has actually completed one — both relied on direct declarations/effective POM/Maven Central metadata for the items checked)
- [ ] Remove the dead Flash-based `netviz.jsp`/`cytoscape_web` feature — tracked in [cBioPortal/cbioportal#12269](https://github.com/cBioPortal/cbioportal/issues/12269)
- [x] Decide whether to formally extend the AI-authorship decision to cover Copilot-authored commits/PRs — **decided 2026-07-10: yes, extended to all AI tools**
