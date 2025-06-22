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

* **`ls -ld <dirname>`** – Shows **detailed info** about a directory without listing its contents.

* **`ls -d <dirname>`** – Shows only the **directory name**, not its contents.

* **`ls -ld <dirname*>`** – Detailed listing for all directories that **start with "dirname"**.

* **`ls -d <dirname*>`** – Lists only the **names** of directories that **start with "dirname"**.

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

* **`cp <oldfilename> <newfilename>`** – Copies a file from source to destination.
  Used when you want to **duplicate** a file in the same or different directory.

* **`mv <oldfilename> <newfilename>`** – Renames or moves a file from source to destination.
  Acts as a **rename** if both files are in the same directory, or a **move** otherwise.

* **Copying using `cat` command:**
  **`cat <oldfilename> >> <newfilename>`** – Appends the content of `oldfilename` to `newfilename`.
  Can also be used for **manual file merging**.

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

