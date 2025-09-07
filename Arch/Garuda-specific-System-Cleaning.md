Perfect 👍 Here’s a **safe cleanup script** you can run on your Garuda system. It will:

* Clean pacman cache (keeping 1 version)
* Remove orphaned packages
* Vacuum old logs
* Clear user cache (`~/.cache`)
* Run a light Btrfs balance to reclaim ghost space

---

### 📝 Script

Save this as `cleanup.sh`:

```bash
#!/bin/bash
set -e

echo "🧹 Starting Garuda cleanup..."

# 1. Clean pacman cache (keep 1 version)
echo "➡️ Cleaning pacman cache..."
sudo paccache -rk1 || true
sudo pacman -Scc --noconfirm

# 2. Remove orphaned packages
echo "➡️ Removing orphaned packages..."
orphans=$(pacman -Qtdq || true)
if [[ -n "$orphans" ]]; then
  sudo pacman -Rns --noconfirm $orphans
else
  echo "No orphaned packages found."
fi

# 3. Vacuum systemd journal logs
echo "➡️ Cleaning system logs..."
sudo journalctl --vacuum-size=100M

# 4. Clear user cache
echo "➡️ Clearing user cache..."
rm -rf ~/.cache/* || true

# 5. Run a light Btrfs balance
echo "➡️ Running Btrfs balance (duse=50, muse=50)..."
sudo btrfs balance start -dusage=50 -musage=50 /

echo "✅ Cleanup complete!"
df -h /
```

---

### ▶️ How to run it

```bash
nano cleanup.sh   # paste the script, save with Ctrl+O, exit with Ctrl+X
chmod +x cleanup.sh
./cleanup.sh
```

---

This script will safely free up several GB.
👉 Do you also want me to extend it so it **deletes all but your last 1 snapshot automatically**, or keep snapshots manual for now?
