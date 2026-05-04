# Windows Fundamentals 2

**Platform:** TryHackMe  
**Path:** Cyber101  
**Module:** Windows and AD Fundamentals  
**Difficulty:** Easy 

---

## 🎯 Learning Objectives
- System Configuration & Optimization: Utilize the System Configuration utility to manage boot parameters and service isolation for troubleshooting.
- Basics of Telemetry & Monitoring: Identify abnormal processes and outbound connections using Resource Monitor
- Registry Architecture: Identify persistence mechanisms in Registry (Run/RunOnce keys)
- Hardware & Software Inventory: Use System Information tools to gather granular data on the operating environment and hardware components.

---

## 📖 Key Concepts (in my own words)
- Windows Registry: A centralized hierarchical database that stores low-level settings for the OS and applications. It is divided into "Hives" (like HKLM and HKCU) that dictate everything from hardware drivers to user preferences.
- MSConfig (System Configuration): A powerful tool for identifying issues during the boot process. It allows an administrator to perform "Clean Boots" by disabling non-Microsoft services, which is essential for isolating malicious or faulty software.
- Event Viewer: The primary tool for system auditing. It categorizes logs into Application, Security, Setup, and System, providing a chronological trail of everything that happens on the machine.
- Resource Monitor (ResMon): Offers a deep dive into CPU, Memory, Disk, and Network telemetry, showing exactly which process is interacting with which file or IP address.

---

## 🛠️ Practical Application

### Step 1 - [System Information & Inventory Management]
Accurate inventory is the first step in any security framework. Using msinfo32 allows for a complete dump of the system’s hardware resources and software environment. It can opened via the msconfig interface or via win + r and typing msinfo32

Practical Note: For a SOC Analyst, this tool is vital to quickly identify the OS version, BIOS mode, and installed drivers during the initial phases of an investigation.

### Step 2 - [Resource Telemetry & Bottleneck Analysis]
While Task Manager provides a surface view, Resource Monitor allows for granular analysis.

Key Insight: The "Network" tab in Resource Monitor is particularly useful for detecting "C2" (Command and Control) traffic by showing active TCP connections and the specific processes initiating them.
Shortcut: resmon via Run (Win + R).

### Step 3 - [Windows Registry Investigation]
The Windows Registry is a central hierarchy used to store information necessary to configure the system for one or more users, applications, and hardware devices.
Navigating the Registry is critical for both configuration and forensics.
```bash
HKLM (HKEY_LOCAL_MACHINE): Contains settings that apply to all users (global).
HKCU (HKEY_CURRENT_USER): Contains settings specific to the logged-in user.
```
Practical Note: Attackers often use the "Run" or "RunOnce" keys within the Registry to maintain persistence. Knowing how to audit these keys is a fundamental defensive skill.

### Step 4 - [Event Auditing & Troubleshooting]
The Event Viewer (eventvwr.msc) is where an admin looks when "something goes wrong."

Critical Logs: The Security log (Event ID 4624 for successful logins and 4625 for failed logins) is the primary source for auditing access control and detecting unauthorized entry attempts.
Practical Note: If an Event Log has a bunch of 4625, I can think there's a brute force attack going on.

## Why it matters
Mastering these Windows internal mechanisms is fundamental to modern incident response. It enables a SOC Analyst to rapidly isolate suspicious processes via Resource Monitor and identify stealthy persistence mechanisms within the Registry. Furthermore, it supports system hardening efforts by allowing for efficient resource management and service optimization, directly impacting an organization's security posture and operational uptime.

