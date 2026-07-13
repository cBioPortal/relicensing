# Copilot instructions for `cBioPortal/relicensing`

## Build, test, and lint commands

This repository is documentation/process-only for RFC86 relicensing coordination. There are currently no build, test, or lint toolchains configured in this repo.

- **Build:** N/A
- **Lint:** N/A
- **Test (full suite):** N/A
- **Test (single test):** N/A

## High-level architecture

The repo is a single-source planning and execution record for the AGPL → Apache-2.0 relicensing program, with three main layers:

1. **Program control plane (`README.md`)**  
   Canonical high-level state: goals, phase model, deadlines, decisions, risk register, and issue mapping (`relicensing#1`–`#8`).
2. **Phase artifacts (`docs/relicensing/*.md`)**  
   Detailed operational documents per phase:
   - `component-manifest.md`: scope denominator and combined-distribution licensing model
   - `dependency-audit.md`: dependency blockers and remediation decisions
   - `contributor-consent-status.md`: public consent board and status tracking model
   - `outreach-tier1-letter.md` / `outreach-tier2-template.md`: standardized outreach templates
3. **Working data (`contributor_matrix.tsv`)**  
   Private operational/contact dataset used to drive outreach and board updates; not intended for publication.

## Key repository conventions

- **Keep README + phase docs synchronized:** project status, decisions, and schedule assumptions should be reflected both in `README.md` and the relevant `docs/relicensing/*` file when changed.
- **Issue-driven execution:** each material change should map to the phase issue hierarchy in `cBioPortal/relicensing` (epic `#8`, phases `#1`–`#7`).
- **Public/private data boundary is strict:** `contributor-consent-status.md` is public and must not include raw emails or private contact fields; sensitive originals stay outside the repo per README policy.
- **Scope discipline:** this repo tracks RFC86 relicensing coordination; implementation fixes belong in target component repos (e.g., `cbioportal`, `cbioportal-frontend`, `cbioportal-core`, `session-service`) and should be referenced here, not implemented here.
- **Respect existing outreach language:** Tier 1/Tier 2 templates are treated as standard text; modify only when policy/decision changes require it.
