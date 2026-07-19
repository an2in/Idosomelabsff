# CASE-001 — 2008 Nitroba University Harassment

## Portfolio summary

Nitroba State University received a harassment complaint from Chemistry 109 teacher Lily Tuckrige, who had been receiving threatening emails at her personal Yahoo Mail account. A network tap placed on the suspect dorm room's Ethernet port captured all traffic in `nitroba.pcap` (E-001, 56 MB). Analysis of the capture in Wireshark identified TCP stream 1707 as an HTTP POST to `willselfdestruct.com` whose payload matches the harassing message received by the victim, and TCP stream 1611 as a Gmail authentication session on the same device showing the server response `"Loading jcoachj@gmail.com…"`. Cross-referencing that Gmail account against the Chemistry 109 course roster identifies the account holder as enrolled student **Johnny Coach**, providing a high-confidence attribution. The primary remaining uncertainty is that the dorm room's open, passwordless Wi-Fi router cannot be ruled out as a vector for a third party — device-level corroboration via endpoint forensics was not performed.

## Case status

- Status: Closed
- Start date: 2026-07-19
- Report date: 2026-07-20
- Investigator: an2in
- Case type: Network forensics / cyber-harassment
- Reporting time zone: UTC+7

## Published materials

- [Executive summary](04_reports/executive_summary.md)
- [Technical report](04_reports/technical_report.md)
- [Timeline](03_analysis/timeline.csv)
- [Findings register](03_analysis/findings_register.csv)

P/S: This looks like a typical CTF challenge, but it requires me to report meticulously:D.