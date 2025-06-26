# 🧮 AWK Command Line Tool 

`awk` is a powerful command-line tool used for:

* Processing columns in text
* Performing calculations
* Extracting and formatting data from files

✅ It’s especially useful for working with **structured text files** where data is organized in columns.

### 👨‍💻 Developed by:

**Aho**, **Weinberger**, and **Kernighan**
(The name "AWK" comes from their initials.)

---

## 🗂️ Sample Data File

**File:** `data.txt`

```text
john 10 developer
sha 90 tester
zara 80 designer
```

---

## 📄 Basic AWK Commands

### Print all content:

```bash
awk '{print}' data.txt
```

**Output:**

```
john 10 developer
sha 90 tester
zara 80 designer
```

---

### Print only the first column (`$1`):

```bash
awk '{print $1}' data.txt
```

**Output:**

```
john
sha
zara
```

---

### Print first and third column (no space in between):

```bash
awk '{print $1 $3}' data.txt
```

**Output:**

```
johndeveloper
shatester
zaradesigner
```

---

### Print first and third column (with space):

```bash
awk '{print $1, $3}' data.txt
```

**Output:**

```
john developer
sha tester
zara designer
```

---

### Conditional Filtering – Show records with age > 10

```bash
awk '$2 > 10 {print $1, $3}' data.txt
```

**Explanation:**

* `$2` refers to the second column (age).
* Filters rows where age > 10.

**Output:**

```
sha tester
zara designer
```

---

## 🧾 Using `printf` for Formatting

```bash
awk '{printf "Name: %s | Age: %s | Role: %s\n", $1, $2, $3}' data.txt
```

**Explanation:**

* `printf` allows you to format the output like in C.
* `%s` is used for strings.
* `\n` adds a new line at the end.
* `$1`, `$2`, `$3` represent the first, second, and third columns.

**Output:**

```
Name: john | Age: 10 | Role: developer
Name: sha | Age: 90 | Role: tester
Name: zara | Age: 80 | Role: designer
```

---

## 🔍 Why Add `NF` (Number of Fields)?

```bash
awk 'NF {printf "Name: %s | Age: %s | Role: %s\n", $1, $2, $3}' data.txt
```

**What does `NF` do?**

* `NF` stands for **Number of Fields** in a line.
* It returns `0` for **empty lines**.
* So `NF { ... }` means: **"only run this block if the line is not empty."**

This prevents blank output like:

```
Name:  | Age:  | Role:
```

---

## ✅ With vs Without `NF`

### 🔹 Without `NF`:

```bash
awk '{printf "Name: %s | Age: %s | Role: %s\n", $1, $2, $3}' data.txt
```

**Output (if file has an empty line at the end):**

```
Name: john | Age: 10 | Role: developer
Name: sha | Age: 90 | Role: tester
Name: zara | Age: 80 | Role: designer
Name:  | Age:  | Role:
```

### 🔹 With `NF`:

```bash
awk 'NF {printf "Name: %s | Age: %s | Role: %s\n", $1, $2, $3}' data.txt
```

**Output:**

```
Name: john | Age: 10 | Role: developer
Name: sha | Age: 90 | Role: tester
Name: zara | Age: 80 | Role: designer
```

> ✅ **Clean and avoids printing empty or invalid rows.**

---

There are more awk - commands if you need you can explore it by searching.

---
