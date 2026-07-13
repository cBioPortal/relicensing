# Tier 1 Outreach — Institutional Team Lead Letter

**To:** [Institutional Lead / PI of the cBioPortal team at Institution]
**From:** cBioPortal Core Team (Memorial Sloan Kettering Cancer Center)
**Re:** cBioPortal Open Source Relicensing — Request for Consent (RFC 86)
**Date:** [DATE]

---

Dear [Name],

We are writing on behalf of the cBioPortal core team at Memorial Sloan Kettering Cancer Center (MSKCC) to request your consent, as the institutional lead of the cBioPortal team at **[INSTITUTION]**, to relicense the cBioPortal open source platform from its current **GNU Affero General Public License v3 (AGPL-3.0)** to the **Apache License 2.0**.

## Background

cBioPortal for Cancer Genomics is an open source platform for visualizing, exploring, and analyzing cancer genomics data. It is jointly developed and maintained by MSKCC and contributors from [INSTITUTION], along with several other academic and industry partners worldwide.

The project is proposing this license change (RFC 86) for the following reasons:

1. **Funder requirements**: NCI ITCR and Chan Zuckerberg Initiative (CZI) explicitly require permissive licenses (Apache 2.0, MIT, or BSD) for grant-funded software. This requirement was flagged at award renewal and must be resolved.
2. **Adoption barriers**: The AGPL's "copyleft network use" provisions have deterred adoption by pharmaceutical, biotechnology, and technology organizations, even in cases where the concern is not technically warranted.
3. **Patent clarity**: Apache 2.0 includes an explicit patent grant and patent retaliation clause required by many corporate and institutional legal teams. This is the same license choice made by Kubernetes and similar large open source platforms.

## Why We're Asking You Directly

Given the project's timeline, we are asking institutional team leads to sign on behalf of their team's contributions, rather than routing this through a formal legal or tech-transfer review. We believe this is appropriate because:
- This is a non-commercial, mission-aligned open source scientific tool, not a matter of contested or commercially-licensed IP.
- As the team lead, you are the person best positioned to know which of your team's contributions are included and whether any of your team members' work should be handled differently.

**If you believe this request should go through your institution's legal or tech-transfer office instead — because your role doesn't carry authority to make this kind of IP decision, or your institution's policy requires it — please let us know and loop in the right contact.** We would rather route this correctly than have a consent that doesn't hold up.

## What We Are Requesting

We are requesting that you, as institutional lead of the cBioPortal team at **[INSTITUTION]**, confirm consent for the relicensing of contributions made by your team to the following repositories:

| Repository | URL |
|---|---|
| cbioportal (backend) | https://github.com/cBioPortal/cbioportal |
| cbioportal-frontend | https://github.com/cBioPortal/cbioportal-frontend |
| cbioportal-docker-compose | https://github.com/cBioPortal/cbioportal-docker-compose |
| cbioportal-core (data importer) | https://github.com/cBioPortal/cbioportal-core |
| session-service | https://github.com/cBioPortal/session-service |

The contributors from [INSTITUTION] whose work is included in the codebase are:

| GitHub Handle | Name | Approx. Commits |
|---|---|---|
| [HANDLE] | [NAME] | [N] |

This consent covers:
- All source code, documentation, test files, and related assets contributed to the above repositories by your team under [INSTITUTION] employment or sponsorship
- The relicensing of that work from AGPL-3.0 to Apache-2.0
- **The person signing below attests that they hold the role of institutional/team lead for cBioPortal work at [INSTITUTION], understands they are representing their institution's consent in that capacity (not as a substitute for formal legal sign-off), and confirms they have a good-faith basis to believe this consent is valid** for the listed contributors' work

We are also separately reaching out to individual contributors where appropriate; your consent here is not intended to replace an individual contributor's own consent for contributions that were not made under institutional employment or sponsorship.

## What We Are NOT Requesting

- We are not asking you to sign a new Contributor License Agreement (CLA) for future contributions.
- We are not modifying any attribution, credit, or authorship records.
- We are not changing the open source nature of the project.

## Timeline

We are targeting completion of institutional consents by **July 24, 2026**. Following that, we will conduct a 30-day public notice and comment period (Aug 21 – Sep 20) before any technical changes are made.

## Questions

Please direct any questions or requests for additional information to:

**Jianjiong Gao** — gaoj@mskcc.org  

A copy of RFC 86 (the full relicensing proposal) is attached for reference. The full relicensing process, including a public status board tracking every contributor's consent status, is tracked at https://github.com/cBioPortal/relicensing.

---

## Consent Statement

By signing below, I confirm that I am the institutional/team lead for cBioPortal work at **[INSTITUTION]**, and in that capacity I consent to the relicensing of my team's contributions in the cBioPortal repositories listed above from AGPL-3.0 to Apache-2.0, as described in RFC 86. I understand this is being sought at the team-lead level rather than through a formal legal/tech-transfer review, and I have a good-faith basis to believe I can grant this consent for the listed contributions.

**Signed:** ________________________________

**Name:** ________________________________

**Role/Title:** ________________________________

**Institution:** ________________________________

**Date:** ________________________________
