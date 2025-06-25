## 🔢 Count & Sort – Using `wc` and `sort`

---

### 📊 `wc` – Word Count Utility

`wc` is used to count lines, words, and characters in a file.

#### 🔹 `wc <filename>`

```bash
wc myfile.txt
```

Displays **lines**, **words**, and **bytes** (in that order) of the file.

#### 🔹 `wc -l <filename>` – **Line count**

```bash
wc -l myfile.txt
```

Counts and displays only the number of lines.

#### 🔹 `wc -w <filename>` – **Word count**

```bash
wc -w myfile.txt
```

Counts and displays only the number of words.

#### 🔹 `wc -c <filename>` – **Byte count**

```bash
wc -c myfile.txt
```

Counts and displays only the number of bytes (not characters, unless all are ASCII).

---

### 🔠 `sort` – Sorting Files

#### 📄 `sortfile.txt` Contents:

```
zebra
apple
banana
mango
lock
hut
```

#### 🔹 `sort sortfile.txt` – Sort alphabetically (ascending)

```bash
sort sortfile.txt
```

**Output:**

```
apple
banana
hut
lock
mango
zebra
```

#### 🔹 `sort -r sortfile.txt` – Sort alphabetically (descending)

```bash
sort -r sortfile.txt
```

**Output:**

```
zebra
mango
lock
hut
banana
apple
```

---

#### 📄 `sortfile2.txt` Contents:

```
9
7
1
4
8
0
10
```

#### 🔹 `sort -n -r sortfile2.txt` – **Numeric sort** in **reverse order**

```bash
sort -n -r sortfile2.txt
```

**Output:**

```
10
9
8
7
4
1
0
```

📌 Option Breakdown:

* `-n` → Sort by numeric value
* `-r` → Reverse the sorting order (descending)

---



