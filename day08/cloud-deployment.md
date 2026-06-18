
# Day 08 - Cloud Server Setup: Docker, Nginx & Web Deployment

## Objective

Deploy a cloud server, install Docker and Nginx, configure web access, and collect application logs.

---

# Cloud Environment

* Cloud Provider: AWS EC2
* Operating System: Ubuntu 24.04 LTS
* Instance Type: t2.micro
* Access Method: SSH

---

# Commands Used

## Connect to Server

```bash
ssh -i devops-key.pem ubuntu@<public-ip>
```
<img width="743" height="68" alt="image" src="https://github.com/user-attachments/assets/8daae391-c4f1-4174-8ce0-c81919e95753" />

Successfully connected to the EC2 instance.

---

## Update Server

```bash
sudo apt update
sudo apt upgrade -y
```

Updated package repositories and installed latest security updates.

---

## Install Docker

```bash
sudo apt install docker.io -y

sudo systemctl enable docker
sudo systemctl start docker

sudo systemctl status docker
```

Verified Docker service is active and running.

---

## Install Nginx

```bash
sudo apt install nginx -y

sudo systemctl enable nginx
sudo systemctl start nginx

sudo systemctl status nginx
```

Verified Nginx service is active and listening on port 80.

---

## Verify Listening Ports

```bash
sudo ss -tulpn | grep nginx
```
<img width="1536" height="148" alt="image" src="https://github.com/user-attachments/assets/ce02de3e-6f3a-434d-bc2b-11d54e7e30ba" />

Confirmed Nginx is listening on HTTP port 80.

---

## Check Public Access

```bash
curl http://localhost
```

Received the default Nginx welcome page.

---

## Extract Nginx Logs

```bash
sudo tail -n 50 /var/log/nginx/access.log
```

Reviewed recent access requests.

---

## Save Logs

```bash
sudo cp /var/log/nginx/access.log ~/nginx-logs.txt
```

Saved logs for submission.

---

## Download Logs

```bash
scp -i devops-key.pem ubuntu@<public-ip>:~/nginx-logs.txt .
```

Downloaded log file to local machine.

---

# Security Group Configuration

| Type | Port |
| ---- | ---- |
| SSH  | 22   |
| HTTP | 80   |

Configured Security Group to allow SSH and web traffic.

---

# Challenges Faced

### Issue 1: Unable to Access Web Page

Cause:
HTTP port 80 was not allowed in Security Group.

Resolution:
Added inbound rule for HTTP (Port 80).

### Issue 2: SSH Connection Refused

Cause:
Incorrect key permissions.

Resolution:

```bash
chmod 400 devops-key.pem
```

SSH connection worked successfully.

---

# What I Learned

* How to launch and connect to an EC2 instance.
* How to install and manage services using systemctl.
* How Security Groups control traffic to cloud servers.
* How to collect and save logs from a Linux server.
* How Nginx serves web content on port 80.

---

# Screenshots Included

1. ssh-connection.png
2. nginx-webpage.png
3. docker-nginx.png

---

# Conclusion

Successfully deployed a cloud-based Ubuntu server, configured Docker and Nginx, enabled web access, and collected logs for troubleshooting and monitoring.
