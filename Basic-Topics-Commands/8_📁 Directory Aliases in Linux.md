
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
