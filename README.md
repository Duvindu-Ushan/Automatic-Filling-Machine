# Automatic Filling Machine – PLC Control System

This project presents a **PLC-based automatic filling machine** that automates the product filling process using **multiple tanks and sensors**.  
The system is designed to ensure efficient, accurate, and safe filling operations for industrial applications.

---

## 🧠 System Overview

The **Automatic Filling Machine Control System** detects product arrival on a conveyor, positions the product below the correct filling nozzle, fills it for a specific duration, and then releases it automatically.  
The process is governed by a **selector switch** that determines whether to use the **Yellow Tank**, **Blue Tank**, or **Both Tanks** for filling.

![image alt](https://github.com/Duvindu-Ushan/Automatic-Filling-Machine/blob/43352bd303dd3c0c8fdf089a389e1f414fe609a8/Screenshot%20(3329).png)

---

## ⚙️ Initial Conditions

| Component | Status | Description |
|------------|---------|-------------|
| **Job_in Sensor** | ON | Detects product arrival at the filling station |
| **Job_out Sensor** | OFF | Product not yet exited |
| **Yellow Tank High-Level Sensor (YTHL)** | ON | Indicates Yellow tank is sufficiently filled |
| **Blue Tank High-Level Sensor (BTHL)** | ON | Indicates Blue tank is sufficiently filled |

---

## 🔄 Operating Modes (Based on Selector Switch)

### 🟡 **Condition 1 – Yellow Tank Filling**
If the Selector Switch is set to **Yellow**:
1. Press **Start_PB** → Conveyor starts moving.
2. Conveyor runs until **Filling_Sensor_1** is activated.
3. After **2 seconds**, **Valve_Yellow** opens.
4. **Valve_Yellow** remains open for **20 seconds**.
5. After **2 more seconds**, the conveyor resumes.
6. Conveyor continues until **Job_out Sensor** is triggered (product exit).

---

### 🔵 **Condition 2 – Blue Tank Filling**
If the Selector Switch is set to **Blue**:
1. Press **Start_PB** → Conveyor starts moving.
2. Conveyor runs until **Filling_Sensor_2** is activated.
3. After **2 seconds**, **Valve_Blue** opens.
4. **Valve_Blue** remains open for **20 seconds**.
5. After **2 more seconds**, the conveyor resumes.
6. Conveyor continues until **Job_out Sensor** is triggered.

---

### 🟢 **Condition 3 – Both Tanks Filling**
If the Selector Switch is set to **Both**:
1. Press **Start_PB** → Conveyor starts moving.
2. Conveyor runs until **Filling_Sensor_1** is activated.
3. After **1 second**, **Valve_Yellow** opens for **10 seconds**.
4. After **2 seconds**, conveyor resumes until **Filling_Sensor_2** is activated.
5. After **1 second**, **Valve_Blue** opens for **10 seconds**.
6. After **2 seconds**, conveyor resumes until **Job_out Sensor** is triggered.

---

## 🧩 Components Used

- **PLC Controller** (e.g., FATEK / Siemens / Allen Bradley)
- **Start / Stop Push Buttons**
- **Selector Switch** (Yellow / Blue / Both)
- **Conveyor Motor**
- **Filling Valves** (Valve_Yellow, Valve_Blue)
- **Sensors**:
  - Job_in Sensor
  - Job_out Sensor
  - Filling_Sensor_1
  - Filling_Sensor_2
  - Tank Level Sensors (YTHL, BTHL)
- **Timers & Relays** (configured in ladder logic)

---

## 🪜 PLC Logic Description

The PLC program uses **ladder logic** to control:
- Conveyor motor sequencing
- Valve timing
- Sensor-based event triggers
- Mode-based process selection
- Safety interlocks and timing delays

The sequence ensures **accurate filling**, **non-overlapping operations**, and **automated product movement** with minimal operator intervention.

---

## 🧰 Tools & Development

- **Programming Environment:** WinProLadder / TIA Portal / RSLogix (depending on PLC brand)
- **Simulation Tool:** PLC Simulator or Factory I/O (optional)
- **Language:** Ladder Diagram (LD)

---

## 📁 Repository Structure

