# 📬 Postfix Configuration with Gmail Relay on Ubuntu

This guide helps you configure **Postfix** to send mail using **Gmail's SMTP** server on an Ubuntu system.

---

## 🧰 Prerequisites

* ✅ Ubuntu or Debian-based Linux system
* ✅ Gmail account (App Password required if 2FA is enabled)
* ✅ Terminal access with `sudo` privileges

---

## 📦 Step 1: Install Postfix and Required Packages

Run the following in your terminal:

```bash
sudo apt update
sudo apt install postfix mailutils libsasl2-2 ca-certificates libsasl2-modules
```

---

## 📥 Step 2: Postfix Initial Configuration

During the installation, you'll see interactive prompts. Select the following options:

### ➤ 1. Mail Configuration Type

Choose:

```
Internet with smarthost
```

### ➤ 2. System Mail Name

Enter your **domain name**, not your email address. For Gmail, you can use:

```
gmail.com
```

> ⚠️ **Do NOT enter your full email address like `you@gmail.com`**

### ➤ 3. SMTP Relay Host

Enter Gmail's SMTP server:

```
[smtp.gmail.com]:587
```

---

## 🔐 Step 3: Set Gmail Authentication Credentials

Create the file to store your Gmail login:

```bash
sudo nano /etc/postfix/sasl_passwd
```

Add the following line, replacing with your Gmail address and [App Password](https://myaccount.google.com/apppasswords):

```
[smtp.gmail.com]:587    your_email@gmail.com:your_app_password
```

### ➤ Secure the credentials:

```bash
sudo postmap /etc/postfix/sasl_passwd
sudo chown root:root /etc/postfix/sasl_passwd /etc/postfix/sasl_passwd.db
sudo chmod 600 /etc/postfix/sasl_passwd /etc/postfix/sasl_passwd.db
```

---

## ⚙️ Step 4: Configure `/etc/postfix/main.cf`

Edit the Postfix configuration:

```bash
sudo nano /etc/postfix/main.cf
```

Add or update the following settings:

```ini
# Basic mail settings
myhostname = your-hostname
myorigin = /etc/mailname
mydestination = $myhostname, localhost.$mydomain, localhost
relayhost = [smtp.gmail.com]:587

# TLS encryption settings
smtp_use_tls = yes
smtp_tls_security_level = encrypt
smtp_tls_note_starttls_offer = yes

# SASL authentication settings
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous

# Network and protocol settings
mynetworks = 127.0.0.0/8
inet_interfaces = all
inet_protocols = all
```

> 💡 Replace `your-hostname` with your system’s hostname. You can get it using `hostname` command.

---

## 🔄 Step 5: Restart Postfix

Apply your changes:

```bash
sudo systemctl restart postfix
```

---

## ✅ Step 6: Send a Test Email

Use the `mail` command to test:

```bash
echo "This is a test email from Postfix via Gmail" | mail -s "Postfix Test" your_email@gmail.com
```

---

## 📋 Step 7: Verify Mail Delivery

Check the logs:

```bash
sudo tail -f /var/log/mail.log
```

Look for `status=sent` — this confirms successful delivery.

---

## 🛠️ Troubleshooting

### ❌ Error: `bad string length 0 < 1: mydomain=`

* **Cause:** You may have left `mydomain` or `myhostname` blank or misconfigured.
* **Fix:** Ensure your `/etc/postfix/main.cf` has:

  ```ini
  myhostname = your-hostname
  ```

  Do **not** set it to an email address.

---

## ✅ Final Summary

| Step | Action                                                                |
| ---- | --------------------------------------------------------------------- |
| 1    | Install Postfix and dependencies                                      |
| 2    | Select `Internet with smarthost`, set `gmail.com` as system mail name |
| 3    | Set relay host to `[smtp.gmail.com]:587`                              |
| 4    | Create `/etc/postfix/sasl_passwd` with Gmail credentials              |
| 5    | Update `/etc/postfix/main.cf` configuration                           |
| 6    | Restart Postfix and send a test email                                 |
| 7    | Check `/var/log/mail.log` for success confirmation                    |

---

Would you like this exported as a **PDF**, **Markdown**, or **Word document**?
