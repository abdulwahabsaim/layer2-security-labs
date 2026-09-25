<div align="center">

# 🛡️ Enterprise Campus Switching & Layer 2 Security Labs

[![Infrastructure](https://img.shields.io/badge/Infrastructure-Campus_Switching_&_L2_Security-00599C?style=for-the-badge&logo=cisco&logoColor=white)](https://github.com/abdulwahabsaim)
[![Certification](https://img.shields.io/badge/Certification-Cisco_CCNA_200--301-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)](https://cisco.com)
[![Verified Labs](https://img.shields.io/badge/Verified_Labs-13_Production_Scenarios-brightgreen?style=for-the-badge)]()
[![Location](https://img.shields.io/badge/Location-Netherlands_🇳🇱-orange?style=for-the-badge)]()
[![Author](https://img.shields.io/badge/Author-Abdul_Wahab_Saim-blueviolet?style=for-the-badge)](https://linkedin.com/in/abdulwahabsaim)

<p align="center">
  <b>A comprehensive, production-grade repository of 13 hands-on enterprise campus switching, Layer 2 attack mitigation, Spanning Tree hardening, link aggregation, and control-plane security labs designed for Level 1 / Level 2 Network Operations Center (NOC) and Security roles.</b>
</p>

[Core Domains](#-core-technical-domains) • [Skills Matrix](#-topics--skills-coverage-matrix) • [Detailed Lab Directory](#-detailed-laboratory-catalog-13-scenarios) • [Campus Defense Matrix](#-layer-2-campus-defense--security-matrix) • [NOC Runbook](#-enterprise-switching--security-cli-runbook)

</div>

---

## 📌 Executive Summary

The Layer 2 access and distribution layers represent the most vulnerable boundaries in enterprise infrastructure. Because Ethernet was designed without intrinsic authentication, unhardened switchports are inherently susceptible to MAC flooding, rogue DHCP injection, ARP cache poisoning (Man-in-the-Middle), VLAN hopping via dynamic trunk negotiation, and spanning tree topology hijacking.

This repository documents a systematic collection of **13 production-style switching and security labs** designed and verified in Cisco Packet Tracer and GNS3.

Every lab enforces industry-standard hardening benchmarks:
* **Zero-Trust Access Layer:** Enforcing Trust Boundaries with DHCP Snooping, Dynamic ARP Inspection (DAI), and Port Security MAC limiting.
* **Resilient Spanning Tree:** Eliminating bridging loops and rogue root bridges using Root Guard, Loop Guard, and BPDU suppression.
* **High-Density Trunking & Aggregation:** Negotiating multi-chassis link aggregation via IEEE 802.3ad LACP, Cisco PAgP, and Layer 3 routed bundles while eradicating DTP vulnerabilities (`switchport nonegotiate`).
* **Control Plane Hardening:** Locking down administrative management via 2048-bit RSA keys, SSHv2, VTY `access-class` filtering, and discovery protocol suppression.

---

## 🧱 Core Technical Domains

```text
                               ┌──────────────────────────────────────────────────────────┐
                               │       ENTERPRISE CAMPUS SWITCHING & L2 SECURITY          │
                               └────────────────────────────┬─────────────────────────────┘
                                                            │
         ┌──────────────────────────┬───────────────────────┴───────────────┬──────────────────────────┐
         │                          │                                       │                          │
         ▼                          ▼                                       ▼                          ▼
┌──────────────────┐      ┌────────────────────┐                 ┌────────────────────┐      ┌────────────────────┐
│ SPANNING TREE &  │      │ LINK AGGREGATION & │                 │ ACCESS LAYER TRUST │      │ CONTROL PLANE &    │
│ LOOP DEFENSE     │      │ TRUNKING FABRIC    │                 │ & MITM DEFENSE     │      │ TRAFFIC FILTERING  │
├──────────────────┤      ├────────────────────┤                 ├────────────────────┤      ├────────────────────┤
│• STP Root Guard  │      │• 802.3ad LACP      │                 │• DHCP Snooping     │      │• SSHv2 (RSA 2048)  │
│• STP Loop Guard  │      │• Cisco PAgP        │                 │• Dynamic ARP (DAI) │      │• VTY Access-Class  │
│• BPDU Filtering  │      │• L3 Routed Bundles │                 │• Port Security     │      │• Ingress Ext ACLs  │
│• STP-HSRP Sync   │      │• VTP Multi-Modes   │                 │• Sticky MACs       │      │• LLDP Hardening    │
│• PVST+ Priorities│      │• DTP Nonegotiate   │                 │• Violation Modes   │      │• Voice VLAN CoS    │
└──────────────────┘      └────────────────────┘                 └────────────────────┘      └────────────────────┘
```

---

## 🎯 Topics & Skills Coverage Matrix

Use this matrix to locate specific protocols, security features, and operational scenarios across the 13 laboratories:

| Technical Topic / Security Defense | Primary Protocol / Feature | Implemented In | Key Cisco IOS Commands |
| :--- | :--- | :--- | :--- |
| **Layer 4 Protocol Filtering** | Extended ACLs (100–199) | [Lab 01](./01-access-control-lists-acl/) | `access-list 105 deny tcp`, `ip access-group in` |
| **VLAN Segmentation & Trunking** | 802.1Q & VTP Server/Client | [Lab 02](./02-vlan-trunking-and-vtp/) | `switchport mode trunk`, `vtp domain`, `vtp mode` |
| **Access Port MAC Limiting** | Cisco Port Security | [Lab 03](./03-port-security-mac-limiting/) | `switchport port-security`, `violation restrict/shutdown` |
| **Rogue Root Bridge Defense** | STP Root Guard | [Lab 04](./04-stp-root-guard/) | `spanning-tree guard root` |
| **Unidirectional Loop Prevention**| STP Loop Guard & BPDU Filter | [Lab 05](./05-stp-bpdu-filtering-and-loop-guard/) | `spanning-tree loopguard default`, `bpdufilter` |
| **Multi-Chassis Link Aggregation**| EtherChannel (LACP & PAgP)| [Lab 06](./06-etherchannel-lacp-pagp-layer3/) | `channel-group 1 mode active/desirable`, `no switchport` |
| **Reconnaissance Suppression** | IEEE 802.1AB LLDP Hardening | [Lab 07](./07-cdp-lldp-discovery-and-hardening/) | `lldp run`, `no cdp run`, `no lldp transmit/receive` |
| **Encrypted Device Administration**| SSHv2 & VTY Access-Class | [Lab 08](./08-secure-device-management-sshv2/) | `crypto key generate rsa`, `transport input ssh`, `access-class` |
| **Converged Telephony Access** | Switchport Voice VLAN | [Lab 09](./09-switchport-voice-vlan-telephony/) | `switchport voice vlan`, `switchport mode access` |
| **Man-in-the-Middle Mitigation** | DHCP Snooping & DAI | [Lab 10](./10-dhcp-snooping-and-dynamic-arp-dai/) | `ip dhcp snooping`, `ip arp inspection vlan`, `validate` |
| **Sub-Optimal Path Elimination** | STP & HSRP Synchronization | [Lab 11](./11-stp-hsrp-active-root-alignment/) | `spanning-tree vlan priority`, `standby priority`, `preempt` |
| **Domain Isolation & DTP Defense**| VTP Transparent & Nonegotiate| [Lab 12](./12-vtp-modes-and-dtp-hardening/) | `vtp mode transparent`, `switchport nonegotiate` |
| **Multi-Service Edge Firewalling**| Ingress Extended ACLs | [Lab 13](./13-enterprise-extended-acls-service-filtering/) | `access-list 101/102`, `eq domain`, `eq www`, `eq 443` |

---

## 🗺️ Detailed Laboratory Catalog (13 Scenarios)

### 🔹 [01-access-control-lists-acl](./01-access-control-lists-acl/)
* **Focus:** Layer 4 Extended Access Control Lists & Socket Filtering
* **Hardware:** Cisco 2811 Router
* **Key Topics Covered:** Extended ACL numerical ranges (`100–199`), filtering unencrypted management protocols (Telnet TCP port 23), matching source/destination subnets, evaluating the invisible implicit deny (`deny ip any any`), and inbound interface binding.

### 🔹 [02-vlan-trunking-and-vtp](./02-vlan-trunking-and-vtp/)
* **Focus:** 802.1Q Encapsulation, Departmental Segmentation & VTP Sync
* **Hardware:** 2x Catalyst 2960 Switches
* **Key Topics Covered:** Provisioning segmented broadcast domains (VLANs 2 & 3), establishing 802.1Q trunk links across inter-switch uplinks, configuring VTP Server and Client synchronization (Revision 2), and verifying inter-switch frame tagging.

### 🔹 [03-port-security-mac-limiting](./03-port-security-mac-limiting/)
* **Focus:** Layer 2 MAC Address Limiting & Violation Mitigation
* **Hardware:** Catalyst 3650 Multilayer Switch
* **Key Topics Covered:** Securing host access ports with `switchport port-security`, setting maximum MAC thresholds, comparing dynamic vs static vs sticky learning (`mac-address sticky`), configuring absolute aging timers, and testing all 3 violation modes (`protect`, `restrict`, `shutdown` into `err-disabled`).

### 🔹 [04-stp-root-guard](./04-stp-root-guard/)
* **Focus:** Spanning Tree Root Bridge Hijack Defense & `ROOT_Inc` State
* **Hardware:** 4x Catalyst 3650 Multilayer Switches
* **Key Topics Covered:** Simulating rogue switch injection with aggressive Bridge Priorities (`0`), deploying `spanning-tree guard root` on designated access/distribution ports, observing automatic transition into Root-Inconsistent (`ROOT_Inc`) blocking state, and validating automatic recovery upon rogue BPDU cessation.

### 🔹 [05-stp-bpdu-filtering-and-loop-guard](./05-stp-bpdu-filtering-and-loop-guard/)
* **Focus:** Bridging Loop Prevention, Unidirectional Link Failure & Loop Guard
* **Hardware:** 3x Catalyst 3650 Multilayer Switches
* **Key Topics Covered:** Demonstrating catastrophic Layer 2 broadcast storms caused by misconfigured `bpdufilter` on active trunks, enabling global `spanning-tree loopguard default`, transitioning non-designated alternate ports into `loop-inconsistent` blocking state upon BPDU loss, and preventing bridging loops.

### 🔹 [06-etherchannel-lacp-pagp-layer3](./06-etherchannel-lacp-pagp-layer3/)
* **Focus:** Multi-Chassis Link Aggregation (L2 LACP/PAgP & L3 Routed Bundles)
* **Hardware:** 2x Catalyst 3650 Multilayer Switches, 2x Catalyst 2960 Access Switches
* **Key Topics Covered:** Eliminating STP blocked links, configuring open-standard IEEE 802.3ad LACP (`channel-group 1 mode active`), configuring Cisco proprietary PAgP (`mode desirable`), provisioning static Layer 3 routed bundles (`no switchport`, `mode on`), IP addressing on logical `Port-channel` interfaces, and verifying hashing load-balance algorithms (`src-dst-ip`).

### 🔹 [07-cdp-lldp-discovery-and-hardening](./07-cdp-lldp-discovery-and-hardening/)
* **Focus:** IEEE 802.1AB LLDP Migration & Ingress Access-Port Hardening
* **Hardware:** Cisco 2911 Router, 2x Catalyst 2960 Switches
* **Key Topics Covered:** Disabling proprietary Cisco Discovery Protocol (`no cdp run`), enabling open-standard LLDP globally (`lldp run`), granularly suppressing discovery frame generation on untrusted host-facing access ports (`no lldp transmit`, `no lldp receive`, `no cdp enable`), and validating topology mapping across infrastructure uplinks.

### 🔹 [08-secure-device-management-sshv2](./08-secure-device-management-sshv2/)
* **Focus:** Control Plane Hardening, RSA 2048-bit Cryptography & VTY Access-Class
* **Hardware:** Catalyst 2960 Switch
* **Key Topics Covered:** Eradicating plaintext Telnet management, configuring local AAA user databases with Type 5 hashed secrets, generating 2048-bit RSA key pairs, enforcing SSHv2 (`transport input ssh`), configuring `exec-timeout` idle protections, and restricting remote VTY terminal sessions exclusively to an authorized management workstation via a Standard ACL (`access-class 1 in`).

### 🔹 [09-switchport-voice-vlan-telephony](./09-switchport-voice-vlan-telephony/)
* **Focus:** Converged Campus Access & 802.1p/Q Voice Multiplexing
* **Hardware:** Catalyst 3650 Switch, Cisco 7960 IP Phones, Router Gateway
* **Key Topics Covered:** Daisy-chaining IP Phones and workstations over a single physical cable, configuring auxiliary Voice VLANs (`switchport voice vlan 20`) alongside untagged Data VLANs (`switchport access vlan 10`), utilizing CDP for automated Voice VLAN ID negotiation, 802.1p CoS tagging, and 802.1Q trunk uplink routing.

### 🔹 [10-dhcp-snooping-and-dynamic-arp-dai](./10-dhcp-snooping-and-dynamic-arp-dai/)
* **Focus:** Rogue DHCP Mitigation, Snooping Binding Database & Dynamic ARP Inspection
* **Hardware:** Cisco 2911 Authorized DHCP Server, 2x Catalyst 2960 Switches
* **Key Topics Covered:** Enforcing Layer 2 Trust Boundaries (`ip dhcp snooping trust`), mitigating Option 82 zero-giaddr drops (`no ip dhcp snooping information option`), building the dynamic MAC-to-IP snooping database, and deploying Dynamic ARP Inspection (DAI) with deep payload validation (`validate src-mac dst-mac ip`) to eliminate ARP cache poisoning / Man-in-the-Middle attacks.

### 🔹 [11-stp-hsrp-active-root-alignment](./11-stp-hsrp-active-root-alignment/)
* **Focus:** Layer 2/3 Convergence & Trunk Hair-Pinning Elimination
* **Hardware:** 2x Catalyst 3650 Multilayer Switches, 2x Catalyst 2960 Access Switches
* **Key Topics Covered:** Resolving the classic "Trunk Hair-Pinning" latency bottleneck, aligning Layer 2 Spanning Tree Primary Root Bridge priorities (`24576`) with Layer 3 HSRPv2 Active Gateway priorities (`105` + `preempt`) for VLAN 10 on DSW1, and mirroring alignment for VLAN 20 on DSW2 to achieve an optimal Active-Active distribution architecture.

### 🔹 [12-vtp-modes-and-dtp-hardening](./12-vtp-modes-and-dtp-hardening/)
* **Focus:** VTP Multi-Mode Architecture (Transparent Transit) & DTP Suppression
* **Hardware:** 3x Catalyst 2960 Switches (Linear Transit Architecture)
* **Key Topics Covered:** The 3-tier VTP domain model (`SW1` Server Rev 5 ➔ `SW2` Transparent Rev 0 ➔ `SW3` Client Rev 5), proving Transparent mode switches forward VTP advertisements without altering local databases, isolating local VLANs, and suppressing Dynamic Trunking Protocol frame generation on all uplinks (`switchport nonegotiate`) to eliminate VLAN hopping risks.

### 🔹 [13-enterprise-extended-acls-service-filtering](./13-enterprise-extended-acls-service-filtering/)
* **Focus:** Multi-Service Layer 4 Filtering & Ingress Traffic Suppression
* **Hardware:** 2x Cisco 2911 Routers, 4x Switches, Dedicated DNS & Web Servers
* **Key Topics Covered:** Enforcing the Golden Rule of Extended ACL placement (as close to the source as possible), applying inbound ACLs `101` and `102` at LAN ingress boundaries, filtering application sockets (DNS UDP 53, HTTP TCP 80, HTTPS TCP 443), enforcing host isolation, and saving serial WAN transit bandwidth by dropping unauthorized packets before WAN serialization.

---

## 📊 Layer 2 Campus Defense & Security Matrix

A quick-reference architectural comparison of the Layer 2 security mechanisms implemented across this repository:

| Layer 2 Security Feature | Attack Vector Mitigated | Optimal Placement | Reaction When Violation Triggered | Standard / RFC |
| :--- | :--- | :--- | :--- | :--- |
| **Port Security** | MAC Flooding / CAM Table Exhaustion | Access Ports only | Drops traffic (`protect`/`restrict`) or shuts down (`shutdown`) | Cisco IOS Standard |
| **DHCP Snooping** | Rogue DHCP Servers / Man-in-the-Middle | Access Layer (Global) | Drops DHCP Offers/Acks on untrusted ports | RFC 7513 |
| **Dynamic ARP Inspection (DAI)** | ARP Poisoning / Gratuitous ARP Spoofing| Access Layer (Per-VLAN)| Drops invalid ARP packets not in Snooping table | RFC 826 Mitigation |
| **STP Root Guard** | Rogue Root Bridge Hijacking | Designated Root Ports | Transitions interface to `ROOT_Inc` (blocking) | Cisco IOS Standard |
| **STP Loop Guard** | Unidirectional Link Failure / Lost BPDUs | Root & Alternate Ports | Transitions interface to `loop-inconsistent` (blocking)| Cisco IOS Standard |
| **DTP Suppression (`nonegotiate`)**| VLAN Hopping / Dynamic Trunk Spoofing | All Switchports | Disables DTP negotiation; hardcodes port mode | IEEE 802.1Q Hardening |
| **VTY `access-class`** | Unauthorized Control-Plane Telnet/SSH | Virtual Terminal Lines | Refuses TCP SYN connection before authentication | Cisco IOS Standard |

---

## 🧰 Enterprise Switching & Security CLI Runbook

Essential Cisco IOS diagnostic commands demonstrated and documented across these 13 laboratories:

```text
================================================================================
CATEGORY 1: SPANNING TREE & LAYER 2 CONVERGENCE
================================================================================
show spanning-tree                    # Displays global STP state, active Root ID, port roles (Root/Desg/Altn)
show spanning-tree vlan [id]          # Displays Spanning Tree topology and bridge priority for a specific VLAN
show spanning-tree summary            # High-level overview of global STP features (PortFast, BPDU Guard, Loop Guard)
show spanning-tree root               # Displays Root Bridge MAC address and path cost for all active VLANs
show spanning-tree detail             # Detailed view verifying Loop Guard states and ROOT_Inc blocking events

================================================================================
CATEGORY 2: LINK AGGREGATION & TRUNKING
================================================================================
show etherchannel summary             # Displays bundle state flags (SU/RU) and individual port member states (P/I/s)
show etherchannel load-balance        # Displays the active frame hashing algorithm (src-dst-ip / src-mac)
show interfaces trunk                 # Displays active 802.1Q trunking interfaces and allowed/active VLAN lists
show interfaces [id] switchport       # Displays administrative vs operational mode, Native VLAN, and DTP state

================================================================================
CATEGORY 3: ACCESS LAYER SECURITY & TRUST BOUNDARIES
================================================================================
show port-security interface [id]     # Inspects port status, violation counters, and learned secure MAC addresses
show ip dhcp snooping                 # Verifies trusted vs untrusted interface boundaries and Option 82 status
show ip dhcp snooping binding         # Displays the dynamic MAC-to-IP lease database built from untrusted ports
show ip arp inspection                # Displays DAI validation state (src-mac/dst-mac/ip) and dropped packet counts
show ip arp inspection interfaces     # Confirms which uplinks are configured as DAI Trusted
show vtp status                       # Displays VTP domain, operating mode (Server/Trans/Client), and revision number
show access-lists                     # Displays all Standard/Extended ACL statements and real-time rule match counters
show ip ssh                           # Confirms SSH daemon operational status, protocol version, and key status
show lldp neighbors                   # Displays adjacent infrastructure devices discovered via IEEE 802.1AB LLDP
```

---

## 📁 Standardized 4-File Package Structure

To maintain production standards, every lab subfolder in this repository is strictly organized as a self-contained 4-file unit:

```text
0X-lab-topic-name/
├── README.md                      # In-depth technical documentation, schema tables & CLI proof
├── topology.png                   # Clean, 16:9 cropped enterprise topology diagram
├── <lab-name>.pkt                 # Completed, verified Cisco Packet Tracer simulation file
└── <device>-config.ios            # Syntax-highlighted, clean running configurations (paste-ready)
```

---

## 👤 Profile

* **Candidate:** Abdul Wahab Saim
* **Primary Certification:** Cisco Certified Network Associate (CCNA 200-301)
* **Professional Links:**
  * **GitHub:** [github.com/abdulwahabsaim](https://github.com/abdulwahabsaim)
  * **Live Portfolio Website:** [abdulwahabsaim.github.io](https://abdulwahabsaim.github.io)
  * **LinkedIn Profile:** [linkedin.com/in/abdulwahabsaim](https://www.linkedin.com/in/abdulwahabsaim/)

---
