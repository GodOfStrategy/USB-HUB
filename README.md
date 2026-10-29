# USB-HUB
USB-C PD USB 3.0 Hub

A compact USB 3.0 hub based on the TUSB8041 hub controller with USB-C Power Delivery, SD/microSD support, and per-port power protection.

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
# Key Components:
Component	PurposeTUSB8041	USB 3.0 Hub Controller
UPD350A	USB-C PD & Orientation Detection
HD3SS3212	SuperSpeed Lane Multiplexer
TPS2553	Port Power Protection
GL823K	USB-to-SD Bridge
# Design Notes:
USB 3.0 differential pairs routed at 90 Ω differential impedance.
HD3SS3212 SEL pin driven by UPD350A orientation output.
TUSB8041 configured for individual port power control.
External 24 MHz crystal used for hub clock generation.
