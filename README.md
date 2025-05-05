# ModelSim Verilog Simulation on macOS via Xubuntu VM

## Overview
- A clean and portable way to run ModelSim on macOS using a Xubuntu virtual machine.  
- Provides an environment to write, test, and simulate basic Verilog programs without OS compatibility issues.  
- Keeps all simulation tasks fully contained within the VM, isolating them from the host system.

## Motivation
- ModelSim is a widely used HDL simulator, but it is not natively supported on macOS.  
- This project solves that by running ModelSim inside a Linux VM with full GUI and functional support.  
- Enables a consistent Verilog simulation workflow on macOS without relying on unofficial tools or workarounds.

## System Configuration
- **Host OS**: macOS (Apple Silicon)  
- **Virtualization Tool**: [UTM](https://mac.getutm.app/)  
- **Guest OS**: [Xubuntu 20.04 LTS or later](https://xubuntu.org/download) (select a mirror in a location close to you.)
- **VM Specs**: 64 GB virtual disk, 4–8 GB RAM  
- **Simulator**: [ModelSim Intel FPGA Edition (Lite)](https://fpgasoftware.intel.com/)


## Setup Steps
1. Download the Xubuntu ISO from https://xubuntu.org/download  
2. Create a new VM in UTM:
   - Allocate 64 GB disk, 4–8 GB RAM
   - Install Xubuntu inside the VM
3. Download ModelSim from: https://fpgasoftware.intel.com/
4. Inside the VM, install ModelSim:
   ```bash
   chmod +x ModelSimSetup-<version>.run
   ./ModelSimSetup-<version>.run
5. Verify installation by launching ModelSim with `vsim` inside the VM;
   the GUI should open showing the console and waveform viewer without errors.
