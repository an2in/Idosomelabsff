# Exhibits


| Exhibit ID | Evidence source | Description | Creation method | Relevance | Redaction / transformation |
|---|---|---|---|---|---|
| EX-001 | E-001 `nitroba.pcap` | Reconstructed TCP stream **`tcp.stream eq 1707`** — HTTP POST from the dorm room source IP (`192.168.15.4`) to `willselfdestruct.com`, including the payload containing the harassing message content. | Wireshark GUI → `tcp.stream eq 1707` → Follow TCP Stream (C-001) | Directly links the dorm network to the delivery of the harassing message; payload matches victim's report. | None — no credentials or irrelevant personal data present in stream. |
| EX-002 | E-001 `nitroba.pcap` | Reconstructed TCP stream **`tcp.stream eq 1611`** — Gmail authentication session from the culprit device, showing the Google server response `"Loading jcoachj@gmail.com…"` confirming the authenticated account. | Wireshark GUI → `tcp.stream eq 1611` → Follow TCP Stream (C-002) | Identifies the authenticated Gmail account (`jcoachj@gmail.com`) active on the device during the harassment event. | None — the fragment contains only the account-identifying response string; no passwords or session tokens are present. |
| EX-003 | Chemistry 109 course roster (external; not in evidence register) | Roster entry for **Johnny Coach** confirming enrollment in Lily Tuckrige's Chemistry 109 summer class and matching the Gmail account username `jcoachj`. | Manual cross-reference by investigator. | Completes the attribution chain: Gmail account → named student in victim's class. | Roster not reproduced here; reference only. No other student names recorded in this exhibit. |
| EX-004 | E-001 `nitroba.pcap` (derivative) | Filtered packet capture containing only the TCP streams relevant to the investigation: the willselfdestruct.com connection and the Gmail session originating from `192.168.15.4`. Stored as `05_exhibits/nitroba_filtered.pcap`. | `tshark` filter (see command below) — **to be executed** | Provides a focused, portable exhibit for reviewers without requiring access to the full 56 MB capture. | Derived from E-001; original is unchanged. Must be hashed after creation and registered in `01_evidence/evidence_register.csv` as E-002. |

---

## EX-004 — Filtered pcap creation command

Run this command against the working copy to produce the filtered pcap exhibit. Hash the output and update the evidence register.

```bash
tshark -r DFIR/cases/CASE-001-TheNitroba/01_evidence/working/nitroba.pcap \
  -Y "tcp.stream eq 1707 || tcp.stream eq 1611" \
  -w DFIR/cases/CASE-001-TheNitroba/05_exhibits/nitroba_filtered.pcap
```

After running:
```bash
sha256sum DFIR/cases/CASE-001-TheNitroba/05_exhibits/nitroba_filtered.pcap
```

Then add E-002 to `01_evidence/evidence_register.csv` with:
- `evidence_id`: E-002
- `description`: Filtered derivative pcap — willselfdestruct.com and Gmail TCP streams from 192.168.15.4
- `source`: Derived from E-001 using tshark
- `original_filename`: nitroba_filtered.pcap
- `size_bytes`: *(fill in after creation)*
- `sha256`: *(fill in after creation)*
- `storage_location`: DFIR/cases/CASE-001-TheNitroba/05_exhibits/nitroba_filtered.pcap

---

> **Note on existing exhibits (EX-001–003):** These are observational records of GUI-based analysis. No files were saved during the Wireshark session. If formal proceedings are initiated, it is recommended to export and hash the TCP stream reconstructions directly from `nitroba.pcap` using `tshark` to complement these descriptive records.
