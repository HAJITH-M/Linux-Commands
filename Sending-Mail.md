# 📬 Postfix Gmail SMTP Relay Setup on Ubuntu

Set up Postfix on Ubuntu to relay outgoing mail via Gmail’s SMTP servers. This guide includes installation, configuration, secure credential handling, testing, and sending attachments.

---

## 🧰 Prerequisites

* ✅ Ubuntu or Debian-based system
* ✅ A Gmail account (App Password required if 2FA is enabled)
* ✅ sudo/root access
* ✅ Internet connection

---

## 📦 1. Install Postfix and Required Packages

Run:

```bash
sudo apt update
sudo apt install postfix mailutils libsasl2-2 ca-certificates libsasl2-modules
```

---

## ⚙️ 2. Postfix Setup Prompts

During installation, you'll be prompted with configuration options:

### ➤ Mail Configuration Type

Select:

```
Internet with smarthost
```

### ➤ System Mail Name

Enter:

```
gmail.com
```

> ⚠️ **Do NOT enter your full Gmail address (e.g., `your_email@gmail.com`)**

---

## 🔐 3. Configure Gmail Authentication

### ➤ Create the Password File

```bash
sudo nano /etc/postfix/sasl_passwd
```

Add:

```
[smtp.gmail.com]:587    your_email@gmail.com:your_app_password
```

> Replace with your Gmail address and App Password from: [https://myaccount.google.com/apppasswords](https://myaccount.google.com/apppasswords)

### ➤ Secure and Compile the Password File

```bash
sudo postmap /etc/postfix/sasl_passwd
sudo chown root:root /etc/postfix/sasl_passwd /etc/postfix/sasl_passwd.db
sudo chmod 600 /etc/postfix/sasl_passwd /etc/postfix/sasl_passwd.db
```

---

## 🛠️ 4. Configure Postfix Main Settings

Open the config file:

```bash
sudo nano /etc/postfix/main.cf
```

Add or verify the following:

```ini
# Basic settings
myhostname = your-hostname
myorigin = /etc/mailname
mydestination = $myhostname, localhost.$mydomain, localhost
relayhost = [smtp.gmail.com]:587

# TLS configuration
smtp_use_tls = yes
smtp_tls_security_level = encrypt
smtp_tls_note_starttls_offer = yes

# SASL auth settings
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous

# Network
mynetworks = 127.0.0.0/8
inet_interfaces = all
inet_protocols = all
```

> 💡 Replace `your-hostname` with the output of `hostname`.

---

## 🔁 5. Enable and Restart Postfix

Enable Postfix at boot:

```bash
sudo systemctl enable postfix
```

Restart the service:

```bash
sudo systemctl restart postfix
```

---

## ✉️ 6. Send a Test Email

```bash
echo "This is a test email from Postfix via Gmail" | mail -s "Postfix Test" your_email@gmail.com
```

---

## 📎 7. Send a File as Email Attachment

### ✅ Ensure `mailutils` is installed:

```bash
sudo apt install mailutils
```

### ➤ Send with one attachment:

```bash
echo "Please find the attached file." | mail -s "Report" -A /path/to/file.pdf your_email@gmail.com
```

### ➤ Send with multiple attachments:

```bash
mail -s "Monthly Report" -A file1.pdf -A file2.xlsx your_email@gmail.com
```

---

## 📋 8. Check Mail Logs

```bash
sudo tail -f /var/log/mail.log
```

Look for `status=sent` to confirm delivery.

---

## 🧯 9. Troubleshooting

### ❌ Error: `bad string length 0 < 1: mydomain=`

* **Cause:** Invalid `mydomain` or `myhostname` setting
* **Fix:** Ensure you have a valid line like:

  ```ini
  myhostname = your-hostname
  ```

### ❌ Cannot authenticate with Gmail

* **Fix:**

  * Use **App Passwords** if 2FA is enabled
  * Ensure the `sasl_passwd` file has correct formatting
  * Regenerate the `.db` with `postmap`

---

## ✅ Quick Summary

| Step | Task                                                   |
| ---- | ------------------------------------------------------ |
| 1    | Install Postfix and dependencies                       |
| 2    | Select `Internet with smarthost` and enter `gmail.com` |
| 3    | Set SMTP relay to `[smtp.gmail.com]:587`               |
| 4    | Store Gmail credentials securely                       |
| 5    | Configure `/etc/postfix/main.cf`                       |
| 6    | Enable and restart Postfix                             |
| 7    | Send test email with or without attachments            |
| 8    | Use logs to debug any issues                           |

---


