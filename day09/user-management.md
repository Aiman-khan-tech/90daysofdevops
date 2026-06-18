
# Day 09 - Linux User & Group Management Challenge

## Objective

Practice Linux user, group, and permission management by creating users, assigning groups, and configuring shared workspaces.

---

# Users & Groups Created

## Users

* tokyo
* berlin
* professor
* nairobi

## Groups

* developers
* admins
* project-team

---

# Task 1: User Creation

## Commands Used

```bash
sudo useradd -m tokyo
sudo passwd tokyo

sudo useradd -m berlin
sudo passwd berlin

sudo useradd -m professor
sudo passwd professor

sudo useradd -m nairobi
sudo passwd nairobi
```

## Verification

```bash
grep -E "tokyo|berlin|professor|nairobi" /etc/passwd

ls -l /home
```

Verified that user accounts and home directories were successfully created.

---

# Task 2: Group Creation

## Commands Used

```bash
sudo groupadd developers
sudo groupadd admins
sudo groupadd project-team
```

## Verification

```bash
grep -E "developers|admins|project-team" /etc/group
```

Confirmed all groups were created successfully.

---

# Task 3: Group Assignments

## Commands Used

```bash
sudo usermod -aG developers tokyo

sudo usermod -aG developers,admins berlin

sudo usermod -aG admins professor

sudo usermod -aG project-team tokyo
sudo usermod -aG project-team nairobi
```

## Verification

```bash
groups tokyo
groups berlin
groups professor
groups nairobi
```

### Group Membership

| User      | Groups                   |
| --------- | ------------------------ |
| tokyo     | developers, project-team |
| berlin    | developers, admins       |
| professor | admins                   |
| nairobi   | project-team             |

---

# Task 4: Shared Developer Directory

## Commands Used

```bash
sudo mkdir -p /opt/dev-project

sudo chgrp developers /opt/dev-project

sudo chmod 775 /opt/dev-project
```

## Verification

```bash
ls -ld /opt/dev-project
```

Expected:

```text
drwxrwxr-x
```

### Testing Access

```bash
sudo -u tokyo touch /opt/dev-project/tokyo-file.txt

sudo -u berlin touch /opt/dev-project/berlin-file.txt
```

Verification:

```bash
ls -l /opt/dev-project
```

Both users successfully created files.

---

# Task 5: Team Workspace

## Commands Used

```bash
sudo mkdir -p /opt/team-workspace

sudo chgrp project-team /opt/team-workspace

sudo chmod 775 /opt/team-workspace
```

## Verification

```bash
ls -ld /opt/team-workspace
```

### Testing Access

```bash
sudo -u nairobi touch /opt/team-workspace/nairobi-file.txt

ls -l /opt/team-workspace
```

Verified group-based collaboration workspace functionality.

---

# Commands Summary

```bash
useradd
passwd
groupadd
usermod
groups
chgrp
chmod
mkdir
touch
ls
grep
```

---

# What I Learned

* Linux groups simplify access management for teams.
* Shared directories become easier to manage using group ownership.
* The combination of users, groups, and permissions forms the foundation of Linux security.
* Proper permission management reduces operational risk and improves collaboration.
* Group-based access control scales much better than assigning permissions user by user.

---

# Conclusion

Successfully created users, groups, shared directories, and validated access through real-world permission management scenarios commonly used in production Linux environments.
