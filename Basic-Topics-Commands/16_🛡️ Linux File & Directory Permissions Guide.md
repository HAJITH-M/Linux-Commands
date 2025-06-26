# 🛡️ Linux File & Directory Permissions Guide

This guide walks you through how Linux file and directory permissions work, how to set them, and how to troubleshoot common permission issues using `chmod`, `ls`, and file access control.

---

## 📁 File Permission Symbols & Explanation

```plaintext
drwxr-xr-x
| ||| |||
| ||| ||└── Others: Execute
| ||| |└─── Others: Read
| ||| └──── Group: Execute
| ||└────── Group: Read
| |└─────── User: Execute
| └──────── User: Write
└────────── User: Read
```

* `d` = directory
* `-` = regular file

---

## 🔧 Setting File Permissions

Use the `chmod` command to change file or directory permissions.

### 🔢 Numeric (Octal) Mode

Each number represents **User, Group, Others** respectively.

| Permission | Symbol | Value |
| ---------- | ------ | ----- |
| Read       | `r`    | 4     |
| Write      | `w`    | 2     |
| Execute    | `x`    | 1     |
| No Access  | `-`    | 0     |

### Examples:

```bash
chmod 777 file      # rwxrwxrwx
chmod 755 file      # rwxr-xr-x
chmod 644 file      # rw-r--r--
chmod 700 file      # rwx------
```

---

### ✍️ Symbolic Mode

* `u` = user (owner)
* `g` = group
* `o` = others
* `a` = all (user + group + others)

```bash
chmod g+w file     # Add write for group
chmod o-r file     # Remove read for others
chmod u=rw file    # Set user permission to read/write only
chmod a+x file     # Give execute permission to all
```

---

## 👥 Example: File Not Visible to Another User

### Scenario:

* You (as `user1`) created a file `data.txt`
* You ran:

  ```bash
  chmod 777 data.txt
  ```
* But the user `sha` **can’t see** the file from their account.

### ✅ Cause:

* The directory containing `data.txt` doesn't allow access to `sha`.

### ✅ Fix:

As `user1`, run:

```bash
chmod 755 /home/user1
```

Then, as user `sha`, run:

```bash
cd /home/user1
ls
```

Now `sha` can list and read `data.txt`.

---

## 📂 Setting Permissions for Directories

### Directory Permission Meaning:

| Permission | Meaning                               |
| ---------- | ------------------------------------- |
| `r`        | List directory contents (`ls`)        |
| `w`        | Create/Delete/Rename files in dir     |
| `x`        | Enter directory (`cd`) & access files |

### Examples:

```bash
chmod 755 myfolder   # Full access for owner, read+cd for others
chmod 700 myfolder   # Only owner can access
chmod 777 myfolder   # Everyone can read/write/enter
chmod g-w myfolder   # Remove write for group
```

### 📝 Note:

To `cd` into a directory, you **must have `x` (execute)** permission!

---

## 🧪 Example Session (with Replaced Users)

```bash
sha@user1-PC:~$ su - user1
Password:

user1@user1-PC:~$ chmod o+x .
user1@user1-PC:~$ chmod 755 .

user1@user1-PC:~$ su - sha
Password:

sha@user1-PC:~$ cd /home/user1
sha@user1-PC:~$ ls
data.txt
```

---

## 📝 Real-World Use Cases

| Use Case                         | Command            |
| -------------------------------- | ------------------ |
| Make folder private              | `chmod 700 folder` |
| Share folder read-only           | `chmod 755 folder` |
| Share folder read/write          | `chmod 777 folder` |
| Prevent others from seeing files | `chmod 750 folder` |

---

## ✅ Useful Commands Summary

```bash
ls -l            # Show file permissions
ls -ld dirname   # Show directory permissions
chmod 755 file   # Set permissions
chown user file  # Change file owner
chgrp group file # Change file group
```

---

## 📚 Advanced Options (Optional)

If you want to go beyond `chmod`:

* Use `umask` to set default permissions
* Use `setfacl` to assign specific permissions per user
* Use groups for shared file access

---

# 🔐 Linux Permission Mapping (Octal to Symbolic)

Each digit in a 3-digit octal number represents permissions for a specific category:

* **1st digit** → User (Owner)
* **2nd digit** → Group
* **3rd digit** → Others

---

## 📊 Example: `755` Permission Breakdown

| Digit | Who    | Binary | Symbolic | Meaning              |
| ----- | ------ | ------ | -------- | -------------------- |
| 7     | User   | 111    | `rwx`    | Read, Write, Execute |
| 5     | Group  | 101    | `r-x`    | Read, Execute        |
| 5     | Others | 101    | `r-x`    | Read, Execute        |

### 🔍 Meaning:

* **User** has full control (`rwx`)
* **Group** can read and execute
* **Others** can read and execute

---