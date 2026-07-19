# Command and query log

## C-001 — Wireshark GUI: Follow TCP Stream to willselfdestruct.com

**Purpose:** Identify and inspect the TCP stream connecting to willselfdestruct.com to confirm the harassing message transmission.

**Tool:** Wireshark (GUI)

**Wireshark stream index:** `tcp.stream eq 1707`

**Steps:**
1. Opened working copy of `nitroba.pcap` in Wireshark.
2. Applied display filter: `tcp.stream eq 1707`
3. Right-clicked a packet in the stream → *Follow → TCP Stream*.
4. Inspected HTTP payload — POST request to `willselfdestruct.com` containing the harassing message body.

**Input**

- Evidence ID: E-001
- Working-copy path: `DFIR/cases/CASE-001-TheNitroba/01_evidence/working/nitroba.pcap`

**Output**

- Saved to: *(no file saved — GUI inspection only)*
- Relevant excerpt: HTTP POST payload matched the harassing message received by victim Lily Tuckrige.

**tshark equivalent:**
```bash
tshark -r DFIR/cases/CASE-001-TheNitroba/01_evidence/working/nitroba.pcap \
  -Y "tcp.stream eq 1707" -w DFIR/cases/CASE-001-TheNitroba/05_exhibits/stream_1707_willselfdestruct.pcap
```

**Interpretation:** TCP stream 1707 is the willselfdestruct.com POST session. The payload confirms the harassing message originated from this device. Supports F-001.

---

## C-002 — Wireshark GUI: Follow TCP Stream for Gmail authentication session

**Purpose:** Identify the authenticated Gmail account active on the culprit device during the harassment event.

**Tool:** Wireshark (GUI)

**Wireshark stream index:** `tcp.stream eq 1611`

**Steps:**
1. Applied display filter: `tcp.stream eq 1611`
2. Right-clicked a packet in the stream → *Follow → TCP Stream*.
3. Located Gmail HTTP response containing the string `Loading jcoachj@gmail.com…`, confirming the authenticated account.

**Input**

- Evidence ID: E-001
- Working-copy path: `DFIR/cases/CASE-001-TheNitroba/01_evidence/working/nitroba.pcap`

**Output**

- Saved to: *(no file saved — GUI inspection only)*
- Relevant excerpt: Gmail server response body includes `"Loading jcoachj@gmail.com…"` indicating an authenticated Gmail session for that account.

**tshark equivalent:**
```bash
tshark -r DFIR/cases/CASE-001-TheNitroba/01_evidence/working/nitroba.pcap \
  -Y "tcp.stream eq 1611" -w DFIR/cases/CASE-001-TheNitroba/05_exhibits/stream_1611_gmail_auth.pcap
```

**Interpretation:** TCP stream 1611 is the Gmail authentication session. The server response `"Loading jcoachj@gmail.com…"` identifies the account. Cross-reference with Chemistry 109 roster identifies account holder as student Johnny Coach. Supports F-002 and F-003.
