# Linux Troubleshooting Runbook

## Day 05 – CPU, Memory, and Logs Troubleshooting Drill

### Target Service

**SSH Service (ssh)**

---

## Environment Information

### 1. Check Kernel Information

```bash
uname -a
```

<img width="1034" height="59" alt="image" src="https://github.com/user-attachments/assets/5889c5ee-9c36-4f64-8b27-83730ed513a2" />

**Observation:**
Verified Linux kernel version and system architecture.

### 2. Check OS Information

```bash
cat /etc/os-release
```

<img width="983" height="275" alt="image" src="https://github.com/user-attachments/assets/214abf37-6193-4240-b492-af15b30d5a4c" />

**Observation:**
Confirmed Ubuntu distribution details and version.

---

## Filesystem Sanity Checks

### 3. Create Test Directory

```bash
mkdir /tmp/runbook-demo
```

<img width="883" height="67" alt="image" src="https://github.com/user-attachments/assets/0abc01f0-d144-4b43-b293-53efd60024d9" />

**Observation:**
Temporary directory created successfully.

### 4. Copy and Verify File

```bash
cp /etc/hosts /tmp/runbook-demo/hosts-copy
ls -l /tmp/runbook-demo
```

<img width="943" height="87" alt="image" src="https://github.com/user-attachments/assets/06bad702-a935-4210-a6bb-3e6179a8ed6e" />

**Observation:**
File copied successfully and permissions verified.

---

## CPU & Memory Snapshot

### 5. Monitor Running Processes

```bash
top
```

<img width="1044" height="476" alt="image" src="https://github.com/user-attachments/assets/b5b5d77c-de2f-448e-a09b-d2f110fd45cc" />

**Observation:**
System load was low with no abnormal CPU consumption.

### 6. Check Memory Usage

```bash
free -h
```

<img width="763" height="73" alt="image" src="https://github.com/user-attachments/assets/1506d44a-7d18-4c23-8dda-6f79468ec878" />

**Observation:**
Memory utilization was within normal limits and swap usage was minimal.

---

## Disk & IO Snapshot

### 7. Check Disk Usage

```bash
df -h
```

<img width="884" height="288" alt="image" src="https://github.com/user-attachments/assets/c354bb04-204d-4151-80ce-7fbf31ae7aa4" />

**Observation:**
All mounted filesystems had sufficient free space.

### 8. Check Log Directory Size

```bash
du -sh /var/log
```

<img width="590" height="65" alt="image" src="https://github.com/user-attachments/assets/a6996deb-ec08-49e7-a332-9f8969ee9041" />

**Observation:**
Log directory size was reasonable and not consuming excessive disk space.

---

## Network Snapshot

### 9. Check Listening Ports

```bash
ss -tulpn
```

<img width="1623" height="219" alt="image" src="https://github.com/user-attachments/assets/2190e41f-a6dc-4b74-bfa7-fbc288f4154a" />

**Observation:**
SSH service was listening on the expected port.

### 10. Verify Network Connectivity

```bash
curl -I https://www.google.com
```

<img width="1634" height="341" alt="image" src="https://github.com/user-attachments/assets/d53a543b-699e-4ccf-bef0-67b9232f081f" />

**Observation:**
Received HTTP response headers successfully, confirming internet connectivity.
Received HTTP/2 200 OK.
Confirmed outbound internet connectivity.
DNS resolution and HTTPS communication functioning normally

---

## Log Review

### 11. Review SSH Logs

```bash
journalctl -u ssh -n 50
```

<img width="1582" height="142" alt="image" src="https://github.com/user-attachments/assets/6aaa7245-9291-4b1d-8236-2c272133254d" />

**Observation:**
No recent errors or failed service events were observed.

### 12. Review System Logs

```bash
tail -n 50 /var/log/syslog
```

**Observation:**
System logs showed normal background activity without critical warnings.

---

## Quick Findings

* SSH service was running normally.
* CPU and memory utilization were healthy.
* Disk space was sufficient.
* Network connectivity was functioning correctly.
* No critical errors were found in service or system logs.

---

## If This Worsens (Next Steps)

### 1. Restart Service

```bash
sudo systemctl restart ssh
```

If the service becomes unresponsive, perform a controlled restart.

### 2. Increase Log Investigation

```bash
journalctl -u ssh -f
```

<img width="1601" height="232" alt="image" src="https://github.com/user-attachments/assets/893e5b49-79cf-4608-bf8d-890258e3f4d9" />

Monitor logs in real time to capture new errors.

### 3. Collect Additional Diagnostics

```bash
ps aux | grep ssh
vmstat 1
```

<img width="1428" height="314" alt="image" src="https://github.com/user-attachments/assets/4dce62d7-a7c6-490c-b200-b447d3466f3f" />

Gather process and performance metrics for deeper analysis before escalation.

---

## Learning Outcome

This troubleshooting drill helped reinforce a structured approach to investigating Linux services by checking system health, reviewing logs, validating network connectivity, and documenting findings before taking corrective action.
