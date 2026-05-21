# Day 03 — Linux Commands Cheat Sheet

> Building command-line efficiency for real-world DevOps and production troubleshooting.

---

# 📌 Overview

Linux command-line proficiency is one of the most important skills for DevOps Engineers, System Administrators, and Cloud Engineers.

Production incidents are often diagnosed and resolved directly from the terminal.

Understanding commonly used Linux commands improves:

* troubleshooting speed
* operational efficiency
* infrastructure visibility
* debugging confidence

Day 03 focuses on creating a practical Linux command cheat sheet covering:

* Process Management
* File System Navigation
* Networking Troubleshooting
* Log Inspection
* System Monitoring

---

# ⚙️ Process Management Commands

| Command              | Purpose                         |
| -------------------- | ------------------------------- |
| `ps aux`             | Display all running processes   |
| `top`                | Real-time process monitoring    |
| `htop`               | Interactive process viewer      |
| `pstree`             | Display process hierarchy       |
| `kill PID`           | Terminate a process by PID      |
| `pkill process_name` | Kill process using process name |
| `jobs`               | Show background jobs            |
| `bg`                 | Resume process in background    |
| `fg`                 | Bring process to foreground     |
| `uptime`             | Show system uptime and load     |

---

# 📂 File System Commands

| Command                 | Purpose                     |
| ----------------------- | --------------------------- |
| `pwd`                   | Show current directory      |
| `ls -la`                | List files with permissions |
| `cd directory`          | Change directory            |
| `mkdir folder`          | Create directory            |
| `rm -rf folder`         | Remove files/directories    |
| `cp source destination` | Copy files                  |
| `mv source destination` | Move or rename files        |
| `touch file.txt`        | Create empty file           |
| `find / -name file`     | Search for files            |
| `du -sh *`              | Check directory sizes       |

---

# 📜 Log & File Inspection Commands

| Command                 | Purpose                   |
| ----------------------- | ------------------------- |
| `cat file.txt`          | Display file contents     |
| `less file.txt`         | Read large files          |
| `head file.txt`         | View first lines          |
| `tail file.txt`         | View last lines           |
| `tail -f app.log`       | Monitor logs in real time |
| `grep "error" file.log` | Search text patterns      |
| `wc -l file.txt`        | Count lines               |
| `sort file.txt`         | Sort file contents        |

---

# 🌐 Networking Troubleshooting Commands

| Command                 | Purpose                   |
| ----------------------- | ------------------------- |
| `ping google.com`       | Test network connectivity |
| `ip addr`               | Display IP addresses      |
| `curl website.com`      | Test HTTP requests        |
| `dig google.com`        | DNS lookup                |
| `netstat -tulnp`        | View listening ports      |
| `ss -tulnp`             | Display socket statistics |
| `traceroute google.com` | Trace network path        |
| `hostname -I`           | Display local IP          |

---

# 💾 System Monitoring Commands

| Command    | Purpose                       |
| ---------- | ----------------------------- |
| `df -h`    | Check disk space              |
| `free -h`  | Display memory usage          |
| `uname -a` | Show system information       |
| `whoami`   | Display current user          |
| `history`  | Show command history          |
| `date`     | Display current date and time |

---

# 🚀 Why These Commands Matter in DevOps

In real production environments, Linux commands help engineers:

* inspect failing applications
* troubleshoot network connectivity
* analyze logs
* monitor system performance
* debug infrastructure issues
* reduce downtime quickly

Efficient command-line usage is a core DevOps skill.

---

# ✅ Practical Tasks Performed

During Day 03, I:

* Practiced commonly used Linux commands
* Explored process monitoring tools
* Performed networking checks
* Practiced log inspection commands
* Learned basic troubleshooting workflows
* Worked inside Ubuntu WSL environment

---

# 📚 Key Takeaways

* Linux commands are essential for troubleshooting infrastructure
* Process monitoring helps diagnose system issues
* Networking commands assist in connectivity debugging
* Log inspection is critical during production incidents
* Command-line efficiency improves operational productivity

---

---

# 📖 Learning Outcome

Day 03 strengthened my Linux command-line fundamentals and improved my confidence in navigating, monitoring, and troubleshooting Linux systems — foundational skills for modern DevOps engineering.
