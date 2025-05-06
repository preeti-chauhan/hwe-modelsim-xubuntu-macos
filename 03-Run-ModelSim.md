### Step 3: Run ModelSim

Once installed, launch ModelSim from its install directory.

---

**1. Launch ModelSim GUI:**

Open a terminal and run:

```bash
cd ~/intelFPGA_std/modelsim_ase/bin
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
echo 'export PATH="$HOME/intelFPGA_std/bin:$PATH"' >> ~/.bashrc
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

## Troubleshooting

### 1. **vsim** not working






