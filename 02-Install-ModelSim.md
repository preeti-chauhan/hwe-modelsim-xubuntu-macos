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
~/intelFPGA_std/modelsim_int/
```

If the folder doesn’t exist, the installer will create it.

---

**5. Confirm Installation Success:**

It shows a message like:

```
Installation completed successfully.
```

---

### Step 3: Run ModelSim

Once installed, launch ModelSim from its install directory.

---

**1. Launch ModelSim GUI:**

Open a terminal and run:

```bash
cd ~/intelFPGA_std/modelsim_int/modelsim_ase/bin
./vsim
```

This starts the full GUI version of ModelSim. It should show the main simulation window open.

---

**2. Launch in Console Mode (Faster for VMs):**

To run ModelSim in command-line mode (useful for scripting or low-resource systems):

```bash
./vsim -c
```

This allows to load designs, run simulations, and print results in the terminal.

---

**3. Add to PATH (Optional):**

To avoid typing the full path every time, optionally add ModelSim to the shell PATH:

```bash
echo 'export PATH="$HOME/intelFPGA_std/modelsim_int/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Now it can just be run using:

```bash
vsim
```

or

```bash
vsim -c
```

from anywhere in the terminal.

---

✅ ModelSim is now ready to simulate Verilog designs!
