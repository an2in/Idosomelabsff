## Log

### 2026-07-20 00:00 — Wireshark GUI analysis of nitroba.pcap

- **Time zone:** UTC+7
- **Objective:** Identify the source device and user account responsible for sending harassing emails, and confirm network-level evidence of the willselfdestruct.com message.
- **Evidence examined:** E-001 — `nitroba.pcap` (working copy)
- **Tool / command:** Wireshark (GUI) — Follow TCP Stream; filter by source IP; inspect HTTP payloads
- **Result:**
  1. A TCP stream was identified originating from a device on the dorm room network connecting to `willselfdestruct.com`. The HTTP payload content matched the harassing message received by victim Lily Tuckrige.
  2. Following traffic from the same source IP, a Gmail session was observed in which the Gmail server responded with the string `"Loading jcoachj@gmail.com…"`, revealing the authenticated Google account in use.
  3. Cross-referencing `jcoachj@gmail.com` against the Chemistry 109 course roster identified the account holder as **Johnny Coach**, a student enrolled in Tuckrige's class.
- **Interpretation:** The device at the culprit IP initiated both the Gmail session and the willselfdestruct.com submission during the period of harassment. The authenticated Gmail session response conclusively links the network activity to the account `jcoachj@gmail.com`, attributed to student Johnny Coach.
- **Confidence:** High
- **Next action:** Document findings, IOCs, and timeline. Prepare technical report.
- **Output reference:** Wireshark GUI session; no saved capture filter output file.
