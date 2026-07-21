# CASE-003 — OTRF Blind Threat Hunt

## Portfolio summary

Security monitoring detected suspicious script execution and unusual outbound network activity in a Windows domain environment. This case provides raw Windows host telemetry, network packet captures, and Zeek network logs collected during the timeframe of interest. The investigation is structured as a blind threat hunt to analyze the environment, identify affected assets, and reconstruct the sequence of events without prior knowledge of ground truth or attack details.

## Case status

- Status: Active (Blind Investigation)
- Start date: 2026-07-21
- Report date: Pending
- Investigator: Analyst
- Case type: Blind Threat Hunt / DFIR Investigation
- Reporting time zone: UTC

## Evidence source

The evidence used in this investigation was obtained from the [OTRF Security-Datasets](https://github.com/OTRF/Security-Datasets) repository. The source repository was pinned to a specific Git commit (`d9d40ef123d2c87d5d3df28c96bcab4f0faccc87`) to support reproducibility. Original evidence and extracted working data are preserved locally and excluded from this public repository. Only hashes, case documentation, queries, sanitised outputs, scripts, and reports may be published.

- **Repository**: [OTRF/Security-Datasets](https://github.com/OTRF/Security-Datasets)
- **Source Commit SHA**: `d9d40ef123d2c87d5d3df28c96bcab4f0faccc87`
- **Acquisition Date**: 2026-07-21
- **Local Storage**: Preserved locally in `01_evidence/original/` and `01_evidence/working/` (excluded from Git).

## Blind and neutral case preparation

The evidence for this case was prepared through a neutral automated setup process. The investigator did not select or inspect the underlying labelled dataset during preparation and was not shown the associated threat actor, ATT&CK techniques, emulation plan, ground truth, walkthroughs, suspicious entities, or intended answers. The investigator began only with the neutral scenario described in `00_case_admin/case_description.md`.

- The setup agent was permitted only to locate, copy, hash, verify, extract, and identify evidence formats.
- It was instructed not to search for malicious activity.
- It did not create findings, hypotheses, timelines, detections, or investigative conclusions.
- All later analysis must be based only on the evidence available in the case.

## Reproducibility and spoiler policy

- The precise labelled dataset identity will remain undisclosed in public documentation until the blind investigation is complete.
- After completion, the investigator may add a ground-truth validation section.
- Any later disclosure must clearly separate:
  - blind investigative findings,
  - post-investigation ground-truth comparison,
  - corrections or missed activity identified afterward.

## Published materials

- [Case description](00_case_admin/case_description.md)
- [Case metadata](00_case_admin/case_metadata.md)
- [Evidence register](01_evidence/evidence_register.csv)