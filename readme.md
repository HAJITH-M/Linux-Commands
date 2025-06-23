### Linux Commands and Their Purpose

* **`pwd`** – Prints the **current working directory**.
  Used to display the absolute path of the directory you're currently working in.

* **`uname`** – Displays the **name of the operating system**.
  Useful for identifying the OS (e.g., Linux, Darwin).

* **`uname -a`** – Displays **all available system information**, including kernel name, node name, kernel release, version, machine, processor, and OS.
  Helpful for getting a full snapshot of system details.

* **`whoami`** – Displays the **current logged-in user's username**.
  Useful for verifying which user account is being used in the terminal.

* **`clear`** – **Clears the terminal screen**.
  Used to remove all previous output from view and provide a clean workspace in the terminal.

* **`history`** – Shows the **list of previously executed commands** in the terminal.
  Useful for reviewing or reusing past commands.

* **`mkdir <foldername>`** – **Creates a new directory** with the specified name.
  Used to make a new folder in the current location.

* **`cd <dirname>`** – **Changes the current directory** to the specified one.
  Used for navigating into another directory.

* **`vi <filename>`** – Opens the **`vi` text editor** to create or edit a file.
  A powerful command-line text editor commonly used in Linux.

  * **`i`** – Switches to **insert mode** to start typing.
  * **`Esc`** – Returns to **command mode** to execute commands.
  * **`:w`** – **Saves** the file.
  * **`:wq!`** – **Saves and forcefully exits**, overriding warnings or permissions.
  * **`:q!`** – **Exits without saving** changes.
  * **`dd`** – **Deletes the current line**.

* **`nano <filename>`** – Opens the **`nano` text editor** to create or edit a file.
  A simpler, beginner-friendly editor with on-screen shortcuts for saving (`Ctrl + O`), exiting (`Ctrl + X`), and more.

* **`touch <filename>`** – **Creates an empty file** with the given name.
  Also updates the **timestamp** of an existing file without modifying its content.

* **`rm <filename>`** – **Deletes a file** permanently.
  Use with caution, as deleted files cannot be easily recovered.

---

### 📂 LS Commands to Know

* **`ls`** – Lists **all files and directories** in the current directory.

* **`ls *`** – Lists **all files and folders recursively** that match the wildcard `*`.

* **`ls filename*`** – Lists all files that **start with "filename"**.

* **`ls *filename`** – Lists all files that **end with "filename"**.

* **`ls -a`** – Lists all files, including hidden files (those starting with a dot .).
              - Useful for revealing files like .bashrc, .gitignore, or .env.

* **`ls -ld <dirname>`** – Shows **detailed info** about a directory without listing its contents.

* **`ls -d <dirname>`** – Shows only the **directory name**, not its contents.

* **`ls -ld <dirname*>`** – Detailed listing for all directories that **start with "dirname"**.

* **`ls -ld *`** – Detailed listing for all directories that **start with "dirname"**.

* **`ls -d <dirname*>`** – Lists only the **names** of directories that **start with "dirname"**.

* **`ls -lstr`** – Lists files in **long format**, showing **block size**, sorted by **modification time**, in **reverse order** (oldest first).
                 - A powerful combination to see file details and sort by time.

  * `-l` → Long listing format
  * `-s` → Show file size in blocks
  * `-t` → Sort by last modified time
  * `-r` → Reverse the sort order

---


### 🧹 Remove Commands to Know

* **`rm <filename>`** – Removes the specified file.

* **`rm *`** – Removes all the files in the current directory (fails if it includes directories).

* **`rm filename*`** – Removes all files starting with "filename".

* **`rm *filename`** – Removes all files ending with "filename".

* **`rm -r <dirname>`** – Recursively deletes the specified directory and all its contents (use with caution!).

* **`rm -rf dirname*`** – Forcibly and recursively removes all directories starting with "dirname" without prompting (⚠️ dangerous).

* **`rm -i filename*`** – Interactively asks for confirmation before deleting each file that starts with "filename".

* **`rmdir <dirname>`** – Removes an **empty directory** (fails if not empty).

* **`rmdir dirname*`** – Removes all **empty directories** that start with "dirname".

* **`rm -v filename*`** – Deletes matching files and **shows what’s being deleted** (verbose mode).

---

### 📄 Commands – View, Copy, Rename/Move

* **`cat <filename>`** – Displays the **contents of a file** directly in the terminal.
  Useful for quickly reading file data.

  **Examples using paths:**

  ```bash
  cat ~/Documents/notes.txt
  ```

  – Displays content from a file in the user's `Documents` folder.

  ```bash
  cat /var/log/syslog
  ```

  – Reads a system log file using an **absolute path**.

  ```bash
  cat ../report.txt
  ```

  – Displays a file from the **parent directory**.

* **`cp <oldfilename> <newfilename>`** – Copies a file from source to destination.
  Used when you want to **duplicate** a file in the same or different directory.

* **`mv <oldfilename> <newfilename>`** – Renames or moves a file from source to destination.
  Acts as a **rename** if both files are in the same directory, or a **move** otherwise.

* **Copying using `cat` command:**
  **`cat <oldfilename> >> <newfilename>`** – Appends the content of `oldfilename` to `newfilename`.
  Can also be used for **manual file merging**.

  **Example with paths:**

  ```bash
  cat ~/notes/part1.txt >> ~/notes/complete.txt
  ```

  – Appends the contents of `part1.txt` into `complete.txt` in the `~/notes/` directory.

---

### 📁 File Copy, Move, and Rename – With Paths (Including `~` Home Shortcut)

* **Using `~` to represent the user's home directory:**

  ```bash
  cp ~/Downloads/file.txt ~/Documents/
  ```

  This copies `file.txt` from the `Downloads` folder to the `Documents` folder inside your home directory.

* **Rename a file inside the home directory:**

  ```bash
  mv ~/notes/todo.txt ~/notes/done.txt
  ```

  This renames `todo.txt` to `done.txt` in the `notes` directory under home.

* **Move a file to another directory using `~`:**

  ```bash
  mv ~/Pictures/image.png ~/Desktop/
  ```

* **Copy a file from another directory into your home folder:**

  ```bash
  cp /var/log/syslog ~/log_backup.txt
  ```

* **Copy file from current dir to a subdirectory in home:**

  ```bash
  cp myfile.txt ~/Documents/
  ```

* **Copy using relative path with tilde:**

  ```bash
  cp ../report.txt ~/Reports/
  ```

* **Copy a full folder into home:**

  ```bash
  cp -r /opt/project ~/project_backup
  ```

* **Move multiple files (e.g., `.txt`) to a folder in home:**

  ```bash
  mv *.txt ~/TextFiles/
  ```

---

### 📁 Directory Creation with `mkdir`

* Basic usage
* Creating **parent directories** with `-p`
* Creating **multiple directories at once**


* **`mkdir <dirname>`** – Creates a **single new directory** in the current path.
  Example:

  ```bash
  mkdir myfolder
  ```

* **`mkdir -p <parent/child>`** – Creates **nested directories**, including any missing parent directories.
  Use this when intermediate folders may not exist.
  Example:

  ```bash
  mkdir -p projects/2025/june
  ```

  This creates the entire path: `projects/`, `2025/`, and `june/`.

* **Create multiple directories at once:**

  ```bash
  mkdir folder1 folder2 folder3
  ```

  This will create `folder1`, `folder2`, and `folder3` in the current directory in one command.

* **Using brace expansion to create structured sets of directories:**

  ```bash
  mkdir project_{A,B,C}
  ```

  This creates: `project_A`, `project_B`, and `project_C`.

  ```bash
  mkdir -p client_{X,Y,Z}/docs
  ```

  This creates three directories: `client_X/docs`, `client_Y/docs`, and `client_Z/docs` with nested `docs` folders.

---


### 📂 Directory Navigation with `cd`

* **`cd <dirname>`** – Changes into the specified subdirectory.
  Example:

  ```bash
  cd projects
  ```

* **`cd /data/abc/test`** – Navigates to the specified **absolute path** from root.
  Useful for jumping directly to a known full path.

* **`cd ..`** – Moves **up one directory level** (to the parent directory).
  Example:

  ```bash
  cd ..
  ```

* **`cd ../..`** – Moves **up two levels** from the current directory.
  Handy when you need to quickly backtrack through the folder hierarchy.

* **`cd`** – Changes to the **home directory** (`~`).
  Equivalent to:

  ```bash
  cd ~
  ```

* **`cd -`** – Switches back to the **previous working directory**.
  This is useful when toggling between two locations.

---

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

## 📁 Directory Aliases in Linux

---

### 🧭 What is a Directory Alias?

A **directory alias** is a shortcut or alternate name for a frequently used command or path. It saves time by letting you type a short name instead of a long command or path.

Aliases are usually set in your **shell configuration file** (like `.bashrc`, `.zshrc`, etc.).

---

### 🔧 How to Create a Directory Alias

To define an alias for navigating to a specific directory:

```bash
alias proj='cd /home/hajith/projects/myapp'
```

Now you can just run:

```bash
proj
```

…and you’ll be instantly taken to that folder.

---

### 📝 Making It Permanent

To keep the alias after a reboot or new terminal session:

1. Open your `.bashrc` or `.zshrc` file in your home directory:

```bash
nano ~/.bashrc
```

2. Add the alias at the bottom:

```bash
alias docs='cd ~/Documents'
```

3. Save and exit (`Ctrl + O`, `Enter`, `Ctrl + X`)

4. Apply the changes:

```bash
source ~/.bashrc
```

---

### ⚙️ Example Aliases

```bash
alias dtop='cd ~/Desktop'
alias work='cd ~/workspace'
alias demodir='cd ~/abc/text/demo'
```

Use these to quickly navigate without typing the full path every time.

---

### 📜 View All Aliases

```bash
alias
```

This lists all currently defined aliases.

---

### ❌ Remove an Alias (temporary)

```bash
unalias work
```

To remove it permanently, delete the line from `.bashrc`.

---

### ✅ Bonus: Alias for `ls` and Directory Listings

```bash
alias ll='ls -la'
alias ..='cd ..'
alias ...='cd ../..'
```

---

## 📈 Running Python Scripts in Background and Monitoring with `nohup`

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

* **`du -h`** – Displays **disk usage in human-readable format** (KB, MB, GB).

```bash
du -h
```

* **`du -sh`** – Displays the **total size** of the current directory or specified folder, **summarized and human-readable**.

```bash
du -sh .
du -sh myfolder/
```

---

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

