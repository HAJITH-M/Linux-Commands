## 📈 Running Scripts in Background and Monitoring with `nohup`

---

### 🧪 Example Python Script (`data_processing.py`)

```python
import time

a = 0
b = 5
while True:
    a = a + b
    print(f"updated value a: {a}", flush=True)
    time.sleep(3)
```

> 📝 **Note:** `flush=True` ensures output is written immediately to the log file.

---

### 🚀 Running the Script in Background

```bash
nohup python3 -u data_processing.py >> data_process.log &
```

* `nohup`: Prevents termination when terminal closes.
* `python3 -u`: Runs Python in unbuffered mode (prints appear immediately).
* `>> data_process.log`: Appends output to the log file.
* `&`: Runs the command in the background.

---

### 🔎 Monitoring the Process

#### View system activity:

```bash
top
```

> Use `top` to monitor CPU, memory, and active processes.

#### List all processes:

```bash
ps
ps -aux
```

#### Filter specific script:

```bash
ps -aux | grep data_processing.py
```

This shows the PID (Process ID) of your script for further action.

---

### 📄 Monitoring the Log Output

#### View log file contents:

```bash
cat data_process.log
```

#### Live log stream (updates in real time):

```bash
tail -f data_process.log
```

#### View last 10 lines of the log:

```bash
tail -10 data_process.log
```

---

### 🛑 Stopping the Script

Find the PID using:

```bash
ps -aux | grep data_processing.py
```

Example output:

```
hajith   12345  0.0  ... python3 data_processing.py
```

Then stop the process:

```bash
kill 12345
```

Or force kill if it doesn't stop:

```bash
kill -9 12345
```

---
