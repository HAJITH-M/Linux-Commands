## 🔗 Hard Links & Soft Links in Linux

---
### 📁 What is a Link in Linux?

In Linux, a **link** allows multiple references (names) to point to the same data on disk. There are two primary types:

1. **Hard Link** – Directly links to the file’s **inode**.
2. **Soft Link (Symbolic Link)** – Links to the file’s **path** (acts like a shortcut).

---

## 🔒 Hard Link

### 📘 Definition

A **hard link** creates another **filename** that directly refers to the same inode (storage) as the original file.

### ✅ Characteristics

| Feature                  | Hard Link                   |
| ------------------------ | --------------------------- |
| Points to                | File **inode**              |
| File content shared      | ✅ Yes                       |
| If original is deleted   | ❌ File **still exists**     |
| Works across filesystems | ❌ No                        |
| Can link to directories  | ❌ No (typically restricted) |
| Inode number             | ✅ Same                      |

### 🔧 How to Create

```bash
ln original.txt hardlink.txt
```

### 🔬 Example

```bash
echo "Hello Hard Link" > file1.txt
ln file1.txt file1_hard.txt
ls -li file1.txt file1_hard.txt
```

Both files will show the **same inode number**, confirming they're hard-linked.

### 💡 Note

Changes made to either file are reflected in both — since they reference the same underlying data.

---

## 🧷 Soft Link (Symbolic Link)

### 📘 Definition

A **soft link** (or symbolic link) is a file that contains a **path** to another file or directory.

### ✅ Characteristics

| Feature                  | Soft Link                 |
| ------------------------ | ------------------------- |
| Points to                | File **path** (not inode) |
| File content shared      | ✅ Yes (via reference)     |
| If original is deleted   | ❌ Link breaks (dangling)  |
| Works across filesystems | ✅ Yes                     |
| Can link to directories  | ✅ Yes                     |
| Inode number             | ❌ Different               |

### 🔧 How to Create

```bash
ln -s /path/to/original.txt symlink.txt
```

Use **absolute paths** to avoid broken links from directory changes.

### 🔬 Example

```bash
echo "Hello Soft Link" > original.txt
ln -s original.txt softlink.txt
cat softlink.txt
```

Then delete the original:

```bash
rm original.txt
cat softlink.txt
```

You’ll see:

```
cat: softlink.txt: No such file or directory
```

Because the **symlink is now dangling**.

---

## 🧪 Inode Comparison

```bash
ls -li original.txt hardlink.txt softlink.txt
```

* `original.txt` and `hardlink.txt` → Same **inode**.
* `softlink.txt` → Different inode, shows `-> original.txt`.

---

## 🚫 Cross-Filesystem Limitation (Hard Links)

Hard links **cannot span across different filesystems**:

```bash
ln /mnt/drive1/file.txt /mnt/drive2/hardlink.txt
```

This returns:

```
ln: failed to create hard link: Invalid cross-device link
```

✅ Instead, use a soft link:

```bash
ln -s /mnt/drive1/file.txt /mnt/drive2/symlink.txt
```

---

## 🧭 Summary: Hard Link vs Soft Link

| Feature                  | Hard Link         | Soft Link           |
| ------------------------ | ----------------- | ------------------- |
| Type                     | Direct inode      | Path reference      |
| Cross-filesystem support | ❌ No              | ✅ Yes               |
| Target deletion effect   | ❌ Still works     | ✅ Becomes broken    |
| Inode number             | Same as original  | Different           |
| Can link to directories  | ❌ No              | ✅ Yes               |
| Typical use              | Low-level backups | Shortcuts, symlinks |

---
