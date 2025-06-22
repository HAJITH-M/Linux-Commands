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
* **`rm *`** - Removes all the files (fails it contains directory)

* **`rm filename*`** – Removes all files starting with "filename".

* **`rm *filename`** – Removes all files ending with "filename".

* **`rm -r <dirname>`** – Recursively deletes the specified directory and all its contents (use with caution!).

* **`rm -rf dirname*`** – Forcibly and recursively removes all directories starting with "dirname" without prompting (⚠️ dangerous).

* **`rm -i filename*`** – Interactively asks for confirmation before deleting each file that starts with "filename".

* **`rmdir <dirname>`** – Removes an **empty directory** (fails if not empty).

* **`rmdir dirname*`** – Removes all **empty directories** that start with "dirname".

* **`rm -v filename*`** – Deletes matching files and **shows what’s being deleted** (verbose mode).

---

Let me know if you want this turned into a printable cheat sheet, or if you'd like a similar section for other command categories like `cp`, `mv`, or `find`.
