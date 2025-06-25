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
* **move a full folder into home:**

  ```bash
  mv Day-2 ~/
  ```

---
