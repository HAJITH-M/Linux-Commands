# 🔗SSH and SCP Connectivity and Usage

## Introduction

SSH (Secure Shell) and SCP (Secure Copy) are essential tools used to securely access and transfer files between systems over a network.

---

## SSH - Secure Shell

### 1. Installing SSH on Ubuntu

To use SSH, make sure `openssh-server` is installed:

```bash
sudo apt-get install openssh-server
```

### 2. Checking the IP Address

If `ifconfig` is not available:

```bash
sudo apt install net-tools
ifconfig
```

Look for a line like:

```
inet 172.27.101.131
```

This is your machine's IP address.

### 3. Connecting via SSH

From another system, connect using the IP address:

```bash
ssh username@IP
```

Or connect using the username and hostname:

```bash
hostname
# Output: your-hostname

ssh username@hostname
```

### 4. First-Time SSH Prompt

When connecting to a host for the first time, SSH will ask for confirmation:

```
The authenticity of host '172.20.124.218 (172.20.124.218)' can't be established.
ED25519 key fingerprint is SHA256:sDPJbiVzKQib20zUN+3HtLQ/ZtKfakQtSsJ5mawt/S4.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

* This is a security feature to prevent connecting to a spoofed system.
* Type `yes` to continue.
* Then you'll be prompted for the password:

```
*****
```

### 5. Add to Resume

> "Configured and used SSH for secure remote access and file transfer between Linux systems."

---

## Windows SSH Clients

For Windows users:

* **PuTTY** – SSH terminal client
* **WinSCP** – GUI tool for secure file transfer (SCP/SFTP)

---

## SCP - Secure Copy

### 1. Using SCP to Copy Files

To copy a file securely from one machine to another:

```bash
scp /home/username/Day-2/image/OIP.Kl3R1bXcD_yd6xpq9txudAHaEo\?r\=0\&rs\=1\&pid\=ImgDetMain\&cb\=idpwebpc2 \
username@hostname:/home/username/scpcopy/imagecopy
```

* Replace the source and destination paths as needed.
* This command copies the file to the remote system under the specified path.

### 2. For Other Systems

To copy to a friend's system:

```bash
scp <file> ubuntu@user1:/home/ubuntu/destination_path
```

* Replace `username@hostname` with the appropriate user and hostname or IP address.

---

## Summary

* Use **SSH** to connect securely to remote systems.
* Use **SCP** to transfer files securely over SSH.
* Tools like **PuTTY** and **WinSCP** make this easy on Windows.

---

Let me know if you want this saved to a file or if you need a `.pdf` or `.md` export!
