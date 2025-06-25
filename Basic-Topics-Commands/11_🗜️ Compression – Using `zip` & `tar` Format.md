## 🗜️ Compression – Using `zip` Format

---

### 📦 Create Zip Archives

* **`zip zippingfilename.zip originaldir/`**
  Compresses the specified directory or files into a `.zip` file.

```bash
zip mybackup.zip myfolder/
```

* **`zip -r zippingfilename.zip originaldir/`**
  Compresses **recursively**, including all nested subdirectories and files.

```bash
zip -r fullbackup.zip myproject/
```

🔹 **`-r`** → Recursively zip subfolders and their contents.

---

### 📂 Extract Zip Archives

* **`unzip zippedfilename.zip`**
  Unzips/extracts the contents of a `.zip` archive into the current directory.

```bash
unzip fullbackup.zip
```

---

## 📦 Compression – Using `.tar` Format (No Compression)

---

### 🧵 Create a `.tar` Archive (Uncompressed)

* **`tar -cvf archive.tar folder/`**
  Archives a folder into a `.tar` file **without compression**.

```bash
tar -cvf sample.tar day-2/
```

🔹 Option Breakdown:

* `c` → Create archive
* `v` → Verbose (shows files being added)
* `f` → Specify archive filename

---

### 📂 Extract a `.tar` Archive (Uncompressed)

* **`tar -xvf archive.tar`**
  Extracts the contents of a `.tar` archive.

```bash
tar -xvf sample.tar
```

🔹 Option Breakdown:

* `x` → Extract files
* `v` → Verbose (shows extraction progress)
* `f` → Specify archive filename

---

