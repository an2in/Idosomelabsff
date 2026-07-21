### 2026-07-20 10:00 — Extract evidence

- **Time zone:** Unknown
- **Objective:** Locate and extract email communication.
- **Evidence examined:** Disk images (nps-2008-jean.E01, nps-2008-jean.E02)
- **Tool / command:** FTK Imager
- **Result:** Found and extracted outlook.pst
- **Interpretation:** PST file contains user's emails.
- **Confidence:** High
- **Next action:** Analyze outlook.pst
- **Output reference:** DFIR/cases/CASE-002-M57Jean/01_evidence/working/outlook.pst

---

### 2026-07-21 14:00 — Analyze PST File

- **Time zone:** Unknown
- **Objective:** Analyze emails to determine if data exfiltration occurred.
- **Evidence examined:** outlook.pst
- **Tool / command:** GoldFynch PST Viewer (https://goldfynch.com/pst-viewer/)
- **Result:** Traced email chain (#207, #210, #214, #215) showing data exfiltration via impersonation.
- **Interpretation:** Attacker tuckgorge@gmail.com successfully impersonated Alison to trick Jean.
- **Confidence:** High
- **Next action:** Document findings.
- **Output reference:** Emails #207, #210, #214, #215
