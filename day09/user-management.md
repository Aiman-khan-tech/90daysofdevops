
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
<img width="626" height="502" alt="image" src="https://github.com/user-attachments/assets/11fea6ec-0afe-45b5-8331-f979c5c46b55" />

## Verification

```bash
grep -E "tokyo|berlin|professor|nairobi" /etc/passwd

ls -l /home
```
<img width="797" height="330" alt="image" src="https://github.com/user-attachments/assets/5fc7b846-7656-4c99-90e6-b826ce11f26a" />

Verified that user accounts and home directories were successfully created.

---

# Task 2: Group Creation

## Commands Used

```bash
sudo groupadd developers
sudo groupadd admins
sudo groupadd project-team
```
<img width="647" height="112" alt="image" src="https://github.com/user-attachments/assets/ee404689-8aa9-43c3-8b71-5266f9db30e8" />

## Verification

```bash
grep -E "developers|admins|project-team" /etc/group
```
<img width="866" height="140" alt="image" src="https://github.com/user-attachments/assets/e7c16f26-2027-4edd-bffa-0012c40a1bda" />

Confirmed all groups were created successfully.

---

# Task 3: Group Assignments

## Commands Used

```bash
sudo usermod -aG developers tokyo

sudo usermod -aG developers,admin berlin

sudo usermod -aG admins professor

sudo usermod -aG project-team tokyo

sudo usermod -aG project-team nairobi
```
<img width="781" height="175" alt="image" src="https://github.com/user-attachments/assets/8581872f-854f-4706-971b-f0f98fe1c8dd" />

## Verification

```bash
groups tokyo
groups berlin
groups professor
groups nairobi
```
<img width="802" height="192" alt="image" src="https://github.com/user-attachments/assets/63c3e63a-6613-4b38-ae56-ebd259566c27" />

### Group Membership

| User      | Groups                   |
| --------- | ------------------------ |
| tokyo     | developers, project-team |
| berlin    | developers, admin       |
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
<img width="703" height="112" alt="image" src="https://github.com/user-attachments/assets/f9cf6527-df2a-493d-82d2-cfe3952930a1" />

## Verification

```bash
ls -ld /opt/dev-project
```

Expected:

```text
drwxrwxr-x
```
<img width="758" height="77" alt="image" src="https://github.com/user-attachments/assets/0cd1809b-6d93-4a3b-970c-2fba4a86817f" />

### Testing Access

```bash
sudo -u tokyo touch /opt/dev-project/tokyo-file.txt

sudo -u berlin touch /opt/dev-project/berlin-file.txt
```
<img width="847" height="117" alt="image" src="https://github.com/user-attachments/assets/46ac3a9f-3da0-48b7-b474-0746d0693466" />

Verification:

```bash
ls -l /opt/dev-project
```
<img width="752" height="118" alt="image" src="https://github.com/user-attachments/assets/619b2f76-a7e8-49e3-bd93-5b9d4938798f" />

Both users successfully created files.

---

# Task 5: Team Workspace

## Commands Used

```bash
sudo mkdir -p /opt/team-workspace

sudo chgrp project-team /opt/team-workspace

sudo chmod 775 /opt/team-workspace
```
<img width="816" height="92" alt="image" src="https://github.com/user-attachments/assets/caac19d2-9692-4754-b930-a09dffbd3a38" />

## Verification

```bash
ls -ld /opt/team-workspace
```
<img width="770" height="73" alt="image" src="https://github.com/user-attachments/assets/cf9f77cb-afa7-4558-8f11-86a3feca57bb" />

### Testing Access

```bash
sudo -u nairobi touch /opt/team-workspace/nairobi-file.txt

ls -l /opt/team-workspace
```
<img width="981" height="166" alt="image" src="https://github.com/user-attachments/assets/1903b9bd-acda-4189-9cf2-54406d259d67" />

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
