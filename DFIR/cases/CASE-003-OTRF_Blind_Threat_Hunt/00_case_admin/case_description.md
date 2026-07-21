# Windows Domain Suspicious Activity Investigation

## Background

Security monitoring detected suspicious script execution and unusual outbound network activity in a Windows domain environment. The available evidence includes Windows host telemetry and network telemetry collected from the environment.

## Investigation objective

Determine whether malicious activity occurred, identify the affected systems and accounts, and reconstruct the sequence of relevant events.

## Initial questions

1. Which systems and accounts are involved?
2. What activity triggered the initial suspicion?
3. What processes, scripts, or commands were executed?
4. Did the activity spread to additional systems?
5. Was persistence established?
6. Was information collected, staged, or transferred?
7. Which conclusions are directly supported by the evidence?
8. What evidence or visibility is missing?

## Available evidence

* Windows host telemetry
* Network packet captures
* Zeek network logs

## Constraints

* No threat actor has been identified.
* No malicious tool or technique should be assumed.
* The initial affected host is unknown.
* The full incident scope is unknown.
* Published walkthroughs, labels, and ground truth must not be consulted during the investigation.

## Analyst instruction

Begin by understanding the evidence sources, time range, systems, accounts, and normal activity. Form and test hypotheses based only on the supplied evidence.
