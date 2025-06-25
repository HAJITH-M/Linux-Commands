## 🌐 Download & Disk Usage Commands

---

### 🔽 `wget` – Download Files from the Internet

```bash
wget <URL>
```

* Downloads a file from the specified URL.
* Supports HTTP, HTTPS, and FTP.
* Example:

```bash
wget https://example.com/sample.txt
```

---

### 💽 `du` – Disk Usage

* **`du -h` , `df -h`** – Displays **disk usage in human-readable format** (KB, MB, GB).

```bash
du -h 
```
```bash
df -h
```

* **`du -sh`** – Displays the **total size** of the current directory or specified folder, **summarized and human-readable**.

```bash
du -sh .
du -sh myfolder/
```

---

## 🧠 RAM Usage & Cache Management

---

### 📊 View RAM Usage

#### 🔹 `free -m` – Show memory usage in **megabytes**

```bash
free -m
```

Displays the amount of used, free, and available memory in MB.

#### 🔹 `free -g` – Show memory usage in **gigabytes**

```bash
free -g
```

Displays the same info as above, but in GB for easier reading on systems with more RAM.

📌 Output includes:

* **total** – Total installed memory
* **used** – Memory in use
* **free** – Completely unused memory
* **available** – Estimated available memory (including buffers/cache)

---

### 🧹 Clear Cached Memory (Drop Cache)

#### 🔹 Free up page cache, dentries, and inodes (⚠️ Use with caution)

```bash
sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"
```

✅ What it does:

* `sync` writes all pending disk writes to storage (flushes disk buffers)
* `echo 3 > ...drop_caches` clears:

  * PageCache (`1`)
  * Dentries and inodes (`2`)
  * Setting `3` clears **all three types**

⚠️ **Warning**: This doesn't affect running programs but may temporarily slow performance as caches are rebuilt.

---

