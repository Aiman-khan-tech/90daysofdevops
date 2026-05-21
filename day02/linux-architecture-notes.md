# Day 02 — Linux Architecture, Processes & systemd

> Building strong Linux fundamentals for DevOps, Cloud, and Platform Engineering.

---

## 📌 Overview

Linux powers the majority of modern infrastructure across:

* Cloud platforms
* Kubernetes clusters
* CI/CD pipelines
* Container runtimes
* Production servers

For a DevOps Engineer, understanding Linux internals is essential for:

* troubleshooting systems
* debugging deployments
* managing infrastructure
* optimizing performance
* automating operations

Day 02 focused on understanding:

* Linux Architecture
* Linux Processes
* Process Monitoring
* systemd Service Management

---

# 🏗️ Linux Architecture

Linux follows a layered architecture model where each layer has a dedicated responsibility.

```text
+----------------------+
|   User Applications  |
+----------------------+
|        Shell         |
+----------------------+
|   System Libraries   |
+----------------------+
|        Kernel        |
+----------------------+
|       Hardware       |
+----------------------+
```

---

## 🔹 Linux Kernel

The **Kernel** is the core component of the Linux operating system.

It acts as a bridge between:

* Hardware
* User applications

### Responsibilities of the Kernel

* Process Management
* Memory Management
* Device Management
* File System Management
* Networking
* Security & Permissions

The kernel manages system resources efficiently and enables communication between software and hardware.

---

## 🔹 User Space

User Space is where applications and user processes execute.

### Examples

* Bash
* VS Code
* Docker CLI
* Python Applications
* Git
* Nginx

Applications in user space cannot directly access hardware.
They interact with hardware through the Linux kernel.

---

## 🔹 Linux Shell

The shell acts as a command-line interface between the user and the operating system.

### Common Linux Shells

* Bash
* Zsh
* Fish

The shell interprets commands and forwards them to the kernel for execution.

---

# ⚙️ Linux Processes

A process is a running instance of a program.

### Examples of Linux Processes

* `ssh`
* `nginx`
* `docker`
* `systemd`

Every process has:

* Process ID (PID)
* Parent Process
* CPU Usage
* Memory Allocation
* Execution State

---

## 🔄 Process Lifecycle

Processes move through different states during execution.

```text
New → Running → Waiting → Stopped → Terminated
```

Understanding process behavior is important for troubleshooting and system monitoring.

---

# 🛠️ Process Management Commands

## Display Running Processes

```bash
ps aux
```

---

## Real-Time Process Monitoring

```bash
top
```

---

## Display Process Tree

```bash
pstree
```

---

## Display Current User

```bash
whoami
```

---

## Display Current Working Directory

```bash
pwd
```

---

# 🔧 Understanding systemd

`systemd` is the modern initialization and service management system used by most Linux distributions.

It is usually the first process started during boot and typically runs as:

```text
PID 1
```

---

## Responsibilities of systemd

* Boot Process Management
* Service Initialization
* Background Service Handling
* Dependency Management
* Logging
* System State Management

systemd plays a critical role in managing production Linux environments.

---

# 🖥️ systemctl Commands

## Check Service Status

```bash
systemctl status ssh
```

---

## Start a Service

```bash
sudo systemctl start nginx
```

---

## Stop a Service

```bash
sudo systemctl stop nginx
```

---

## Restart a Service

```bash
sudo systemctl restart nginx
```

---

## Enable Service at Boot

```bash
sudo systemctl enable nginx
```

---

# 🚀 Why Linux Fundamentals Matter in DevOps

Modern DevOps ecosystems rely heavily on Linux infrastructure.

Strong Linux knowledge helps engineers:

* troubleshoot production systems
* automate infrastructure
* manage containers
* understand Kubernetes internals
* optimize cloud workloads
* debug real-world incidents

Linux is one of the most critical foundational skills for DevOps Engineers.

---

# ✅ Practical Tasks Performed

During Day 02, I:

* Explored Linux architecture concepts
* Practiced process monitoring commands
* Understood Linux process lifecycle
* Learned the role of `systemd`
* Executed basic troubleshooting commands
* Worked within a WSL Ubuntu environment

---

# 📚 Key Takeaways

* Linux follows a layered architecture model
* The kernel manages system resources and hardware communication
* Processes are fundamental execution units in Linux
* `systemd` manages services and system initialization
* Process management is essential for troubleshooting Linux systems
* Linux fundamentals are critical for DevOps and Cloud Engineering

---

# 📖 Learning Outcome

Day 02 strengthened my understanding of Linux internals, process management, and service handling — foundational concepts that are essential for modern DevOps engineering and production infrastructure management.
