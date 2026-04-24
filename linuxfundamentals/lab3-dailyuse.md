# Linux Fundamentals 3

**Platform:** TryHackMe  
**Path:** Cyber101  
**Module:** Linux Fundamentals
**Difficulty:** Easy  

---

## 🎯 Learning Objectives
- Terminal Text Editing: Use clients like NANO or VIM to manipulate files and scripts via Linux Terminal
- Data Transfer & Web Server Basics: Deploy temporary web servers using Python modules and retrieve resources using wget and scp
- System Processes: Manage background tasks, utilize signals to control processes execution
- Automation Basics: Schedule tasks using Cron

---

## 📖 Key Concepts (in my own words)
- Crontab: A time-based job scheduler used to automate repetitive tasks like backups, log rotation, or system updates.
- Process Signals: Communication methods used to tell a process how to behave (e.g., SIGTERM for a graceful exit or SIGKILL for immediate termination).
- Package Management: The methodology of installing, updating, and removing software while maintaining security through GPG key verification.
- Service Management (systemctl): The interface for interacting with the init system (systemd) to start, stop, or enable services at boot.

---

## 🛠️ Practical Application

### Step 1 - [Basic Text Manipulation]
Terminal-based editors like Vim and Nano offer a more efficient way to handle data than simple echo and redirection operators. They allow for the creation and precise modification of persistent files in environments without a GUI.

```bash
nano task3.txt                # Opens the Nano editor for a specific file
# Use Ctrl + O to save and Ctrl + X to exit
vim script.sh                 # Standard advanced editor available on most systems
```

### Step 2 - [Resource Retrieval]
A fundamental skill for any technical professional is knowing how to transfer files securely. Using Python's HTTP module to serve files or wget to retrieve them is essential for deploying tools in remote environments.

```bash
wget http://10.10.x.x/flag.txt     # Downloads a file from a web server
python3 -m http.server 8000        # Starts a rapid-deployment web server on port 8000
scp user@remote:/path/to/file .    # Securely copies files over the SSH protocol
```
Practical Note:
python3 -m http.server 8000 is insecure by design (requires no authentication), so it's useful just for internal lab environments

### Step 3 - [Backgrounding]
Managing system load is crucial to ensure that long-running tasks do not lock the active terminal session, allowing for better multitasking and resource allocation.

```bash
ps aux | grep "apache"        # Lists all processes filtered by a keyword
top                           # Real-time system monitoring interface
kill -15 [PID]                # Sends a SIGTERM for a clean process shutdown
fg                            # Brings the most recent background task to the foreground
```
Practical Note:
SIGTERM allows cleanup, but some processes ignore SIGTERM and requires SIGKILL because it can be refused

### Step 4 - [Automation and System Maintenance]
Keeping a system updated and auditing events is vital for system health. Automation via Cron ensures these critical tasks are performed consistently without manual intervention.

```bash
crontab -e                    # Edits the scheduled tasks for the current user
sudo apt update && sudo apt full-upgrade    # Syncs repositories and applies security patches
ls /var/log/apache2/          # Locating web server logs (access.log and error.log)
```
Crontab Format:
```bash
* * * * * command
│ │ │ │ │
│ │ │ │ └── day of week
│ │ │ └──── month
│ │ └────── day of month
│ └──────── hour
└────────── minute
```

## Why it matters
These tools form the operational baseline for Linux environments. In real-world systems administration and security work, they are not theoretical knowledge they are daily use primitives for debugging live systems, moving data in constrained environments, controlling system processes and automating repetitive operationals tasks.

