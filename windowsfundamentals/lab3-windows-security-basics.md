# Windows Fundamentals 3

**Platform:** TryHackMe  
**Path:** Cyber101  
**Module:** Windows and AD Fundamentals  
**Difficulty:** Easy 

---

## 🎯 Learning Objectives
- System Integrity & Patch Management: Comprehend the Windows Update lifecycle and the significance of "Patch Tuesday" in vulnerability management.
- Endpoint Defense Mechanisms: Configure and audit Microsoft Defender’s real-time protection, cloud-delivered intelligence, and attack surface reduction.
- Host-Based Perimeter Security: Manage Windows Firewall profiles (Domain, Private, Public) and analyze inbound/outbound rule sets for network hardening.
- Hardware-Rooted Security & Encryption: Understand the role of the Trusted Platform Module (TPM) and BitLocker in protecting Data-at-Rest (DaR).
- Data Resiliency & Anti-Ransomware: Evaluate the Volume Shadow Copy Service (VSS) for system recovery and recognize common malware techniques used to disable these backups.

---

## 📖 Key Concepts (in my own words)
- Windows Security Center: A unified dashboard for managing defensive layers, including threat protection, firewall status, and device health. It uses a traffic-light system (Green/Yellow/Red) to indicate the urgency of security actions.
- SmartScreen & Exploit Protection: Advanced security features that protect against phishing, malicious downloads, and memory-based attacks (like buffer overflows) using techniques such as DEP (Data Execution Prevention) and ASLR.
- Trusted Platform Module (TPM): A dedicated, tamper-resistant physical microcontroller that provides hardware-based security for cryptographic operations and secure boot processes.
- Volume Shadow Copy Service (VSS): A framework that enables the creation of "snapshots" of disk volumes, allowing for data restoration even while files are in use.

---

## 🛠️ Practical Application

### Step 1 - [Lifecycle & Vulnerability Management]
Maintaining system updates is the most basic yet critical form of defense. Windows Update settings allow for the management of security patches, which Microsoft typically releases on the second Tuesday of each month ("Patch Tuesday").
When a system isn't update, it can be vulnerable to attacks via broken apps or API's.

Practical Note: For a SOC Analyst, verifying the update history is essential during an investigation to determine if a machine was vulnerable to a specific "Zero-Day" or known exploit at the time of an incident.

### Step 2 - [Real-Time Threat Detection]
Microsoft Defender serves as the primary EDR/Antivirus solution. Key settings include:

Real-time Protection: Actively monitors for malware execution.
Automatic Sample Submission: Sends suspicious files to Microsoft's cloud for analysis, contributing to global threat intelligence.

Key Insight: Utilizing "Controlled Folder Access" is a vital hardening step to prevent unauthorized applications (such as Ransomware) from modifying sensitive data in protected directories.

### Step 3 - [Network Hardening via Firewall Profiles]
Windows Firewall applies different security postures based on the network environment, there is three profiles:

Domain: When the host is the domain controller
Public: Used to designate public networks
Private: Most used in home network or designed private networks

Practical Note: If an analyst detects C2 communication, the Windows Firewall advanced settings can be used to immediately block specific outbound ports or IP addresses.

### Step 4 - [Cryptographic Integrity & Data Protection]
BitLocker provides full-disk encryption, integrating with the TPM to ensure that data cannot be accessed if the drive is removed or the system is tampered with.

Critical Knowledge: If a system lacks a TPM 1.2 or later, a physical USB startup key is required to enable BitLocker, highlighting the importance of hardware-based trust..

## Why it matters
Mastering these Windows internal mechanisms is fundamental to modern incident response. It enables a SOC Analyst to rapidly isolate suspicious processes via Resource Monitor and identify stealthy persistence mechanisms within the Registry. Furthermore, it supports system hardening efforts by allowing for efficient resource management and service optimization, directly impacting an organization's security posture and operational uptime.
