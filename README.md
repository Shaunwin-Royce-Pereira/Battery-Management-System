# Battery Management System — MATLAB/Simulink
Industrial-style Battery Management System developed in MATLAB/Simulink featuring cell monitoring, SOC/SOH estimation, protection, balancing, contactor control, precharge logic, fault diagnostics, and BMS state management.
#Overview
This project presents a modular Battery Management System (BMS) developed in MATLAB/Simulink for a 4S battery pack.

The system was developed with an industrial-oriented architecture covering battery monitoring, protection, estimation, cell balancing, contactor management, precharge control, and fault handling.

The current implementation represents Version 1 of the BMS architecture and is being developed as a simulation-first platform before future embedded hardware implementation.

The BMS consists of the following major modules

# System Architecture
- Battery Pack Model
- Cell Voltage Monitoring
- Pack Current Measurement
- Cell Temperature Monitoring
- SOC Estimation
- SOH Estimation
- Cell Imbalance Detection
- Passive Cell Balancing
- Battery Protection
- Fault Code Generation
- Fault Action Management
- BMS State Machine
- Precharge Control
- Main Contactor Control
- Contactor Fault Diagnostics
- BMS Monitoring Dashboard

# Key Features

# Battery Monitoring
The system monitors:
- Individual cell voltages
- Pack voltage
- Pack current
- Individual cell temperatures
- Maximum/minimum cell voltage
- Cell voltage difference
- Maximum cell temperature
- SOC
- SOH

# Protection
The protection system detects:
| Fault                     | Code |
| ------------------------- | ---: |
| Cell Over-Voltage         |    1 |
| Cell Under-Voltage        |    2 |
| Over-Current              |    4 |
| Over-Temperature          |    8 |
| Under-Temperature         |   16 |
| Cell Imbalance            |   32 |
| Low SOC                   |   64 |
| Severe Protection Fault   |  128 |
| Main Contactor Fault      |  256 |
| Precharge Contactor Fault |  512 |

Fault codes are represented using bitwise encoding, allowing multiple simultaneous faults to be represented within a single diagnostic value.

# Cell Balancing
The controller:
- Identifies the highest-voltage cell
- Activates its balancing path
- Uses voltage hysteresis to prevent chattering
- Maintains minimum ON/OFF timing
- Stops balancing once the cell voltage difference falls below the defined threshold

# BMS State Machine
The BMS operates through defined operating states:
 OFF
 ↓
 INITIALIZE
 ↓
 PRECHARGE
 ↓
 IDLE
 ├──→ CHARGING
 └──→ DISCHARGING
 FAULT

The state machine controls:
- Main contactor
- Precharge contactor
- Charge enable
- Discharge enable
- Fault response

# Precharge System
A DC-link precharge circuit is implemented using:
- Precharge resistor
- Precharge contactor
- Main contactor
- DC-link capacitor
- Pack voltage measurement
- DC-link voltage measurement
Precharge completion is determined using:
VDC ≥ 0.95 × VPACK
A timeout mechanism is also implemented to prevent the system from remaining indefinitely in the PRECHARGE state.

# Fault Management
Fault conditions are classified according to severity.
-0 → Normal
-1 → Warning
-2 → Disable Charging
-3 → Disable Discharging
-4 → Critical / Isolate Battery
Critical faults cause the contactors to open and isolate the battery.
