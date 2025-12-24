# ASIC Implementation of Digital System Transmitter

This repository contains the complete **RTL-to-GDSII** implementation flow for a Digital System Transmitter. The project demonstrates a full backend ASIC design cycle, including logic synthesis, floorplanning, placement, clock tree synthesis (CTS), routing, and sign-off timing analysis.

---

## 📌 Project Overview
The objective of this project was to transform a high-level RTL description into an optimized physical layout (GDSII) ready for fabrication, ensuring all timing, area, and power constraints were strictly met.



### Key Highlights:
- **Design Methodology:** Full RTL-to-GDSII flow using industry-standard tools.
- **Optimization:** Comparative analysis between Area, Power, and Timing-driven synthesis.
- **Verification:** Successfully cleared LVS/DRC and achieved zero timing slack (Setup/Hold) in PrimeTime.
- **Flow Stages:** Synthesis → Floorplan → Power Planning → Placement → CTS → Routing → STA.

---

## 🏗️ Implementation Flow

The implementation follows the standard VLSI backend flow:

1. **Synthesis:** Performed using **Synopsys Design Compiler** to map RTL to gate-level netlists.
2. **Floorplanning:** Defined die area, aspect ratio, and I/O port placement.
3. **Power Planning:** Established the power grid (Rings, Meshes, and Standard Cell Rails).
4. **Placement:** Optimized standard cell positioning with high-density legalization.
5. **CTS (Clock Tree Synthesis):** Built a balanced clock tree to minimize skew and latency.
6. **Routing:** Global and Detail routing to resolve connectivity and DRC violations.
7. **Sign-off:** Final Static Timing Analysis (STA) using **Synopsys PrimeTime**.

---

## 📊 Synthesis Results Comparison

The design was synthesized under different strategies to evaluate trade-offs:

| Strategy | Total Area ($\mu m^2$) | Total Power ($mW$) | Setup Slack |
| :--- | :--- | :--- | :--- |
| **No Constraints** | 1565.80 | 0.203 | N/A |
| **Area Optimized** | 1950.98 | 6.554 | 0.00 |
| **Power Optimized** | 2537.30 | 6.606 | 0.00 |
| **Timing Optimized** | 1953.50 | 6.557 | 0.00 |

---

## 📁 Repository Structure

```text
├── scripts/          # Tcl scripts for Synthesis, PnR, and PrimeTime
├── cons/             # SDC (Synopsys Design Constraints) files
├── report/           # Synthesis, Area, Power, and Timing reports
├── result/           # Final GDSII, Netlists, and SPEF files
├── starrc/           # Parasitic extraction files
└── sta/              # PrimeTime timing reports & fixing scripts
