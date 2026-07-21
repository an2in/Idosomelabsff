# Case metadata

| Field | Value |
|---|---|
| Case ID | CASE-003-OTRF_Blind_Threat_Hunt |
| Case title | Windows Domain Suspicious Activity Investigation |
| Investigator | an2in |
| Requester / source | OTRF/Security-Datasets |
| Source Repository URL | https://github.com/OTRF/Security-Datasets |
| Source Commit SHA | d9d40ef123d2c87d5d3df28c96bcab4f0faccc87 |
| Date received | 2026-07-21 |
| Examination start | 2026-07-21 |
| Examination end | TBD |
| Reporting time zone | UTC + 7 |
| Authority | Public training dataset / authorised lab |
| Status | Investigating (Active Blind Investigation) |
| Preparation method | Neutral automated setup |
| Ground truth consulted | No |
| Original evidence location | DFIR/cases/CASE-003-OTRF_Blind_Threat_Hunt/01_evidence/original |
| Working-copy location | DFIR/cases/CASE-003-OTRF_Blind_Threat_Hunt/01_evidence/working |
| Report version | 0.1 |

## Purpose

Determine whether malicious activity occurred, identify the affected systems and accounts, and reconstruct the sequence of relevant events.

## Scope

### Included

- Analysis of Windows host telemetry collected from the environment.
- Analysis of network packet captures and Zeek network logs.
- Identification of suspicious script executions, processes, commands, potential lateral movement, persistence, and data exfiltration.
- **Timeline reconstruction** of security events and activity across domain hosts and accounts.

### Excluded

- Direct forensic analysis of external threat actor infrastructure beyond captured network traffic and logs.
- Consultation or use of published walkthroughs, dataset ground truth, labels, or threat actor writeups during the investigation.
- Analysis of hosts or network traffic outside the scope of the provided telemetry dataset.

## Initial information

Security monitoring detected suspicious script execution and unusual outbound network activity in a Windows domain environment. Available evidence includes Windows host telemetry, network packet captures, and Zeek network logs collected during the timeframe of interest.

## Assumptions

- The provided telemetry, packet captures, and Zeek logs represent complete and unmanipulated records of the captured domain activity.
- Host system and network log timestamps can be correlated accurately.
- No specific malicious tools, techniques, or threat actors are assumed prior to evidence-driven investigation.

## Constraints

- No threat actor has been identified.
- No malicious tool or technique should be assumed.
- The initial affected host is unknown.
- The full incident scope is unknown.
- Published walkthroughs, labels, and ground truth must not be consulted during the investigation.
