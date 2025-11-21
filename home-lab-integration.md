Homelab Integration Plan

This document outlines the integration of my homelab environment with the Ranger TDI Overland Build project, focusing on leveraging computing power, storage, and network capabilities to support mobile and remote workflows.

My primary homelab server is a Dell PowerEdge R730 equipped with dual Intel Xeon E5-2560 CPUs, 192 GB of RAM, and a high-capacity SSD storage array. It serves as the backbone for data storage, rendering tasks, and software development resources.

The homelab is designed to seamlessly sync and interact with my mobile workstation setups, including:

    A Dell Precision 7560 laptop with Xeon CPU and Nvidia A4000 GPU running Arch Linux for on-the-go development and work.

    A Dell Optiplex mini-workstation installed in the Ranger, planned to act as a mobile server hub for data feeds, camera inputs, and remote system monitoring.

    Future plans for GPU upgrades (Nvidia RTX 4070, possible A6000) and additional PowerEdge servers for NAS and dedicated processing.

This integration will facilitate smooth data flow between home and mobile environments, enabling efficient remote work, rendering offload, and system control while on the road or at job sites.

⚙️ Hardware Overview

🖥️ Dell PowerEdge R730 (Primary Server)

CPU: Dual Xeon E5-2690v4 (planned upgrade)

RAM: 192 GB ECC

Drives: 8x 2.5" SFF SSDs (1.2TB each)

Expansion Plan: Add second SFF bay (8 slots)

GPU: RX 580 currently installed, to be upgraded to RTX 4070, then A6000 or Radeon Pro W7900

Use Case: Rendering offload, backup sync, camera footage ingest, AI/ML, personal cloud services

💾 Dell PowerEdge R630 (Planned NAS Node)

Purpose: Dedicated NAS/TrueNAS SCALE or Ceph/ZFS target

Notes: To serve as long-term media/archive sync, with 10GbE bridging to R730

🖥️ Workstation (Current)

CPU: AMD Ryzen 7 5800X

GPU: RTX 4070 (to be moved to R730)

RAM: 48 GB

Storage: 6TB (3x M.2, 3x SATA SSD)

OS: Arch Linux + KDE (assumed)

🖥️ Workstation (Planned Upgrade)

CPU: AMD Ryzen 9 9950X3D (Microcenter bundle)

Motherboard: ASUS X670E (WiFi included)

RAM: 32 GB DDR5 (to be upgraded later)

Use Case: Main dev box, occasional gaming, fallback render node, full integration with homelab

🔌 Truck Integration

Dell OptiPlex Micro Workstation (in-truck compute node)

Raspberry Pi 4 (router, sensor control, Wi-Fi puck, thermal ingest)

Tablet Touchscreen (Samsung Galaxy Tab or similar)

Full Linux-based UI environment (Debian fork, minimal overhead)

Video input from BMW/Mercedes thermal cam module

Bluetooth peripherals for road work & dev sync

Offline-first data caching, synced via Syncthing or Git when on network

🔋 Power + Cooling Plans

Blower-Style GPU: Avoid thermal overload in R730 chassis

Ranger Dual Battery Setup:

Relocated to jump seat space inside cab

Deep cycle AGM or YellowTop batteries

Solar panel on bed rack for off-grid operation

Inverter System:

Mounted behind driver seat

Supports Ryobi tool use, trickle charging

📡 Networking + Sync

Home Network:

R730 and R630 on bonded or 10GbE link

Main desktop connects via Wi-Fi 6E or wired fiber

All systems run Syncthing or rsync for local/offsite data integrity

Field Truck:

Wi-Fi puck + boosted antenna

Optionally runs SSH tunnel or Tailscale for secure remote connection

📁 Submodules for Expansion

homelab/r730-config.md

BIOS/Firmware

ZFS install

GPU tuning

homelab/nas-node.md

R630 configuration

Ceph/TrueNAS/SCALE setup

homelab/desktop-upgrade-plan.md

AM5 build

GPU migration

homelab/camera-ingest-pipeline.md

Thermal cam integration

Pi-to-optiplex video routing

homelab/gpu-selection-notes.md

A6000 vs 7900XTX

Performance comparisons

Price tracking

✅ Next Steps

Upgrade R730 CPUs to E5-2690v4

Add second drive bay + SSDs

Install Proxmox with ZFS pool

Set up Git remote sync to Ranger repo

Migrate RTX 4070 to R730

Begin camera pipeline testing

Fork homelab folder to dedicated repo as needed

Stay modular, iterate fast, and treat everything like code.

