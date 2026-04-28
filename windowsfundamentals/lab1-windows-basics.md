# Windows Fundamentals 1

**Platform:** TryHackMe  
**Path:** Cyber101  
**Module:** Windows and AD Fundamentals  
**Difficulty:** Easy  

---

## 🎯 Learning Objectives
- Remote Administration: Leverage Remote Desktop Protocol (RDP) via CLI tools to manage remote Windows instances.
- File System Governance: Understand the architecture of NTFS, including permissions, journaling, and Alternate Data Streams (ADS).
- Identity & Access Management (IAM): Manage local user accounts and groups to enforce the Principle of Least Privilege (PoLP)
- Security Mechanisms: Analyze the role of User Account Control (UAC) in mitigating unauthorized system changes.
- System Auditing Basics: Utilize native administrative tools (Task Manager, Control Panel) to monitor resource consumption and system configuration.

---

## 📖 Key Concepts (in my own words)
- NTFS (New Technology File System): The standard Windows file system that provides advanced features like file-level security (ACLs), data recovery through journaling, and metadata storage.
- UAC (User Account Control): A fundamental security tool that prevents malware from executing with administrative privileges without explicit user consent.
- System32 Folder: The "core" of the OS, houses the critical .dll files and executables required for the Windows kernel and system processes to run.
- Service Management: The interface (accessible via services.msc) used to manage background processes that run independently of user sessions, essential for hosting web servers or database engines.

---

## 🛠️ Practical Application

### Step 1 - [File System & Permissions Audit]
Correct NTFS configuration is vital for data integrity. Checking file properties allows an admin to verify if a user has "Read," "Modify," or "Full Control" over sensitive directories.

Key Insight: Unlike FAT32, NTFS allows for granular permissions that are essential for securing corporate data.

### Step 2 - [Local Account & Group Management]
Standardizing access via groups is more scalable than managing individual users. Using the Microsoft Management Console (MMC) snap-ins provides a centralized view of system access. 
```bash
# Opens the Local Users and Groups manager
lusrmgr.msc
```
Practical Note: To grant a user remote access without making them a full administrator, they should be added to the "Remote Desktop Users" group. This limits the attack surface of the machine.

### Step 3 - [Process Monitoring and Resource Management]

Identifying high-resource consumers is one of the keys to maintaining system uptime. The Task Manager provides real-time telemetry on CPU, Memory, and Disk usage being crucial to do the backgrounding of the OS.

Shortcut: Ctrl + Shift + Esc
Practical Note: The details tab is essential for identifying the Process ID (PID) and the associated user account, which is critical during incident response to find unauthorized executions

## Why it matters
These skills represent the operational baseline for managing any Windows-based infrastructure. Whether you are performing system hardening, troubleshooting performance issues, or conducting a security audit, understanding how Windows handles file permissions, user hierarchies, and administrative boundaries is fundamental to securing the environment.
