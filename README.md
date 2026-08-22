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

