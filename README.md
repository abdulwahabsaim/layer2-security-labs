<div align="center">

# 🔒 Layer 2 Switching Infrastructure & Security Labs

[![Domain](https://img.shields.io/badge/Domain-Layer_2_Switching_&_Security-00599C?style=for-the-badge&logo=cisco&logoColor=white)](https://cisco.com)
[![Platform](https://img.shields.io/badge/Platform-Cisco_Catalyst_3650_/_2960-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)](https://cisco.com)
[![Technologies](https://img.shields.io/badge/Hardening-VLANs_|_Trunking_|_Port_Security_|_STP_Guards_|_ACLs-brightgreen?style=for-the-badge)]()
[![Defense](https://img.shields.io/badge/Defense-CAM_Overflow_|_Root_Hijack_|_Loop_Prevention-blueviolet?style=for-the-badge)]()
[![Status](https://img.shields.io/badge/Portfolio_Status-5_Labs_Verified-success?style=for-the-badge)]()

<p align="center">
  <b>A comprehensive Layer 2 campus networking portfolio demonstrating VLAN segmentation, IEEE 802.1Q trunking, switchport hardening, STP Root Guard, STP Loop Guard, and Extended Access Control Lists (ACLs).</b>
</p>

</div>

---

## 📌 Executive Overview

Local Area Networks (LANs) are vulnerable to broadcast storms, bridging loops, MAC address spoofing, and unauthorized access if switchports are left in default configurations.

This repository covers the complete Layer 2 security lifecycle on Cisco Catalyst switches:
* **Segmentation:** Isolating broadcast domains using VLANs and 802.1Q trunking.
* **Access Hardening:** Enforcing strict MAC address limits via Port Security.
* **STP Protection:** Defending Spanning Tree against rogue root bridge elections (Root Guard) and unidirectional link loops (Loop Guard).
* **Traffic Filtering:** Enforcing port-specific filtering via Extended Access Control Lists.

---

## 🗺️ Master Lab Catalog & Navigation

| Lab Directory | Topic & Security Focus | Key Mechanisms & Modes | Target Switches | Defense Objective |
| :--- | :--- | :--- | :--- | :--- |
| [**`01-access-control-lists-acl`**](./01-access-control-lists-acl) | Traffic Filtering & Access Control | Extended ACL 105, TCP Port 23 Filtering | Cisco 2811 Gateway | Block insecure Telnet management while permitting routing |
| [**`02-vlan-trunking-and-vtp`**](./02-vlan-trunking-and-vtp) | VLAN Segmentation & Trunking | IEEE 802.1Q, VTP Server/Client (Rev 2) | 2x Catalyst 2960 | Isolate Layer 2 broadcast domains across interswitch links |
| [**`03-port-security-mac-limiting`**](./03-port-security-mac-limiting) | Switchport MAC Hardening | Shutdown, Restrict, Protect, Sticky MACs | Catalyst 3650 | Prevent CAM table overflow & unauthorized rogue devices |
| [**`04-stp-root-guard`**](./04-stp-root-guard) | Spanning Tree Root Protection | `spanning-tree guard root`, `ROOT_Inc` state | 4x Catalyst 3650 | Prevent rogue Priority 0 switch from hijacking Root Bridge |
| [**`05-stp-bpdu-filtering-and-loop-guard`**](./05-stp-bpdu-filtering-and-loop-guard) | Bridging Loop Prevention | `loopguard default`, `loop-inconsistent` | 3x Catalyst 3650 | Prevent loops caused by unidirectional links or BPDU filter |

---

## 🛡️ Layer 2 Security Defense Matrix

```text
               ┌─────────────────────────────────────────────────────────┐
               │              Enterprise Campus Layer 2 Defense          │
               └────────────────────────────┬────────────────────────────┘
                                            │
         ┌──────────────────────────────────┼──────────────────────────────────┐
         ▼                                  ▼                                  ▼
┌──────────────────┐               ┌──────────────────┐               ┌──────────────────┐
│  Port Security   │               │  STP Root Guard  │               │  STP Loop Guard  │
│  (Access Ports)  │               │ (Designated Trk) │               │  (Non-Desg Trk)  │
├──────────────────┤               ├──────────────────┤               ├──────────────────┤
│ Drops rogue MACs │               │ Blocks superior  │               │ Prevents loops   │
│ Limits per-port  │               │ BPDUs; prevents  │               │ if BPDUs cease;  │
│ Shutdown/Restrict│               │ root hijacking.  │               │ loop-inconsistent│
└──────────────────┘               └──────────────────┘               └──────────────────┘
```

---

## 🧰 Master Layer 2 CLI Verification Cheat Sheet

| Diagnostic Objective | Cisco IOS Command | Expected Operational Output |
| :--- | :--- | :--- |
| **Verify Port Security** | `show port-security` | Displays secure ports, max allowed MACs, current count, violation counters, and active action. |
| **View Secure MACs** | `show port-security address` | Lists all learned MACs categorized by `SecureConfigured`, `SecureDynamic`, or `SecureSticky`. |
| **Inspect 802.1Q Trunks** | `show interfaces trunk` | Displays trunking status, 802.1q encapsulation, native VLAN, and allowed VLAN lists. |
| **Inspect Spanning Tree** | `show spanning-tree` | Displays Root Bridge ID, local Bridge Priority, path costs, and port states (`FWD`, `BLK`, `ROOT_Inc`). |
| **Verify ACL Hit Counters** | `show access-lists` | Displays configured ACL rules and real-time packet match counters (`match(es)`). |
| **Inspect Err-Disabled Ports** | `show interfaces status err-disabled` | Identifies ports shut down due to `psecure-violation` or `bpduguard`. |

---

## 📂 Repository File Structure

```text
layer2-security-labs/
├── README.md                                  <-- Master Repository Index
├── 01-access-control-lists-acl/
│   ├── README.md
│   ├── topology.png
│   ├── access-control-lists.pkt
│   ├── router-a-config.ios
│   └── router-b-config.ios
├── 02-vlan-trunking-and-vtp/
│   ├── README.md
│   ├── topology.png
│   ├── vlan-trunking.pkt
│   ├── sw-a-server-config.ios
│   └── sw-b-client-config.ios
├── 03-port-security-mac-limiting/
│   ├── README.md
│   ├── topology.png
│   ├── port-security.pkt
│   └── switch-port-security-config.ios
├── 04-stp-root-guard/
│   ├── README.md
│   ├── topology.png
│   ├── stp-root-guard.pkt
│   └── configs/ (s1, s2, s3, and attacker switch configs)
└── 05-stp-bpdu-filtering-and-loop-guard/
    ├── README.md
    ├── topology.png
    ├── bpdu-filtering-loop-guard.pkt
    ├── switch0-root-config.ios
    ├── switch1-backup-config.ios
    └── switch2-access-config.ios
