# Linux `find` Command Cheatsheet

This document outlines various `find` commands useful for searching files in a Linux system.

---

## 📁 Basic Usage

* `find . -name readme.md`
  Searches for a file named `readme.md` in the current directory and its subdirectories.

* `find . -name "*.txt" -ls`
  Lists all `.txt` files from the current directory and all subdirectories, along with file details.

* `find . -maxdepth 1 -name "*.txt"`
  Searches for `.txt` files **only** in the current directory (not subdirectories).

---

## ⚙️ Advanced Filters

* `find . -type f -size +10M`
  Displays files **larger than 10MB**.

* `find . -mtime -1`
  Shows files **modified within the last 24 hours**.

---

## 🧪 Special Cases

* `find . -empty`
  Shows **empty files and directories** in the current directory and subdirectories.

* `find . -type f -empty`
  Shows **only empty files**.

* `find . -name "*.tmp" -delete`
  Deletes all files ending with `.tmp`.
  ⚠️ **Use with caution!**

---

## 💡 Examples

* `find . -name "*.log" -type f -size +1M`
  Searches for `.log` files larger than **1MB**.

* `find . -name "*.txt" -ls`
  Lists details (like size and permissions) of all `.txt` files.

---

## 📝 Notes

* These commands operate at the **file system level**.
* Always **double-check paths and patterns**, especially when using `-delete`, to avoid accidental data loss.
