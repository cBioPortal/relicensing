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
   - `outreach-individual-template.md`: individual contributor outreach template
3. **Working data (`contributor_matrix.tsv`)**  
   Private operational/contact dataset used to drive outreach and board updates; not intended for publication.

## Key repository conventions

- **Keep README + phase docs synchronized:** project status, decisions, and schedule assumptions should be reflected both in `README.md` and the relevant `docs/relicensing/*` file when changed.
- **Issue-driven execution:** each material change should map to the phase issue hierarchy in `cBioPortal/relicensing` (epic `#8`, phases `#1`–`#7`).
- **Public/private data boundary is strict:** `contributor-consent-status.md` is public and must not include raw emails or private contact fields; sensitive originals stay outside the repo per README policy.
- **Live consent records are sensitive:** `cbioportal#12282`, `cbioportal#12271`, and `docs/relicensing/contributor-consent-status.md` are live records. Preserve recorded consents exactly; make only surgical edits when needed, and avoid broad rewrites that could alter or obscure existing consent entries.
- **Current live entries:** Nikolaus Schultz is already recorded in `cbioportal#12282` and JJ Gao is already recorded in `cbioportal#12271`. Preserve those consent entries exactly in any future edits.
- **Scope discipline:** this repo tracks RFC86 relicensing coordination; implementation fixes belong in target component repos (e.g., `cbioportal`, `cbioportal-frontend`, `cbioportal-core`, `session-service`) and should be referenced here, not implemented here.
- **Respect existing outreach language:** team-lead and individual-contributor outreach text is treated as standard copy; modify only when policy/decision changes require it.
