# Command and query log

## Command C-001

**Purpose**
Extract email evidence from disk image.

**Command**
```
Used FTK Imager UI
```

**Input**
- Evidence ID: E-001, E-002
- Working-copy path: Disk images

**Output**
- Saved to: `01_evidence/working/outlook.pst` (Original path: `[root]\Documents and Settings\Jean\Local Settings\Application Data\Microsoft\Outlook\outlook.pst`)
- Relevant excerpt: N/A

**Interpretation**
Successfully extracted PST file for email analysis.

---

## Command C-002

**Purpose**
Analyze contents of PST file.

**Command**
```
Used GoldFynch PST Viewer web interface (https://goldfynch.com/pst-viewer/)
```

**Input**
- Evidence ID: outlook.pst
- Working-copy path: `01_evidence/working/outlook.pst`

**Output**
- Saved to: N/A
- Relevant excerpt: Emails #207, #210, #214, #215

**Interpretation**
Identified a successful social engineering attack leading to data exfiltration.
