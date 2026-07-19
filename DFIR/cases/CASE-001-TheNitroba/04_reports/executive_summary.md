# Executive summary

## Case overview

Nitroba State University's IT department received a complaint from Chemistry Department teacher Lily Tuckrige, who had been receiving harassing emails at her personal address (`lilytuckrige@yahoo.com`). Prior email header analysis by the system administrator identified the source IP address as `140.247.62.34`, a dorm room assigned to three female students who share an open, passwordless Wi-Fi router. A network tap was placed on the dorm room's Ethernet port. On Monday 21 July 2008, the harassing party sent another message via the ephemeral service `willselfdestruct.com`. All packets captured by the tap are preserved in evidence item E-001 (`nitroba.pcap`). This investigation analysed that packet capture to determine whether a student enrolled in Chemistry 109 was responsible.

## Scope

Analysis was limited to the network traffic captured from the dorm room Ethernet tap (E-001 `nitroba.pcap`) and the Chemistry 109 course roster. No physical device forensics, router logs, or off-campus traffic were examined.

## Key findings

1. **Finding:** A TCP stream in `nitroba.pcap` originating from the dorm room network connects to `willselfdestruct.com` and contains HTTP payload content consistent with the harassing message received by the victim.  
   **Confidence:** High  
   **Why it matters:** Establishes network-level evidence that the harassing message was transmitted from a device on the dorm room network during the tap window.

2. **Finding:** A Gmail HTTP session in the same packet capture, originating from the same source IP, shows the Google server responding with `"Loading jcoachj@gmail.com…"`, identifying the authenticated Gmail account active on that device during the harassment event.  
   **Confidence:** High  
   **Why it matters:** Directly links the network activity to a specific authenticated user identity.

3. **Finding:** Cross-referencing `jcoachj@gmail.com` against the Chemistry 109 summer course roster identifies the account holder as student **Johnny Coach**, enrolled in Lily Tuckrige's class.  
   **Confidence:** High  
   **Why it matters:** Attributes the network activity and the harassing message to a specific identified student in the victim's class.

## Impact or investigative significance

Network-level evidence strongly associates the harassing message delivery (willselfdestruct.com TCP stream) with the authenticated Gmail account `jcoachj@gmail.com`, which the supplied course roster links to enrolled student Johnny Coach. The available network evidence does not independently establish who physically operated the device. Device-level attribution would require endpoint forensics not currently in scope.

## Immediate actions

- Present findings to Nitroba University's student conduct or disciplinary authority for review.
- Preserve `nitroba.pcap` (E-001) in its original, unmodified state as potential evidentiary material.
- Notify the system administrator to retain all related email header screenshots and complaint records.

## Longer-term recommendations

- Require password protection on all Wi-Fi access points in student dorm rooms (or prohibit unauthorized routers entirely) to enable reliable device-level attribution in future investigations.
- Deploy network logging with per-device MAC address tracking on dorm ports to support future attribution without requiring full packet capture.
- Consider endpoint forensics (disk imaging of the suspect device) to corroborate the network-level attribution if formal disciplinary or legal proceedings are initiated.

## Important limitations

- **Open Wi-Fi**: The absence of a password on the dorm room's Wi-Fi router means that a visitor or neighbour with physical proximity could theoretically have used the network, though the authenticated Gmail session substantially reduces this alternative.
- **No device-level forensics**: Without a disk image or login records from the specific device, it is not possible to confirm with absolute certainty which physical machine was used.
- **Ephemeral message content**: The content of the willselfdestruct.com message was recoverable only from the packet capture; the service itself destroyed the message after viewing.
- **Packet capture timestamps**: The exact time-of-day of the harassment event within the packet capture was not independently verified against a reference time source.
