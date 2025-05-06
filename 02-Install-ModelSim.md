### Step 2: Download and Install ModelSim

**Optional: Install Firefox**

Run the following commands:

```bash
sudo apt update
sudo apt install firefox -y
```

This installs the latest stable version of Firefox and adds it to your application menu.

---

**Optional: Launch Firefox**

After installation, launch Firefox by either:

- Clicking **Applications → Internet → Firefox**
- Or running in terminal:

```bash
firefox &
```

**1. Download the Installer:**

From within your **Xubuntu VM**, open Firefox and go to:

[https://fpgasoftware.intel.com](https://fpgasoftware.intel.com)

Then:

- Select **ModelSim – Intel FPGA Edition (Linux)**
- Choose **Standard** version (check installation guides)
- Save the `.run` file to your `Downloads` folder  
  (e.g., `ModelSimSetup-<version>.run`)

> ℹ️ This may require to register or sign in with an Intel account

---

**2. Make the Installer Executable:**

Open a terminal and run:

```bash
cd ~/Downloads
chmod +x ModelSimSetup-*.run
```

Use `Tab` to autocomplete the filename if needed.

---

**3. Run the Installer in Text Mode:**

```bash
./ModelSimSetup-*.run --mode text
```

This avoids the GUI installer (which can be slow in UTM) and provides a simple terminal-based flow.

---

**4. Choose the Install Directory:**

When prompted, install to:

```bash
~/intelFPGA_std/
```

If the folder doesn’t exist, the installer will create it.

---

**5. Confirm Installation Success:**

It shows a message like:

```
Installation completed successfully.
```

---


## Troubleshooting

### 1) ./vsim gives error





