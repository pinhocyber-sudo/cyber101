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
ssh tryhackme@10.10.x.x
password
```
### Step 2 - [Advanced File System Administration]
Efficiency in managing system objects and directory structures.
```bash
touch web_config.txt          # File creation
mkdir -p internal/backups     # Recursive directory creation
cp logs.txt /tmp/             # Data migration to volatile storage
mv old_data.txt archival/     # File relocation and renaming
rm -rf sensitive_data/        # Secure deletion of directory trees
```
### Step 3 - [Advanced File System Administration]
Understanding file attributes and switching user contexts to performe admnistrative tasks.
```bash
ls -la                        # Detailed listing (including hidden system files)
chmod 600 private_key.pem     # Restricted access: Read/Write for owner only
su -l specialist_user         # Switching user context with environment initialization
```
### Step 4 - [Directory Exploration]
File types and standart Linux partitions for incident responses or system auditing.
```bash
file unknown_binary           # Identifying file metadata without extensions
cd /var/log                   # Investigating system and service logs
ls /etc/passwd                # Auditing system user configurations
```
## Why it matters

Mastering these core skills is like building the essential foundation for anyone looking to grow in Infrastructure Management or Security Operations (SOC). The Linux directory hierarchy and file permissions is the same of your first line of defense, where the system hardering starts, preventing that the wrong people have access to the right data. Furthermore understanding volatile storage (/tmp) and system logs (/var/log) is what separates a beginner from a professional in Digital Forensics and Incident Response (DFIR). These areas are like the "digital crime scenes" of a server they are the first places we check to find the footprints of an intruder or to diagnose a critical system error
