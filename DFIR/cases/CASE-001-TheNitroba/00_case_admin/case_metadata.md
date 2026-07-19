# Case metadata

| Field | Value |
|---|---|
| Case ID | 001|
| Case title | 2008 Nitroba University Harassment|
| Investigator |an2in |
| Requester / source |Self-Directed Study / Evidence sourced from the Digital Corpora Nitroba University Scenario (2008). |
| Date received |19/07/2026 |
| Examination start | 19/07/2026|
| Examination end | |
| Reporting time zone | UTC+7 |
| Authority | Academic training exercise. Authorized under individual professional development using the open-source Digital Corpora educational license. |
| Status | Investigating |
| Original evidence location | The Internet |
| Working-copy location | DFIR/cases/CASE-001-TheNitroba/01_evidence/working/nitroba.pcap |
| Report version | 0.1 |

## Purpose

To investigate harassing emails sent to Chemistry Department teacher Lily Tuckrige, determine if a student enrolled in her Chemistry 109 summer class is responsible, and establish clear, conclusive evidence identifying the perpetrator.

### Included

- Analysis of the network traffic capture (`nitroba.pcap`) from the tapped Ethernet port of the suspects' dorm room.
- Analysis of the email headers and browser screenshots provided by the victim.
- Correlation of network traffic metadata, web requests, search history, and web-based email artifacts with the Chemistry 109 roster.
- Investigation of connection details surrounding `willselfdestruct.com` and Yahoo Mail.

### Excluded

- Direct physical or logical forensic analysis of client devices (laptops, phones) used by the dorm residents or their guests.
- Inspection of the internal system logs or configuration of the unauthorized Wi-Fi router.
- Investigation into Nitroba University network traffic outside of the tapped dorm room port.

## Initial information

Chemistry Department teacher Lily Tuckrige reported receiving harassing emails at her personal email address (`lilytuckrige@yahoo.com`). Headers from an early email showed the source IP address was `140.247.62.34`, which belongs to a Nitroba student dorm room shared by three women. The room's Ethernet connection is shared via an unauthorized, open Wi-Fi router with no password.
A network tap was placed on the dorm room's Ethernet port. On Monday, 7/21, Tuckrige received another harassing email sent via `willselfdestruct.com`. 
The available evidence consists of browser/email screenshots, the network packet capture (`nitroba.pcap`), and the Chemistry 109 course roster.

## Assumptions

- The packet capture (`nitroba.pcap`) represents a complete and unaltered record of the network traffic passing through the dorm room's Ethernet tap.
- The timestamps in the network log and the screenshots are accurate or can be correlated accurately.
- The provided Chemistry 109 course roster is complete and correct.

## Constraints

- The lack of encryption or password on the dorm room's Wi-Fi router allows for the possibility of external users (e.g., neighbors or visitors) utilizing the connection.
- No direct device forensics (mobile/PC disk images) or physical device access is authorized or available.
- The web service `willselfdestruct.com` destroys message contents upon viewing, leaving only the network traffic capture of the interaction as evidence of the transmission.
