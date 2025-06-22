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

Certainly! Here's your updated **📂 LS Commands to Know** section with the **`ls -lstr`** command added at the end, along with its breakdown—formatted just like the rest of your document:

---

### 📂 LS Commands to Know

* **`ls`** – Lists **all files and directories** in the current directory.

* **`ls *`** – Lists **all files and folders recursively** that match the wildcard `*`.

* **`ls filename*`** – Lists all files that **start with "filename"**.

* **`ls *filename`** – Lists all files that **end with "filename"**.

* **`ls -ld <dirname>`** – Shows **detailed info** about a directory without listing its contents.

* **`ls -d <dirname>`** – Shows only the **directory name**, not its contents.

* **`ls -ld <dirname*>`** – Detailed listing for all directories that **start with "dirname"**.

* **`ls -ld *`** – Detailed listing for all directories that **start with "dirname"**.

* **`ls -d <dirname*>`** – Lists only the **names** of directories that **start with "dirname"**.

* **`ls -lstr`** – Lists files in **long format**, showing **block size**, sorted by **modification time**, in **reverse order** (oldest first).
  A powerful combination to see file details and sort by time.

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
