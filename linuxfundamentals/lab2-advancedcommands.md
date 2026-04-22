# Linux Fundamentals 2

**Platform:** TryHackMe  
**Path:** Cyber101  
**Module:** Linux Fundamentals  
**Difficulty:** Easy  

---

## 🎯 Learning Objectives
- Secure Remote Administration: Execute remote management of Linux servers using the SSH (Secure Shell) protocol.
- Advanced File System Management: Implement directory structures and manage data integrity through advanced CLI operations.
- Access Control & Permissions: Analyze and configure the Linux permission model (rwx) to ensure the Principle of Least Privilege (PoLP).
- System Investigation: Utilize manual pages (man) and file headers (file) to perform technical reconnaissance on unknown environments.

---

## 📖 Key Concepts (in my own words)
- Secure Shell (SSH): Encrypted communication protocol for remote command-line access.
- Directory Hierarchy: Understanding critical system paths such as /etc (config), /var/log (audit logs), and /tmp (volatile storage).
- Identity & Access Management (IAM): Managing user contexts and elevating privileges responsibly using su and sudo.

---

## 🛠️ Practical Application

### Step 1 - [Establishing Secure Remote Access]
The primary method for server administration. SSH ensures that all data is transmited, including credentials, is encrypted.
```bash
#Syntax: ssh [user]@[ip address]

