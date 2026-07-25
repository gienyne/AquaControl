# AquaControl

> Industrial PLC application for smart irrigation with an embedded OPC UA Server for real-time monitoring and control.

![CODESYS](https://img.shields.io/badge/CODESYS-V3.5_SP22-blue)
![IEC 61131-3](https://img.shields.io/badge/IEC-61131--3-orange)
![OPC UA](https://img.shields.io/badge/OPC_UA-IEC_62541-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## Overview

AquaControl is an industrial automation project developed with **CODESYS V3.5 SP22**.

The application simulates an irrigation process supplied by two independent water sources: a rainwater storage tank and a municipal water supply. An embedded **OPC UA Server** exposes the PLC process variables, allowing external OPC UA clients such as **UaExpert** to monitor and control the process in real time.

The project demonstrates the implementation of PLC process logic, HMI visualization and OPC UA communication within a single industrial automation application.

---

## Key Features

- PLC application developed with CODESYS
- IEC 61131-3 based implementation
- Automatic and manual irrigation modes
- Automatic switching between water sources
- Continuous tank level simulation
- Water consumption monitoring
- Integrated HMI visualization
- Embedded OPC UA Server
- Certificate-based OPC UA communication
- Real-time monitoring using UaExpert

---

## System Architecture

<p align="center">
    <img src="docs/architecture/architecture.png" width="850">
</p>

The application consists of three main components:

- **PLC Application** implemented in CODESYS
- **Embedded OPC UA Server** exposing process variables
- **UaExpert OPC UA Client** for supervision and interaction

---

## Process Overview

The irrigation process is supplied by two water sources.

The rainwater tank is always used as the primary source. During irrigation, the PLC activates the pump to supply water from the tank.

Whenever the tank becomes empty, the controller automatically switches to the municipal water supply by opening the valve. This transition is performed without operator intervention.

The system supports both automatic and manual irrigation while continuously tracking the total water consumption.

---

## HMI Visualization

<p align="center">
    <img src="docs/screenshots/visualization.png" width="900">
</p>

The visualization allows the operator to

- start or stop the irrigation system;
- enable or disable automatic mode;
- trigger manual irrigation;
- simulate rainfall;
- monitor the tank level;
- observe the pump and valve states;
- monitor the accumulated water consumption.

---

## OPC UA Connectivity

<p align="center">
    <img src="docs/screenshots/uaexpert.png" width="900">
</p>

The embedded OPC UA Server exposes the PLC variables through its Address Space.

Using UaExpert, the client can

- browse the Address Space;
- read process variables;
- write control variables;
- monitor the process in real time.

---

## OPC UA Information Model

| Variable | Type | Access | Description |
|----------|------|:------:|-------------|
| `EIN` | BOOL | RW | Main system switch |
| `AutoEin` | BOOL | RW | Automatic mode |
| `ManuelTaste` | BOOL | RW | Manual irrigation |
| `Level` | REAL | R | Tank level |
| `Pumpe` | BOOL | R | Pump state |
| `Ventil` | BOOL | R | Valve state |
| `Verbrauch` | REAL | R | Total water consumption |

---

## Repository Structure

```text
AquaControl/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── plc_server/
│   └── SmartIrrigation.project
│
├── plc_client/
│   └── SmartIrrigation_UaExpert.uap
│
└── docs/
    ├── architecture/
    ├── diagrams/
    └── screenshots/
```

---

## Technologies

- CODESYS V3.5 SP22
- IEC 61131-3
- OPC UA (IEC 62541)
- UaExpert

---

## Getting Started

1. Open the CODESYS project located in `plc_server/`.
2. Download the application to the CODESYS Control Win runtime.
3. Start the PLC in **RUN** mode.
4. Open the UaExpert project from `plc_client/`.
5. Connect to the embedded OPC UA Server.
6. Browse the Address Space.
7. Read and write the exposed process variables.

---

## Future Improvements

- OPC UA Methods
- OPC UA Alarms & Events
- Historical Data Access
- MQTT Integration
- Node-RED Dashboard
- Sparkplug B Support

---

## License

Released under the MIT License.
