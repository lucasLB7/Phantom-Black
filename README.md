# Phantom-Black
Phantom Black Cyberdeck - a modular dual-node system with a FastAPI command layer, enabling real-time control of SDR, navigation and AI workloads in a field-ready architecture. Build on dual raspberry-pi and esp32 supervisor and watchdog

# 🧠 CYBERDECK — Field Computing Platform

## 🚀 Overview

The Cyberdeck is a modular, field-deployable computing system designed for **offline capability, hardware control, and multi-domain operations**.

It combines:
- RF analysis (SDR)
- Offline intelligence (LLM + knowledge base)
- Navigation & telemetry
- Hardware supervision (ESP32 layer)

> This is not just a portable computer — it is a **self-contained digital operations unit**.

---

## 🏗️ Architecture

### 🔹 Compute Layer

**Pi1 — UI Node**
- Operator interface
- Browser / display system
- Input control layer

**Pi2 — Backend Node**
- Headless (CLI)
- Runs:
  - FastAPI control server
  - Future workloads (SDR, LLM, NAV)

---

### 🔹 Supervisor Layer (Planned)

**ESP32**
- Hardware control (fans, sensors, battery)
- Mode selection (rotary encoder)
- Emergency system (GNSS + GSM + LoRa)
- Telemetry + watchdog logic

---

### 🔹 Network Layer

Dedicated direct Ethernet link:

| Device | IP Address     |
|--------|----------------|
| Pi1    | 192.168.50.1   |
| Pi2    | 192.168.50.2   |

- Static IP configuration
- No DHCP dependency
- Fully deterministic communication

---

## 🌍 End Vision

The Cyberdeck operates in **mode-based workflows**:

### 📡 RADIO MODE
- SDR signal analysis
- Frequency scanning
- Directional antenna optimization
- RF intelligence gathering

### 🧭 NAV MODE
- GPS tracking
- Route visualization
- Rover/system integration

### 🧠 LLM MODE
- Offline AI assistant
- Technical reasoning & knowledge access

### 📚 KNOWLEDGE MODE
- Offline Wikipedia / indexed datasets
- Fast lookup system

---

## 🧱 Milestones & Progress

### 📅 Phase 1 — Concept & Architecture
- Defined dual-node system (Pi1 + Pi2)
- Introduced ESP32 supervisor concept
- Designed mode-based operation model

---

### 📅 Phase 2 — Network Foundation

#### ✅ Static Ethernet Backbone
- Direct Pi ↔ Pi connection established
- Static IP assignment:
  - `192.168.50.1`
  - `192.168.50.2`

#### ✅ Network Stabilization
- Disabled:
  - `NetworkManager`
  - DHCP (`dhcp4`)
- Implemented manual netplan config:
  - `99-cyberdeck.yaml`

#### ✅ Stress Testing
```bash
ping -f 192.168.50.2

## ⏱️ Stress Test Results

- **Duration:** ~30 minutes  
- **Result:**
  - Stable connection  
  - No packet loss  
  - No interface drops  

---

## 📅 Phase 3 — Backend System

### ✅ FastAPI Server (Pi2)

**Endpoints:**
- `/status`
- `/mode/{mode}`

**Run manually:**
```bash
python3 main.py
✅ Systemd Integration
Service: cyberdeck-api.service
Auto-start enabled on boot
✅ Boot Validation
Pi2 reboot tested
API confirmed running automatically
📅 Phase 4 — System Decisions
🔒 Security
Autologin disabled
CLI access retained
🧠 Control Model
Pi2 = autonomous backend
Pi1 = control interface
ESP32 = future supervisor
⚠️ Current Limitations
❌ Pi1 not yet connected to API
❌ Mode switching is not functional (logic only)
❌ No service orchestration (SDR / LLM not started)
❌ ESP32 not integrated
❌ No UI layer yet
✅ Core Achievements
Stable dual-node architecture
Clean static networking (no DHCP conflicts)
Reliable direct Ethernet communication
Persistent backend service (auto-start)
Defined scalable system architecture

The foundation is production-grade and stable

🧭 Next Steps
🔹 Phase 5 — Control Layer

Test API from Pi1:

curl http://192.168.50.2:8000/status

Trigger mode:

curl http://192.168.50.2:8000/mode/radio

Build:

Minimal CLI or web UI on Pi1
🔹 Phase 6 — Mode Execution

Implement service control:

def set_mode(mode):
    stop_all_services()

    if mode == "radio":
        start_sdr()
    elif mode == "llm":
        start_llm()
🔹 Phase 7 — SDR Integration
Install SDR stack (e.g. SDR++)
Bind to RADIO mode
Add scanning + logging
🔹 Phase 8 — ESP32 Integration
Serial/WiFi communication
Mode input control
Fan + thermal + battery management
🔹 Phase 9 — System Cohesion
Sync UI ↔ backend
Add feedback + logging
Status reporting
🔹 Phase 10 — Field Deployment
Battery system (3S5P 18650)
Cooling system
Rugged enclosure
Weatherproofing
🧠 Strategic Insight

This project prioritizes:

Infrastructure before functionality

What’s already secured:
Stable networking ✔
Boot reliability ✔
Architecture clarity ✔
This avoids:
Fragile systems
Hidden bugs
Scaling issues later
📌 Suggested Commit Message
Initial cyberdeck core system foundation

- Established dual Raspberry Pi architecture (UI + backend)
- Configured static Ethernet link (192.168.50.1 ↔ 192.168.50.2)
- Disabled NetworkManager/DHCP conflicts, moved to manual netplan config
- Stress-tested connection (30min ping flood, stable)
- Implemented FastAPI backend with /status and /mode endpoints
- Added systemd service for auto-start on boot
- Defined system architecture, modes, and expansion roadmap

Foundation complete — ready for control layer and service integration
🔚 Status

Foundation complete.
System is stable, deterministic, and ready for functional expansion.
