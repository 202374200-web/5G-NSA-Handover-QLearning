# 5G-NSA-Handover-QLearning
4G/5G NSA Smart Handover using Q-Learning - Sana'a University


# Intelligent Handover & Radio Resource Management in 4G/5G NSA Networks Using Q-Learning

**B.Sc. Graduation Project — Department of Electrical Engineering (Telecommunications & Networks Track)**  
**Faculty of Engineering, Sana'a University — Sana'a, Yemen**

---

## 📌 Project Overview

This repository contains the spatial RF datasets, Reinforcement Learning (`Tabular Q-Learning`) training pipeline, and interactive `PyQt5` Digital-Twin simulator developed for our graduation project. The study addresses mobility management challenges in **4G/5G Non-Standalone (NSA — EN-DC Option 3x)** networks deployed in dense urban environments, using the **Hadda Commercial Area in Al-Wahdah District, Sana'a** as a real-world testbed.

By integrating deterministic radio propagation modeling from **Forsk Atoll** and **Global Mapper** with an **O-RAN Near-RT RIC Traffic Steering xApp** model in **Python**, the proposed Q-Learning agent dynamically balances throughput maximization, handover stability, and user equipment (UE) battery conservation.

### 👥 Research Team
* **Alian Aref Ahmed Thawaba** — *AI / Reinforcement Learning & Interactive GUI Lead*
* **Nasrallah** — *RF Network Planning (Forsk Atoll) & GIS Cartography*
* **Ahmed** — *Spatial Data Engineering & 3GPP Protocol Analysis*
* **Masoud** — *Multi-KPI QoS Evaluation & Technical Documentation*

---

## 🗺️ Study Area & Radio Network Architecture

* **Geographic Scope:** Hadda Commercial Area, Al-Wahdah District, Sana'a (`WGS 84 / UTM Zone 38N`, spanning `3.15 km × 2.70 km`).
* **Deployment Topology:** 9 co-located tri-sector macro sites (`Site0` – `Site8`, 54 total cells) modeled over real Digital Terrain Models (DTM), WorldPop demographic distributions, and 18-meter urban building clutter.
* **4G LTE Anchor Layer:** Band 1 (`2100 MHz`), `10 MHz` bandwidth, `4T4R MIMO`, `Cost-Hata` propagation model.
* **5G NR Secondary Layer:** Band n78 (`3500 MHz`), `50 MHz` bandwidth, `128T128R Massive MIMO` beamforming, `3GPP TR 38.900` propagation model.
* **Spatial RF Dataset:** `2,338` merged grid coordinates (`Hadda_Q_Learning_Dataset.csv`) evaluated along a continuous `5,325 m` urban mobility trajectory.

---

## 📊 Performance Evaluation (8 KPIs Benchmark)

The trained Q-Learning agent (incorporating a 1-step stability memory register and a `3.5 dB` proactive emergency fallback threshold) was benchmarked against the standard **3GPP Event A3/B1** baseline across both **Pedestrian (`5 km/h`)** and **Vehicular (`50 km/h`)** mobility scenarios:

| Key Performance Indicator (KPI) | Pedestrian (`5 km/h`)<br>3GPP Baseline | Pedestrian (`5 km/h`)<br>Proposed Q-Learning | Vehicular (`50 km/h`)<br>3GPP Baseline | Vehicular (`50 km/h`)<br>Proposed Q-Learning |
| :--- | :---: | :---: | :---: | :---: |
| **Effective Goodput (Mbps)** | 107.60 Mbps | **106.87 Mbps** | 88.63 Mbps | **89.57 Mbps** |
| **Spectral Efficiency (bps/Hz)** | 2.15 bps/Hz | **2.19 bps/Hz** | 1.93 bps/Hz | **1.98 bps/Hz** |
| **Total Handover Events (HOs)** | 61 Events | **38 Events (-37.7%)** | 65 Events | **40 Events (-38.5%)** |
| **Ping-Pong Handovers** | 12 Events | **0 Events (-100%)** | 11 Events | **0 Events (-100%)** |
| **Radio Link Failure Rate (RLF %)** | 5.63% | **0.00% (Zero Outage)** | 7.04% | **0.00% (Zero Outage)** |
| **Average Handover Delay (ms)** | 4.37 ms | **2.70 ms (-38.2%)** | 4.46 ms | **2.93 ms (-34.3%)** |
| **Packet Loss Rate (%)** | 0.72% | **0.27%** | 0.80% | **0.29%** |
| **Average UE Modem Current (mA)** | 538.5 mA | **505.9 mA** | 511.7 mA | **481.0 mA** |
| **Energy Efficiency (Mbit/Joule)** | 52.59 Mbit/J | **55.59 Mbit/J (+5.7%)** | 45.58 Mbit/J | **49.00 Mbit/J (+7.5%)** |

### 📈 Visual Results & Convergence Analysis

#### 1. Mobility Trajectory, SINR Profile & Q-Learning Convergence
![Mobility Analysis](Hadda_Full_Mobility_Analysis.png)

#### 2. Multi-KPI Comparative Evaluation (3GPP vs. Q-Learning)
![KPIs Evaluation](Hadda_KPIs_Evaluation_Charts.png)

---

## 📂 Repository Structure

```text
├── Hadda_Q_Learning_Dataset.csv        # Merged 4G/5G spatial RF dataset (2,338 points from Atoll)
├── Hadda_Route_Simulation.csv          # Evaluated 5,325m trajectory decisions & telemetry logs
├── q_table_hadda.npy                   # Pre-trained Q-Learning policy table (350 episodes)
├── train_q_learning.py                 # Q-Learning training script & 300 DPI chart generator
├── hadda_gui_simulator.py              # Interactive PyQt5 O-RAN Digital Twin desktop simulator
├── Hadda_Full_Mobility_Analysis.png    # 4-panel mobility & convergence visualization
├── Hadda_KPIs_Evaluation_Charts.png    # 4-panel KPI comparison bar charts
└── README.md                           # Project documentation
