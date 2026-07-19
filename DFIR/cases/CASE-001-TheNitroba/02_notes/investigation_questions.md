# Investigation questions

| ID | Question | Priority | Required evidence | Status | Answer / finding |
|---|---|---|---|---|---|
| Q-01 | Is a student from Chemistry 109 responsible for the harassing emails sent to Lily Tuckrige? | High | Network pcap; Chemistry 109 roster | Answered | Yes. Network traffic from the dorm room IP links to Gmail account `jcoachj@gmail.com`, identified as belonging to Chemistry 109 student Johnny Coach. |
| Q-02 | Does the network capture contain evidence of the willselfdestruct.com message transmission? | High | E-001 nitroba.pcap | Answered | Yes. A TCP stream in nitroba.pcap shows a connection from the culprit IP to willselfdestruct.com whose HTTP payload matches the harassing content received by the victim. |
| Q-03 | Could the traffic have originated from a third party using the open Wi-Fi rather than a dorm resident? | Medium | E-001 nitroba.pcap; Gmail session data | Partially addressed | The Gmail session response (`Loading jcoachj@gmail.com…`) ties the activity to an authenticated account. However, physical device attribution is not possible without endpoint forensics. |
