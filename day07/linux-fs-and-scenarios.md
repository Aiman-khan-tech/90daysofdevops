# Day 07 - Linux File System Hierarchy & Scenario-Based Practice

## Part 1: Linux File System Hierarchy

### / (Root Directory)

* The top-level directory in Linux. Everything starts from here.
* Command:

```bash
ls -l /
```
<img width="486" height="337" alt="image" src="https://github.com/user-attachments/assets/102f1e65-d9f8-4d51-908e-95990b4a7330" />


* Observed: bin, etc, home, usr, var
* I would use this when navigating the overall Linux filesystem.

### /home

* Stores personal files and directories for users.
* Command:

```bash
ls -l /home
```
<img width="481" height="73" alt="image" src="https://github.com/user-attachments/assets/2309d5e1-ff59-4b2f-9b33-5de172fb63c6" />

* Observed: user directories
* I would use this when managing user data and scripts.

### /root

* Home directory of the root user.
* Command:

```bash
sudo ls -l /root
```
<img width="422" height="71" alt="image" src="https://github.com/user-attachments/assets/ebaa9e5b-dc21-49b3-ad7b-8d128f919434" />

* Observed: root-specific configuration files
* I would use this when logged in as root for administration tasks.

### /etc

* Contains system-wide configuration files.
* Command:

```bash
ls -l /etc
```
<img width="525" height="601" alt="image" src="https://github.com/user-attachments/assets/8df49380-1ab6-44e5-ad7a-76913575fb49" />

* Observed: hostname, hosts, passwd
* I would use this when troubleshooting configuration issues.

### /var/log

* Stores application and system logs.
* Command:

```bash
ls -l /var/log
```
<img width="745" height="402" alt="image" src="https://github.com/user-attachments/assets/1c1a1fc7-d6b6-4e28-a4a5-9216650a7b3b" />

* Observed: syslog, auth.log, journal
* I would use this when investigating service failures.

### /tmp

* Temporary storage used by applications and users.
* Command:

```bash
ls -l /tmp
```
<img width="742" height="202" alt="image" src="https://github.com/user-attachments/assets/0c00d85d-d612-4b65-8d8a-39a79cecbc24" />

* Observed: temporary files and directories
* I would use this for temporary testing and scripts.

### /bin

* Contains essential Linux commands.
* Command:

```bash
ls -l /bin
```
<img width="473" height="52" alt="image" src="https://github.com/user-attachments/assets/9d4229b4-16c1-457c-96bb-7c6541fb6c8d" />

* Observed: ls, cp, mv
* I would use this to understand where core commands reside.

### /usr/bin

* Contains most user command binaries.
* Command:

```bash
ls -l /usr/bin | head
```
<img width="663" height="171" alt="image" src="https://github.com/user-attachments/assets/4cfe8708-dedd-47f4-8bfa-d85817e99281" />

* Observed: hundreds of executable programs
* I would use this when locating installed commands.

### /opt

* Used for optional or third-party applications.
* Command:

```bash
ls -l /opt
```
<img width="417" height="52" alt="image" src="https://github.com/user-attachments/assets/4736d9e3-ba5b-405e-aafc-4376e156d881" />

* Observed: application directories
* I would use this when managing third-party software.

---

## Hands-On Tasks

### Find Largest Log Files

```bash
du -sh /var/log/* 2>/dev/null | sort -h | tail -5
```

Observation:
Identified the largest log directories consuming disk space.

### View Hostname Configuration

```bash
cat /etc/hostname
```
<img width="578" height="50" alt="image" src="https://github.com/user-attachments/assets/0e650310-5b6e-4520-a158-ac5b7238ec25" />

Observation:
Displayed the system hostname.

### Check Home Directory

```bash
ls -la ~
```
<img width="746" height="212" alt="image" src="https://github.com/user-attachments/assets/27288f5e-9b15-4f8e-a682-4223bdb0f024" />

Observation:
Listed personal files, hidden files, and configuration directories.

---

# Part 2: Scenario-Based Practice

## Scenario 1: Service Not Starting

### Step 1

```bash
systemctl status myapp
```

Why: Check if the service is active, failed, or stopped.

### Step 2

```bash
journalctl -u myapp -n 50
```

Why: Review recent logs for errors.

### Step 3

```bash
systemctl is-enabled myapp
```

Why: Verify whether the service starts automatically after reboot.

### Step 4

```bash
systemctl list-units --type=service
```

Why: Confirm the service exists and is recognized by systemd.

### What I Learned

Always check service status first before making changes.

---

## Scenario 2: High CPU Usage

### Step 1

```bash
top
```

Why: View live CPU and memory utilization.

### Step 2

```bash
ps aux --sort=-%cpu | head -10
```

Why: Identify the top CPU-consuming processes.

### Step 3

```bash
ps -fp <PID>
```

Why: Get detailed information about the process.

### Step 4

```bash
htop
```

Why: Visualize resource usage interactively.

### What I Learned

Identify the process causing the issue before attempting remediation.

---

## Scenario 3: Finding Service Logs

### Step 1

```bash
systemctl status docker
```

Why: Verify service health.

### Step 2

```bash
journalctl -u docker -n 50
```

Why: View recent Docker logs.

### Step 3

```bash
journalctl -u docker -f
```

Why: Monitor logs in real time.

### Step 4

```bash
journalctl -u docker --since "1 hour ago"
```

Why: Review recent activity during an incident window.

### What I Learned

Systemd-managed services store logs in journald and can be queried with journalctl.

---

## Scenario 4: File Permission Issue

### Step 1

```bash
ls -l /home/user/backup.sh
```

Why: Check current permissions.

### Step 2

```bash
chmod +x /home/user/backup.sh
```

Why: Add execute permission.

### Step 3

```bash
ls -l /home/user/backup.sh
```

Why: Verify execute permission was added.

### Step 4

```bash
./backup.sh
```

Why: Test script execution.

### What I Learned

Scripts require execute permission before they can run.

---

## Key Takeaways

* Linux files are organized into a predictable hierarchy.
* Logs are commonly found in `/var/log`.
* Configuration files are primarily stored in `/etc`.
* Troubleshooting should follow a structured, evidence-based approach.
* Understanding file locations speeds up incident resolution and debugging.

