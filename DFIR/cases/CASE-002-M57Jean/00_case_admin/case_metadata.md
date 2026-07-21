# Case metadata (completed)

| Field | Value |
|---|---|
| Case ID | 002 |
| Case title | M57-Jean |
| Investigator | an2in |
| Requester / source | Digital Corpora |
| Date received | 2026-07-20 |
| Examination start | 2026-07-21 |
| Examination end | 2026-07-21 |
| Reporting time zone | UTC + 7 |
| Authority | Public training dataset / authorised lab |
| Status | Investigating |
| Original evidence location | DFIR/cases/CASE-002-M57Jean/01_evidence |
| Working-copy location | DFIR/cases/CASE-002-M57Jean/02_working |
| Report version | 0.1 |

---

## Purpose
Determine how the confidential spreadsheet was stolen and whether Jean is innocent.

---

## Scope

### Included
- Analysis of disk image files from Jean’s laptop  
- Timeline reconstruction of spreadsheet creation and modification  
- Tracing how the file was exfiltrated and appeared on competitor’s website  

### Excluded
- Broader attribution of attacker identity or motives  
- Investigation of external infrastructure beyond Jean’s laptop  

---

## Initial information
The M57-Jean scenario involves a single disk image from Jean’s laptop. A confidential spreadsheet containing employee names and salaries was leaked to a competitor’s website. The file existed only on Jean’s machine. Jean denies involvement and claims her laptop was hacked.

---

## Assumptions
- The disk image provided is a complete and accurate representation of Jean’s laptop at the time of seizure.  
- Jean had sole legitimate access to the confidential spreadsheet.  
- The competitor’s website did not have insider access to M57.Biz systems.    

---

## Constraints
- Limited to a single disk image; no network captures or logs are available.  
- No direct access to competitor’s infrastructure for verification.   