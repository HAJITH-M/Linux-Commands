

# 📬 **Linux Mail Setup - making a copy of mail & Usage Guide (Postfix + Mailutils)**

---

## 1️⃣ Install Required Packages

Install **Postfix** and **GNU Mailutils**:

```bash
sudo apt update
sudo apt install postfix mailutils
```

During setup:

* Select **"Internet Site"**
* Set system mail name to `localhost` or your hostname.

To reconfigure later:

```bash
sudo dpkg-reconfigure postfix
```

---

## 2️⃣ Verify Postfix is Running

```bash
sudo systemctl status postfix
```

Start/enable if not active:

```bash
sudo systemctl start postfix
sudo systemctl enable postfix
```

---

## 3️⃣ Send a Local Email

```bash
echo "This is a test message" | mail -s "Test Subject" user1
```

Read your inbox:

```bash
mail
```

---

## 🧠 Internal Flow

| Action                   | Outcome                            |
| ------------------------ | ---------------------------------- |
| `mail` command run       | Sends to `postfix`                 |
| Postfix finds local user | Stores in `/var/mail/user1`       |
| `mail` command opens     | Displays message from mailbox file |

Check the mailbox directly:

```bash
cat /var/mail/user1
```

---

## 4️⃣ Create and Mail Another Local User

Create new user:

```bash
sudo adduser testuser
```

Send mail:

```bash
echo "Welcome testuser" | mail -s "Greetings" testuser
```

Login as them and check:

```bash
sudo su - testuser
mail
```

---

## 5️⃣ Fix: “No Mailbox” Error

If you see:

```
Cannot open mailbox /var/mail/user1: No such file or directory
```

Run:

```bash
sudo touch /var/mail/user1
sudo chown user1:mail /var/mail/user1
sudo chmod 660 /var/mail/user1
```

---

## 6️⃣ Send Mail to External Email

```bash
echo "Hello from Linux" | mail -s "External Test" yourname@gmail.com
```

Note: These won't appear in your `mail` inbox — they're outbound messages only.

---

## 7️⃣ Send Email with an Attachment

```bash
echo "Please find attached file" | mail -s "Attachment Test" -A ./readme.md user1
```

Make sure `readme.md` exists.

---

## 8️⃣ View Mail Logs

```bash
sudo tail -f /var/log/mail.log
```

Or:

```bash
journalctl -u postfix
```

---

## 9️⃣ Clear or Reset Mailbox

### Empty inbox:

```bash
sudo truncate -s 0 /var/mail/user1
```

### Delete & recreate:

```bash
sudo rm /var/mail/user1
sudo touch /var/mail/user1
sudo chown user1:mail /var/mail/user1
sudo chmod 660 /var/mail/user1
```

---

## 🔟 Raw Email via `sendmail`

```bash
(
  echo "To: yourname@gmail.com"
  echo "Subject: Sendmail Raw Test"
  echo
  echo "Message sent using sendmail"
) | sendmail -t
```

---

## ✅ Quick Commands Reference

| Purpose               | Command Example                                             |
| --------------------- | ----------------------------------------------------------- |
| Install mail tools    | `sudo apt install postfix mailutils`                        |
| Check postfix status  | `sudo systemctl status postfix`                             |
| Send local mail       | `echo "Hi" \| mail -s "Hi" user1`                          |
| Read local mail       | `mail`                                                      |
| Fix mailbox not found | `sudo touch /var/mail/user1 && sudo chown user1:mail ...` |
| Send external mail    | `mail -s "Hi" yourname@gmail.com`                           |
| Send with attachment  | `mail -s "Subj" -A file.txt user1`                         |
| Check logs            | `sudo tail -f /var/log/mail.log`                            |
| Use sendmail          | Block with `To:` and `Subject:` piped into `sendmail -t`    |

---

