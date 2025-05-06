
## Installation Steps

Follow these instructions to set up **ModelSim Intel FPGA Edition** inside your Xubuntu VM.
- First Read: `Optional Fix-3: Boot from Installed Xubuntu (Exit Live ISO Session)`, to ensure correct drive and avoid errors.

---

### Note: Copy-Paste Between macOS and Xubuntu in UTM

If running Xubuntu in UTM on macOS:

- **Copy (from macOS)**: `Cmd + C`
- **Paste (into VM Terminal)**:  
  Inside Xubuntu Terminal, press:
  ```
  Ctrl + Shift + V
  ```

---

### Step 1: Update System and Install Dependencies

Before installing ModelSim, update the package manager and install essential development libraries to ensure compatibility.

---

**1. Update and Upgrade System Packages:**

Open a terminal and run:

```bash
sudo apt update && sudo apt upgrade -y
```

This ensures your package lists and system software are current.

---

**2. Install Required Dependencies:**

ModelSim requires several runtime libraries and developer tools to run smoothly on Linux. Install them with:

```bash
sudo apt install build-essential libxft2 libxext6 libx11-dev libxtst6 libglu1-mesa -y
```

These libraries support GUI rendering, simulation timing, and system calls ModelSim depends on.

> 📝 Note: If you encounter a `dpkg` error, see the “Fixing dpkg error” section.

---

### Optional Fix-1: `dpkg` Error After Fresh Xubuntu Install

If you see:

```
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Follow these steps to fix it:

**1. Edit the source list:**
   ```bash
   sudo nano /etc/apt/sources.list
   ```

**2. Comment out the line starting with:** `deb cdrom:[...]` by adding a `#`

**3. Save and exit:** (`Ctrl + O`, Enter, then `Ctrl + X`)

**4. Run:**
   ```bash
   sudo dpkg --configure -a
   sudo apt clean
   sudo apt update
   sudo apt upgrade -y
   ```
---

### Optional Fix-2: Broken Install or `dpkg` Errors in UTM VM

In some UTM VM setups, you might encounter errors like:

```
E: Sub-process /usr/bin/dpkg returned an error code (1)
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Stale file handle
```

These are often caused by:
- Interrupted package installs
- `cdrom` source leftover in `/etc/apt/sources.list`
- Virtual disk sync issues (especially after suspend/resume)

Follow these steps to fix it:

**1. Reboot your Xubuntu VM** to clear stale file references:
   ```bash
   sudo reboot
   ```

**2. After reboot, open terminal and run:**

   ```bash
   sudo dpkg --configure -a
   sudo apt --fix-broken install
   ```

**3. Then continue with updates and ModelSim dependency install:**

   ```bash
   sudo apt update && sudo apt upgrade -y
   sudo apt install build-essential libxft2 libxext6 libx11-dev libxtst6 libglu1-mesa -y
   ```

If the problem continues, check which package failed with:
It means: “Give me all packages where the 3rd character (error state) is r” → these are reinstall-required or broken.

```bash
dpkg -l | grep ^..r
```

Then remove and reinstall that package manually if needed.
If it returns nothing, repeat (**3.**) above. 

**Important** There could be memory issue! 

This could me mistakenly done in the Live session, not the real installed Xubuntu !!!

Confirm:
```bash
df -h
```
---

## Optional Fix-3: Boot from Installed Xubuntu (Exit Live ISO Session)

If it is stuck in the Xubuntu Live ISO environment (the "Try Xubuntu" session), it will encounter limited disk space and installation errors.

These steps help with **boot into the actual installed Xubuntu system** on the virtual disk.

---

### Problem Symptoms

- `df -h` shows `/cow` and `/cdrom` as full
- getting errors like:
  ```
  No space left on device
  E: Sub-process /usr/bin/dpkg returned an error code (1)
  ```
- It is not booting from `/dev/sda1` or the installed filesystem

---

### Fix It: Boot from the Installed Xubuntu System

**1. Shut Down the VM**

- Click the **Stop** button

---

**2. Remove the Xubuntu ISO**

- In UTM, click **Edit** on the VM (right click)
- Go to the **Drives** section
- **Do not remove the real virtual hard disk** (*.qcow2 is ~64 GB or more (virtual), 8.19 GB (actual), this will expand with use!)
- Remove the attached **`xubuntu-22.04-desktop-amd64.iso`** (*.iso is ~2–4 GB)
- Uncheck or remove it 

---

**3. Restart the VM**

- Start the VM again from UTM
- It should now boot from the installed Xubuntu system on disk

---

### Verify it is in the Real System

Run:

```bash
df -h
```

✅ It should show something like:

```
/dev/sda1        64G    4G   58G  7% /
```

No `/cow`, no `/cdrom`.

---

It is now in the **fully installed environment** and ready to proceed with:

- Installing ModelSim
- Running updates and simulation scripts
---
**Next:** [Install ModelSim](https://github.com/preeti-chauhan/hwe-modelsim-xubuntu-macos/blob/main/02-Install-ModelSim.md)
