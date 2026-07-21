# Technical report

## 1. Report information
- **Case Name:** CASE-002-M57Jean
- **Date:** 2026-07-21
- **Investigator:** Antigravity

## 2. Purpose and investigation questions
The purpose of this investigation is to determine if sensitive data was exfiltrated from Jean's account and the mechanism used. 
Questions: Was sensitive data exfiltrated? How was it exfiltrated? Who was involved?

## 3. Scope and authority
The scope is limited to the provided disk images (`nps-2008-jean.E01`, `nps-2008-jean.E02`) and the extracted `outlook.pst` file in the working directory. Identifying the source of the attacker's prior knowledge about internal conversations is out of scope.

## 4. Evidence received
- `nps-2008-jean.E01` (Disk image #1)
- `nps-2008-jean.E02` (Disk image #2)
- Extracted file: `outlook.pst` from Jean's system (Original path: `[root]\Documents and Settings\Jean\Local Settings\Application Data\Microsoft\Outlook\outlook.pst`).

## 5. Evidence handling and integrity
The original images were handled according to standard digital forensics practices. Working copies of the evidence, including the extracted `outlook.pst`, were analyzed to preserve the original evidence.

## 6. Tools and environment
- FTK Imager: Used for investigating files and extracting evidence (`outlook.pst`).
- GoldFynch PST Viewer (https://goldfynch.com/pst-viewer/): Used for analyzing the `outlook.pst` file.

## 7. Methodology
1. Investigated the provided disk images using FTK Imager.
2. Located and extracted Jean's `outlook.pst` file.
3. Analyzed the contents of `outlook.pst` using GoldFynch PST Viewer to trace email communications.
4. Reconstructed the sequence of events related to the suspected data exfiltration.

## 8. Findings

### Finding F-01 — Data Exfiltration through Social Engineering

- **Conclusion:** Sensitive information was successfully exfiltrated by an external party using a social engineering attack (impersonation).
- **Supporting evidence:**
  - Email #207: Alison asked Jean for sensitive information.
  - Email #210: Jean answered email #207, but Alison appeared confused.
  - Email #214: An external address `tuckgorge@gmail.com` impersonating "Alison" urged Jean to send the sensitive info to him.
  - Email #215: Jean sent the requested sensitive information to the impersonator and said "thanks".
  - Subsequent emails: Other employees emailed Jean asking "What's going on", indicating confusion and a realization of the anomaly.
- **Interpretation:** The attacker (`tuckgorge@gmail.com`) successfully impersonated Alison to trick Jean into sending the sensitive data.
- **Confidence:** High, based on direct email evidence.
- **Alternative explanations:** None plausible given the explicit email chain.
- **Limitations:** It is currently unknown how the attacker became aware that Alison and Jean were discussing sensitive information.

## 9. Timeline reconstruction
- **Event 1:** Email #207 - Alison requests sensitive information from Jean.
- **Event 2:** Email #210 - Jean responds to Email #207; Alison expresses confusion.
- **Event 3:** Email #214 - `tuckgorge@gmail.com` ("Alison") urgers Jean to send the info to him.
- **Event 4:** Email #215 - Jean sends the sensitive info to `tuckgorge@gmail.com`.
- **Event 5:** Later - Coworkers email Jean expressing confusion ("What's going on").

## 10. Hypothesis evaluation
- **Hypothesis:** Data was exfiltrated by an internal malicious actor. (Rejected - exfiltrated to an external gmail account).
- **Hypothesis:** Data was exfiltrated via social engineering by an external actor. (Confirmed - `tuckgorge@gmail.com` impersonated an internal employee).

## 11. Indicators and observables
- **Email Address:** `tuckgorge@gmail.com` (Malicious actor)

## 12. Conclusions
Jean fell victim to a targeted social engineering attack. An external actor impersonating a coworker (Alison) successfully convinced Jean to send sensitive company information to an external email address (`tuckgorge@gmail.com`). The data exfiltration was successful.

## 13. Limitations
The investigation could not determine how `tuckgorge@gmail.com` knew about the internal discussion regarding sensitive information between Alison and Jean.

## 14. Recommendations
- Implement mandatory security awareness training for all employees, emphasizing the risks of social engineering and executive impersonation.
- Establish a verification process (e.g., secondary channel confirmation via phone or internal chat) before sharing sensitive information, even when requested by known colleagues.
- Investigate potential network or account compromises that may have allowed the attacker to monitor internal communications.

## 15. Evidence disposition
Evidence files remain secured in the designated case folder (`DFIR/cases/CASE-002-M57Jean/01_evidence`).

## Appendix A — Commands and queries
- Tool used: FTK Imager for file extraction.
- Online Tool: https://goldfynch.com/pst-viewer/

## Appendix B — Exhibits
- `outlook.pst` (Extracted from Jean's machine)
- Emails #207, #210, #214, #215.

## Appendix C — Glossary
- **PST:** Personal Storage Table, a file format used by Microsoft programs to store calendar events, contacts, and email messages.
