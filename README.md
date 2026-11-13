# USB-HUB
USB-C PD USB 3.0 Hub

A compact USB 3.0 hub based on the TUSB8041 hub controller with USB-C Power Delivery, SD/microSD support, and per-port power protection.
I made this porject to make use of the empty USB-C 3.0 port on my laptop, and since my laptop does not have a SD reader, this hub would be useful.
Features
2× USB 3.0 Type-A ports
SD card reader
microSD card reader
USB-C upstream connection
USB Power Delivery (UPD350A)
USB-C orientation detection and lane switching
Per-port overcurrent protection
USB 3.0 SuperSpeed (5 Gbps)
# Architecture:
USB-C
│
UPD350A (PD Controller)
│
HD3SS3212 (USB-C Lane Mux)
│
TUSB8041 (USB 3.0 Hub)
├── USB 3.0 Port #1
├── USB 3.0 Port #2
├── GL823K SD Reader
└── GL823K microSD Reader
<img width="1327" height="831" alt="Screenshot 2026-09-07 213716" src="https://github.com/user-attachments/assets/291b7d56-cf7e-417a-8313-7645015c4b22" />

# Power System:
USB-C PD input (5–20V)
Buck converter → 5V rail
Buck converter → 3.3V rail
Buck converter → 1.8V rail
LDO → 1.1V rail (TUSB8041 core)
Protection
TPS2553 on each downstream USB port
900 mA current limit per port
Overcurrent fault reporting to TUSB8041
<img width="1312" height="682" alt="image" src="https://github.com/user-attachments/assets/a7f74a5e-d0e8-414c-b5ea-582ced969ca2" />

# Key Components:
Component	PurposeTUSB8041	USB 3.0 Hub Controller
UPD350A	USB-C PD & Orientation Detection
HD3SS3212	SuperSpeed Lane Multiplexer
TPS2553	Port Power Protection
GL823K	USB-to-SD Bridge
<img width="736" height="422" alt="image" src="https://github.com/user-attachments/assets/f3779cd3-a810-4452-aa48-86907d8c4b45" />

# Design Notes:
USB 3.0 differential pairs routed at 90 Ω differential impedance.
HD3SS3212 SEL pin driven by UPD350A orientation output.
TUSB8041 configured for individual port power control.
External 24 MHz crystal used for hub clock generation.
<img width="662" height="417" alt="image" src="https://github.com/user-attachments/assets/e93eb163-81ff-4733-85d3-b28cbdea1385" />


