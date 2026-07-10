# RFC86 Phase 0 — Component & Release Manifest

**Status:** All research follow-ups resolved (2026-07-10). Two decisions remain that aren't licensing questions but affect what "the release" means (see bottom) — everything else is ready to feed Phase 1 (relicensing#2) and Phase 2 (relicensing#3). Tracked in [relicensing#1](https://github.com/cBioPortal/relicensing/issues/1).

## Effective license of the combined/served distribution

**Today:** Not cleanly AGPL. The docker-compose distribution (the actual thing users run) bundles:
- `cbioportal` backend — AGPL-3.0-or-later
- `cbioportal-frontend` — AGPL-3.0-or-later (built into the backend image)
- `session-service` — **no license at all** (not AGPL, not anything — this is an existing gap independent of RFC86)
- `clickhouse-server` — Apache-2.0 (third-party, no conflict)
- `mongo` — SSPL (third-party, network/service dependency only, not statically bundled — doesn't infect cBioPortal's own code, but is part of what's "served")

**Target:** Apache-2.0 for all cBioPortal-owned components (backend, frontend, session-service, cbioportal-core), once each has been through consent (Phase 2) and technical execution (Phase 4). `session-service` and `cbioportal-core` need a real LICENSE file added as a prerequisite — see below. Third-party runtime dependencies (ClickHouse, MongoDB) keep their own licenses; MongoDB's SSPL terms apply to MongoDB itself, not to cBioPortal's code, since it's accessed over the network rather than linked.

**Important caveat:** the docker-compose distribution and the Helm chart distribution are currently **not the same combined distribution** — see the Helm findings below. This manifest's "effective license" statement above describes the docker-compose path specifically; the Helm path needs its own equivalent statement once it's brought current (or an explicit decision to deprecate it).

## Manifest

| Component | Repo | Version pinned | Current license | Consent status | Dependency-scan status | Target treatment | Notes |
|---|---|---|---|---|---|---|---|
| Backend | cBioPortal/cbioportal | `7.0.1` (released, per docker-compose `.env`); `v7.0.6-SNAPSHOT` (dev head) | AGPL-3.0-or-later | Not started (Phase 2) | Partial — repo's own generated `OPEN-SOURCE-DOCUMENTATION` covers ~230 third-party deps; **3 GPL + 2 LGPL vendored components flagged** (below), no AGPL found | Relicensed | Includes docs site source (`docs/`, served at docs.cbioportal.org), DB scripts (`src/main/resources/db-scripts/cgds.sql`), and legacy webapp assets (`src/main/resources/webapp/`, incl. a Flash-era `swf/` folder) — all in the same repo/license boundary |
| Frontend | cBioPortal/cbioportal-frontend | `v7.0.5` (pinned via backend `pom.xml` `<frontend.version>`) | AGPL-3.0-or-later | Not started | Not yet audited — separate npm dependency tree, needs its own Phase 1 pass | Relicensed | React app, built into the backend Docker image at build time |
| Session service | cBioPortal/session-service | `0.6.4` (pinned in docker-compose `.env`) | **None** — no LICENSE file, not GitHub-detected, no README mention | Not started | Not yet audited | Relicensed — **but needs a LICENSE file added first**, since it has none today | 17 contributors, small/tractable list, largely overlapping with the main contributor pool already in Phase 2 outreach |
| cBioPortal Core (importer) | cBioPortal/cbioportal-core | **Not pinned at all** — the backend's own Dockerfile builds it via `ARG CORE_BRANCH=main`, always cloning `cbioportal-core`'s `main` branch HEAD at image build time (with a cache-buster keyed on the latest commit SHA) | **None** — no LICENSE file | Not started | Not yet audited — mixed Java (`pom.xml`) + Python (`requirements.txt`) dependency tree | Relicensed — **same LICENSE gap as session-service** | 18 contributors, similarly tractable; confirmed built directly into the deployed image, not a side tool. Also worth noting: the backend's own Dockerfile separately pins a ClickHouse **client** binary (`ARG CLICKHOUSE_VERSION=25.8.24.21`, Apache-2.0) baked into the image for the import scripts to talk to the (separate) ClickHouse server — a second, distinct ClickHouse version reference beyond the `clickhouse-server:24.10` in docker-compose. No license conflict, just worth recording for SBOM completeness. |
| Docker Compose deployment | cBioPortal/cbioportal-docker-compose | n/a (deployment config) | **None** — no LICENSE file at the repo level | Not started | n/a | Relicensed (config/scripts) — **also needs a LICENSE file added**, same gap as session-service/cbioportal-core | This is the artifact that defines the "combined/served distribution" — see above |
| Helm charts | cBioPortal/cbioportal-helm | `cbioportal/cbioportal:6.4.1-web-shenandoah` (per `charts/cbioportal/values.yaml`) | **None** — no LICENSE file at the repo level | Not started | n/a | Relicensed — needs a LICENSE file; also needs a decision on whether to update or deprecate (see note) | **Stale relative to docker-compose**: pinned to `6.4.1`, not `7.0.1`, and its values.yaml still configures MySQL JDBC settings (`com.mysql.jdbc.Driver`, `MySQL5InnoDBDialect`) — i.e. it targets the **old MySQL-based architecture**, not the current ClickHouse-based one. This chart does not currently deploy an equivalent product to docker-compose; it's a separate, older combined distribution that would need its own update (or explicit deprecation) independent of the license question. |
| Legacy Docker context | cBioPortal/cbioportal-docker | n/a, untouched since 2018 | None | n/a | n/a | **Historical only** — superseded by the `docker/` folder in the main backend repo | Candidate for archiving, not part of the active release |
| Sample/curated data | cBioPortal/datahub | n/a | Not yet checked | n/a | n/a | **Out of RFC86's software scope** — tracked as a separate future data-licensing decision (e.g. CC-BY/CC0), not part of this manifest's denominator | Actively maintained; this is a data question, not a software-copyright question |
| API spec (legacy) | cBioPortal/cbioportal-web-api-spec | n/a, untouched since 2016 | AGPL-3.0 | n/a | n/a | **Historical only** — superseded by the live-generated Swagger/OpenAPI spec served by the backend itself | |
| User manual/docs (3 repos) | cBioPortal/manual, cBioPortal/cbioportal-manual, cBioPortal/documentation | n/a, untouched 2020–2022 | None detected | n/a | n/a | **Historical only** — superseded by docs.cbioportal.org, which is built from the `docs/` folder inside the main backend repo (already covered above) | |
| E2E tests | cBioPortal/cbioportal-test | n/a | **MIT** | n/a | n/a | **No action needed** — already Apache-compatible | Already permissively licensed, not part of the relicense work |

## Vendored copyleft components flagged for Phase 1 (relicensing#2)

Found in the backend's own `OPEN-SOURCE-DOCUMENTATION` file, all appear to be legacy bundled JS/web assets (not the current React frontend):

| Component | License | Likely location |
|---|---|---|
| `jquery.popeye-2.1.min` | GPL | Legacy webapp assets |
| `jslab-stdlib` | GPL | Legacy webapp assets |
| `packery.pkgd.min` | GPL | Legacy webapp assets |
| `cytoscape_web` | LGPL | Legacy webapp assets (network visualization) |
| `corejmoljsv.z` | LGPL | Legacy webapp assets (Jmol viewer) |

These look like strong candidates for the Phase 1 "codebase cleanup" removal task (relicensing#2) — if they're genuinely unused dead code from the pre-React era, removing them resolves the copyleft flag *and* shrinks the Phase 2 consent surface at the same time.

## Full survey of the other ~90 org repos (2026-07-10)

Went through every repo in the `cBioPortal` GitHub org individually (license, activity, and whether it's actually referenced by the in-scope components above) rather than assuming the rest is irrelevant. Findings:

### Already covered — no separate scope needed
`cbioportal-frontend` is a pnpm/lerna monorepo (`packages/` folder). Confirmed via its `package.json` (all pulled in as `workspace:*`, not external npm packages) that these live *inside* the frontend repo already accounted for above, not as separate licensing surfaces: `oncoprintjs`, `react-mutation-mapper`, `cbioportal-clinical-timeline`, `cbioportal-frontend-commons`, `cbioportal-ts-api-client`, `oncokb-frontend-commons`, `oncokb-ts-api-client`, `cbioportal-utils`, `genome-nexus-ts-api-client`, `react-variant-view`.

### Historical only — superseded standalone repos, no action needed
These are old *pre-monorepo* standalone versions of the packages above, confirmed dead (last real commits 2016–2023, not referenced anywhere in current frontend/backend code):
- `oncoprintjs` (standalone, archived, LGPL) — superseded by `cbioportal-frontend/packages/oncoprintjs`
- `react-mutation-mapper` (standalone, archived, AGPL) — superseded by the in-repo package of the same name
- `clinical-timeline` (standalone, LGPL) — last real commit 2020-04-16 (its "updated" timestamp is newer metadata noise, not new commits); superseded by `cbioportal-frontend/packages/cbioportal-clinical-timeline`
- `mutation-mapper` (standalone, LGPL, 2023) — predecessor of `react-mutation-mapper`
- `MobxPromise` (MIT) and `oql` — not present anywhere in `cbioportal-frontend`'s dependencies; reimplemented internally
- `reactable` (MIT) — the frontend's actual `reactable: ^0.14.1` dependency resolves to the original third-party npm package, not this org's same-named repo, which looks like an unused fork/experiment
- `cbio-engine` (AGPL, 2015, "next generation core framework") — no references found anywhere in current backend code; abandoned prototype
- `common` (AGPL, 2017, described as "used by web application and importer projects") — checked the backend's own `docs/Inter-Repository-Dependencies.md` (authoritative, confirms `cbioportal-core`'s actual dependency graph) and Maven search; not referenced by group ID anywhere current — superseded when `cbioportal-core` absorbed this functionality directly
- `importer`, `cbioportal-neo4j`, `gdc-et-pipeline`, `cbioportal-frontend-archive-1`, `iViz` (archived) — old/superseded, no current references found

### Forks or wrappers of third-party projects — not cBioPortal's copyright to relicense
Already permissively licensed or not cBioPortal-owned code in the first place, so no RFC86 action needed: `igv.js` (MIT), `svg2pdf.js` (MIT, cBioPortal maintains a patched fork referenced directly in `cbioportal-frontend/package.json` via `github:cbioportal/svg2pdf.js#v1.3.3-cbio-patch-1`), `swagger-js-codegen` (Apache-2.0), `spring-social-google` / `spring-social-live` (Apache-2.0), `maven-external-version` (Apache-2.0), `wdio-novus-visual-regression-service` (MIT), `LibreChat` (MIT, appears to be an unrelated clone, not part of any cBioPortal product).

### Deferred to a follow-on wave — AGPL, cBioPortal-owned, actively maintained, but NOT bundled into the release
These are real, currently-AGPL, actively-developed cBioPortal repos — but they're auxiliary services/tools called over the network or used offline, not part of the docker-compose/Helm deployment graph, so they fall outside Phase 0's "the release" as currently scoped:
- `cancerhotspots` (AGPL, updated 2026-06-02) — powers cancerhotspots.org; confirmed called by `cbioportal-frontend` as an external API (`packages/react-mutation-mapper`, `src/shared/components/driverAnnotations/...`), not bundled into the app itself
- `datahub-study-curation-tools` (AGPL, updated 2026-06-01) and `clinical-data-normalization` (AGPL, updated 2025-09-23) — data-curation tooling used by curators, not shipped in the served product
- `fmi-converter` (AGPL, 2023) — a data-format converter tool, same category
- `clinical-data-dictionary` (**no license at all**, Java web service) — only referenced from a doc mention (`docs/File-Formats.md`) in the backend repo, not from docker-compose/Helm/pom.xml — appears to be an optional/adjacent service, not deployed as part of the release

**Decided (2026-07-10): kept separate from RFC86.** These five stay outside this relicensing effort's scope/denominator — not included in the Phase 1 SBOM or the Phase 2 consent count. They remain AGPL (or unlicensed, for `clinical-data-dictionary`) for now and are candidates for their own future relicensing effort if/when there's a reason to revisit them.

### Everything else — out of scope by default
The remaining repos (AI/MCP assistant tools, benchmarks, personal notebooks/workshops, project-management repos like `roadmap`/`icebox`/`GSoC`, one-off scripts) show no reference from any in-scope component and are treated as out of scope by default.

## Open follow-ups

- [x] Confirm exact pinned version/tag for `cbioportal-core` in the backend Dockerfile — **resolved: it's not pinned at all, always builds from `main` HEAD** (see manifest row above). Worth its own decision: pin it for reproducibility, independent of RFC86.
- [x] Check `cbioportal-docker-compose` and `cbioportal-helm` repo-level licenses directly — **resolved: both unlicensed**, same gap as session-service/cbioportal-core. This is a recurring pattern across the newer deployment/service repos, not a one-off.
- [x] Verify `cbioportal-helm`'s chart references the same component set as docker-compose — **resolved: it does not.** The Helm chart is pinned to the old `6.4.1` MySQL-based architecture, not the current `7.0.1` ClickHouse-based one docker-compose uses. This is a real product/architecture gap independent of licensing — needs its own decision (update the chart, or deprecate it) before or alongside the relicense.
- [ ] Consider fast-tracking a LICENSE file for `session-service`, `cbioportal-core`, `cbioportal-docker-compose`, and `cbioportal-helm` — none of these were ever AGPL to begin with, so adding Apache-2.0 directly (with sign-off from their small, mostly-already-being-contacted contributor lists) may not need to wait on the full Phase 1–4 sequence for the rest of the codebase
- [x] Decide scope for the 5 "adjacent AGPL tooling" repos — **decided 2026-07-10: kept separate, deferred to a follow-on wave** (see above)

## Remaining Phase 0 decisions needed (not license questions, but block a clean manifest)

- [ ] Should `cbioportal-core` be pinned to a fixed version/tag for reproducibility? (Independent of RFC86, but affects what "the release" even means.)
- [ ] Should `cbioportal-helm` be brought up to date (ClickHouse, 7.0.1) or deprecated? Until decided, the manifest's "effective license of the combined/served distribution" statement only confidently covers the docker-compose path.
