# Technical report

## 1. Report information

| Field | Value |
|---|---|
| Case ID | CASE-001 |
| Case title | 2008 Nitroba University Harassment |
| Report version | 0.1 |
| Investigator | an2in |
| Report date | 2026-07-20 |
| Reporting time zone | UTC+7 |
| Status | Draft |

## 2. Purpose and investigation questions

The purpose of this investigation is to determine whether a student enrolled in Chemistry 109 at Nitroba State University was responsible for sending harassing emails to the course teacher, Lily Tuckrige, and to provide clear, conclusive evidence to support that conclusion using network packet capture data.

The investigation was guided by the following questions:

- **Q-01**: Is a student from Chemistry 109 responsible for the harassing emails? → **Answered** (see F-003)
- **Q-02**: Does the network capture contain evidence of the willselfdestruct.com message transmission? → **Answered** (see F-001)
- **Q-03**: Could the traffic have originated from a third party using the open Wi-Fi? → **Partially addressed** (see Limitations)

## 3. Scope and authority

This investigation is an academic training exercise conducted by investigator an2in under individual professional development using the open-source Digital Corpora educational license (2008 Nitroba University scenario).

**In scope:** Analysis of E-001 (`nitroba.pcap`); HTTP payload inspection; Gmail session identification; cross-reference against the Chemistry 109 course roster.  
**Out of scope:** Physical device forensics; router configuration or logs; network traffic originating outside the tapped dorm room Ethernet port.

## 4. Evidence received

| Evidence ID | Filename | Size (bytes) | SHA-256 | Date received |
|---|---|---|---|---|
| E-001 | nitroba.pcap | 56,180,821 | `2b77a9eaefc1d6af163d1ba793c96dbccacb04e6befdf1a0b01f8c67553ec2fb` | 19/07/2026 |

Evidence was received from the Nitroba IT Department. Analysis was performed on a verified working copy located at `DFIR/cases/CASE-001-TheNitroba/01_evidence/working/nitroba.pcap`. The original file was not modified.

## 5. Evidence handling and integrity

The working copy SHA-256 hash was verified against the original before analysis. No modifications were made to either copy during the investigation. Wireshark was used in read-only mode (GUI, no packet editing).

## 6. Tools and environment

| Tool | Version | Purpose |
|---|---|---|
| Wireshark | 4.6.6 | Network packet capture analysis — TCP stream following, HTTP payload inspection, IP-based traffic filtering |

Platform: Linux (Arch Linux, kernel 7.0.10-arch1-1, 64-bit)

## 7. Methodology

1. **Evidence intake**: Opened `nitroba.pcap` working copy in Wireshark.
2. **TCP stream analysis (C-001)**: Applied a display filter to identify packets destined for `willselfdestruct.com`. Used *Follow → TCP Stream* to reconstruct the full HTTP exchange and inspect the payload.
3. **IP-based traffic filtering (C-002)**: Applied display filter `ip.src == 192.168.15.4` (the culprit's local IP on the dorm network) to enumerate all outbound connections made from that device.
4. **Gmail session inspection**: Within the filtered stream, identified a Gmail HTTP session. Examined the server response body and located the string `"Loading jcoachj@gmail.com…"` confirming the authenticated account.
5. **Roster cross-reference**: Compared the identified Gmail username (`jcoachj`) against the Chemistry 109 summer course roster. Identified the corresponding student as Johnny Coach.

## 8. Findings

### Finding F-001 — TCP connection to willselfdestruct.com confirmed

- **Conclusion:** A TCP stream in `nitroba.pcap` establishes a connection from the dorm room network to `willselfdestruct.com`. The HTTP payload of that stream contains content consistent with the harassing message received by victim Lily Tuckrige.
- **Supporting evidence:** E-001 `nitroba.pcap` — Wireshark Follow TCP Stream (C-001)
- **Interpretation:** The message was transmitted over the network from a device on the dorm room's Ethernet connection. The payload match to the victim's received message confirms this is the delivery event, not unrelated traffic.
- **Confidence:** High
- **Alternative explanations:** None credible — the payload content matches the victim's reported message.
- **Limitations:** Exact packet timestamp was not independently verified against a reference clock.

### Finding F-002 — Gmail session reveals authenticated account jcoachj@gmail.com

- **Conclusion:** A Gmail HTTP session originating from the same source IP shows the Google server responding with `"Loading jcoachj@gmail.com…"`, indicating an active authenticated session for that account on the device at the time of the harassment.
- **Supporting evidence:** E-001 `nitroba.pcap` — Wireshark HTTP stream inspection (C-002)
- **Interpretation:** The device that connected to willselfdestruct.com was simultaneously authenticated to Gmail as `jcoachj@gmail.com`. This ties the network activity to a specific user identity.
- **Confidence:** High
- **Alternative explanations:** A visitor could have used the open Wi-Fi with their own device already logged into that account — however, this remains a low-probability alternative given the corroborating enrollment match.
- **Limitations:** Without device forensics, it cannot be confirmed that the same physical device was used for both connections (though they share a source IP).

### Finding F-003 — Johnny Coach identified as holder of jcoachj@gmail.com

- **Conclusion:** Cross-referencing `jcoachj@gmail.com` against the Chemistry 109 summer course roster identifies the account holder as student **Johnny Coach**, enrolled in Lily Tuckrige's class.
- **Supporting evidence:** Chemistry 109 course roster; F-002
- **Interpretation:** The Gmail account active during the harassment event belongs to a student in the victim's class, satisfying the key investigative question.
- **Confidence:** High
- **Alternative explanations:** The Gmail username `jcoachj` could theoretically belong to a different person who shares the same initials and surname — this is a very low probability given the class enrollment match.
- **Limitations:** No independent confirmation from Google account records was obtained (out of scope).

## 9. Timeline reconstruction

| Event | Timestamp | Source |
|---|---|---|
| Victim receives harassing email via willselfdestruct.com | 2008-07-21 (Monday) | Case complaint; victim screenshot |
| TCP connection from dorm room IP to willselfdestruct.com; payload matches harassing message | 2008-07-21 | E-001 nitroba.pcap (F-001) |
| Gmail session from same source IP shows `"Loading jcoachj@gmail.com…"` | 2008-07-21 | E-001 nitroba.pcap (F-002) |
| Investigator cross-references Gmail account against Chemistry 109 roster → Johnny Coach | 2026-07-20 | F-003; Chemistry 109 roster |

## 10. Hypothesis evaluation

| Hypothesis | Status | Evidence |
|---|---|---|
| H-01: A TCP handshake connects the culprit machine to willselfdestruct.com | **Supported** | TCP stream found in nitroba.pcap; HTTP payload matches victim's message (F-001) |

## 11. Indicators and observables

| Type | Value | Confidence |
|---|---|---|
| IP Address | 192.168.15.4 (local) | High |
| Domain | willselfdestruct.com | High |
| Email Account | jcoachj@gmail.com | High |
| Email Address (victim) | lilytuckrige@yahoo.com | High |

## 12. Conclusions

The network evidence contained in `nitroba.pcap` establishes a clear chain of attribution:

1. A device on the dorm room network (IP `192.168.15.4` internally) transmitted a message to `willselfdestruct.com` whose content matches the harassing email received by the victim **(F-001)**.
2. That same device was simultaneously authenticated to Gmail as `jcoachj@gmail.com` **(F-002)**.
3. The Gmail account `jcoachj@gmail.com` belongs to Chemistry 109 student **Johnny Coach** **(F-003)**.

**The investigator concludes with high confidence that Johnny Coach sent the harassing email to Lily Tuckrige on 21 July 2008.**

## 13. Limitations

- **Open Wi-Fi network**: The dorm room's passwordless router allows the theoretical possibility of an unauthorised third party using the connection; the authenticated Gmail session substantially reduces but does not eliminate this alternative.
- **No endpoint forensics**: Disk images or login records from the specific device are not available, preventing absolute device-level attribution.
- **No Google account verification**: Gmail account ownership was inferred from the HTTP response string and roster cross-reference; formal verification from Google account records was not obtained and is out of scope.
- **Ephemeral message service**: The content of the willselfdestruct.com message was recovered only from the network capture. The service itself destroyed the message after it was viewed by the victim.

## 14. Recommendations

- Present findings to Nitroba University's student conduct authority.
- Consider endpoint forensics (disk image of the suspect device) if formal disciplinary or legal proceedings are initiated, to provide device-level corroboration.
- Enforce password protection or prohibit unauthorised Wi-Fi routers in dorm rooms to enable more reliable attribution in future cases.
- Implement per-device MAC-level logging on dorm Ethernet ports as a standard practice.

## 15. Evidence disposition

| Evidence ID | Original location | Working copy | Integrity status |
|---|---|---|---|
| E-001 | `01_evidence/original/nitroba.pcap` | `01_evidence/working/nitroba.pcap` | Verified (SHA-256 confirmed at intake) |

## Appendix A — Commands and queries

See `03_analysis/command_log.md` for full documentation of C-001 (Follow TCP Stream) and C-002 (IP filter and Gmail session inspection).

## Appendix B — Exhibits

See `05_exhibits/` for the exhibit register.

## Appendix C — Glossary

| Term | Definition |
|---|---|
| pcap | Packet capture file format recording raw network traffic |
| TCP stream | A reconstructed sequence of TCP packets forming a single conversation between two endpoints |
| Follow TCP Stream | Wireshark feature that reassembles and displays the full data exchanged in a TCP connection |
| willselfdestruct.com | An ephemeral web messaging service that destroys messages after they are viewed |
| Ephemeral messaging | A messaging paradigm where message content is deleted after delivery or viewing |
| IOC | Indicator of Compromise — an observable artifact that may indicate malicious or policy-violating activity |
