# 🧾 Grep – Pattern Matching and Related Tools

## 📂 Example Log File Content

`log1.txt`:

```
[INFO] Server started  
[DEBUG] Connection successful  
[ERROR] File not found  
[INFO] Job completed  
[WARNING] Low memory  
[ERROR] Timeout reached  
```

---

## 🔍 Grep – Basic Pattern Matching

### Case-Sensitive Match

```bash
grep ERROR log1.txt
```

Finds lines containing `ERROR`.

### Case-Insensitive Match

```bash
grep -i error log1.txt
```

Matches `error`, `Error`, `ERROR`, etc.

### Invert Match (Exclude Pattern)

```bash
grep -v ERROR log1.txt
```

Excludes lines with `ERROR`.

---

## 📁 Grep – Pattern Matching Across Files

### Search in Multiple Files

```bash
grep WARNING *.txt
```

Searches for `WARNING` in all `.txt` files.

### Recursive Directory Search

```bash
grep -r "Timeout" ~/logs
```

Searches all subdirectories under `~/logs`.

---

## 📡 Grep – Real-Time Log Monitoring

### Live Stream Matching Lines

```bash
grep WARNING *.txt | tail -f
```

Follows matching lines as files grow.

### View Last N Matched Lines

```bash
grep WARNING *.txt | tail -20
```

Displays the last 20 lines of grep output.

---

## 🔠 Grep – Regular Expression Anchors

### Match Lines Starting with a Specific Tag

```bash
grep "^\[ERROR\]" log1.txt
```

Matches lines beginning with `[ERROR]`.

---

## 🧠 Related – Process Monitoring with `ps` and `grep`

### Find a Running Python Script

```bash
ps -aux | grep data_processing.py
```

**Example Output:**

```
python3 data_processing.py
grep --color=auto data_processing.py
```

> Note: `grep` itself appears in results; this is normal.

### `ps` Flag Meanings

| Flag | Description                                  |
| ---- | -------------------------------------------- |
| `a`  | Show processes for all users                 |
| `u`  | Display process owners                       |
| `x`  | Include processes without a terminal session |

---

## 📁 Related – File and Directory Navigation

### Example File Tree

```bash
/home/ubuntu/logs
├── data.txt
├── job_20231201.log
├── job_20241201.log
└── test/
    └── list
```

### Useful Commands

```bash
cd logs         # Navigate to logs directory
pwd             # Print working directory
cd test         # Go into 'test' subdirectory
cat data.txt    # Display contents of data.txt
```

---

## ✅ Grep – Quick Option Reference

| Option     | Description                                     |
| ---------- | ----------------------------------------------- |
| `-i`       | Ignore case when matching                       |
| `-v`       | Invert match; exclude matching lines            |
| `-r`       | Recursively search in directories               |
| `-f`       | Follow new lines as they are added (via `tail`) |
| `^pattern` | Match lines beginning with a pattern            |

---

