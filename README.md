# Smart Irrigation

> **PLC-based irrigation control system with an embedded OPC UA server for real-time industrial monitoring and control.**

![CODESYS](https://img.shields.io/badge/CODESYS-V3.5_SP22-blue)
![IEC61131-3](https://img.shields.io/badge/IEC_61131--3-Structured_Text-success)
![OPC UA](https://img.shields.io/badge/OPC_UA-IEC_62541-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## Overview

Smart Irrigation is an industrial automation project developed with **CODESYS V3.5** using **Structured Text (IEC 61131-3)**.

The system simulates an automated irrigation process supplied by two independent water sources:

- a rainwater storage tank,
- a municipal water supply.

A built-in **OPC UA Server** exposes process variables, allowing external OPC UA clients such as **UaExpert** to monitor and control the system in real time.

---

## Features

- PLC application developed in Structured Text (IEC 61131-3)
- Automatic and manual irrigation modes
- Automatic switching between rainwater tank and municipal water
- Water level monitoring
- Total water consumption measurement
- Embedded OPC UA Server
- Real-time monitoring using UaExpert
- Secure OPC UA client/server communication

---

# System Architecture

<p align="center">
<img src="docs/architecture/system_architecture.png" width="800">
</p>

---

## Process Logic

The irrigation process follows a simple priority rule.

1. The rainwater tank is used as the primary water source.
2. As long as water is available, the pump supplies the irrigation system.
3. When the tank becomes empty, the PLC automatically switches to the municipal water supply by opening the valve.
4. Both automatic and manual irrigation modes are supported.

---

# HMI Visualization

<p align="center">
<img src="docs/screenshots/visualization.png" width="850">
</p>

The HMI allows the operator to

- start or stop the system,
- enable automatic mode,
- trigger manual irrigation,
- simulate rainfall,
- monitor the tank level,
- observe the current state of the pump and valve.

---

# OPC UA Monitoring

<p align="center">
<img src="docs/screenshots/uaexpert.png" width="900">
</p>

The embedded OPC UA Server exposes the PLC variables to external clients.

The screenshots above show the monitored process using **UaExpert**.

---

# OPC UA Information Model

| Variable | Type | Access | Description |
|-----------|------|:------:|-------------|
| EIN | BOOL | RW | Main system power |
| AutoEin | BOOL | RW | Enable automatic mode |
| ManuelTaste | BOOL | RW | Start manual irrigation |
| Level | REAL | R | Current tank level (L) |
| Pumpe | BOOL | R | Pump status |
| Ventil | BOOL | R | Water valve status |
| Verbrauch | REAL | R | Total water consumption (L) |

---

# Project Structure

```text
SmartIrrigation/
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

# Technologies

- CODESYS V3.5 SP22
- IEC 61131-3
- Structured Text (ST)
- OPC UA (IEC 62541)
- UaExpert

---

# Getting Started

1. Open the CODESYS project located in `plc_server/`.
2. Download the application to the local PLC runtime.
3. Start the PLC in **RUN** mode.
4. Open the UaExpert project from `plc_client/`.
5. Connect to the embedded OPC UA Server.
6. Browse and monitor the exposed process variables.

---

# Future Improvements

- OPC UA Methods
- Alarm & Event support
- Historical data logging
- MQTT integration
- Node-RED dashboard
- Sparkplug B integration

---

## License

This project is released under the MIT License.