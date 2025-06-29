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


  * **Create Directories `project_1` to `project_100` with a `docs` Subdirectory:**

  ```bash
  mkdir -p project_{1..100}/docs
  ```

  **Explanation:**

  * `project_{1..100}` creates `project_1`, `project_2`, ..., `project_100`.
  * The `/docs` adds a `docs` folder inside each.

  ---

  * **Create Directories `project_a` to `project_z` with a `docs` Subdirectory**

  ```bash
  mkdir -p project_{a..z}/docs
  ```

  **Explanation:**

  * `project_{a..z}` expands from `project_a` to `project_z`.
  * Each will contain its own `docs` folder.

  ---

