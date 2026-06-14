# Vehicle Dashboard Using CAN Protocol

## Overview
This project implements a distributed Vehicle Dashboard System using the CAN (Controller Area Network) protocol with three LPC2129 microcontroller nodes. The system monitors temperature and fuel level and displays the information on a central dashboard.

## Features
- Multi-node communication using CAN protocol
- Temperature monitoring using LM35 sensor
- Fuel level monitoring using a fuel sensor/potentiometer
- External ADC interfacing using MCP3204 through SPI
- LCD display for real-time data visualization
- Motor control based on temperature
- Low fuel warning using LED indication

## System Architecture

Dashboard Node (Node 1)
- LCD Display
- Motor Control
- LED Indicator
- Push Buttons

Temperature Node (Node 2)
- LM35 Temperature Sensor
- MCP3204 ADC
- CAN Communication

Fuel Node (Node 3)
- Fuel Sensor/Potentiometer
- MCP3204 ADC
- CAN Communication

All three nodes communicate through a CAN bus.

## Hardware Components
- LPC2129 Microcontrollers (3)
- MCP3204 12-bit ADC (2)
- LM35 Temperature Sensor
- Fuel Sensor/Potentiometer
- CAN Transceivers (MCP2551)
- 16×2 LCD
- DC Motor
- LED
- Push Buttons
- Power Supply

## Software Used
- Embedded C
- Keil uVision
- Flash Magic

## Communication Protocols

### CAN Protocol
Used for communication between the dashboard, temperature, and fuel nodes.

CAN IDs:
- `0x101` → Temperature Node
- `0x102` → Fuel Node

### SPI Protocol
Used to interface the MCP3204 ADC with LPC2129.

SPI Pins:
- P0.4 → SCK
- P0.5 → MISO
- P0.6 → MOSI
- P0.7 → CS

## Working Principle

### Temperature Monitoring
1. Dashboard sends an RTR frame with CAN ID `0x101`.
2. Temperature Node reads LM35 through MCP3204.
3. Temperature value is transmitted back to the Dashboard.
4. LCD displays the temperature.
5. Motor turns ON if temperature exceeds 25°C.

### Fuel Monitoring
1. Dashboard sends an RTR frame with CAN ID `0x102`.
2. Fuel Node reads fuel sensor voltage using MCP3204.
3. Fuel data is transmitted back to the Dashboard.
4. LCD displays fuel status and voltage.
5. LED indicates low fuel condition.

## Project Flow

LM35/Fuel Sensor
↓
MCP3204 ADC
↓ SPI
LPC2129 Sensor Node
↓ CAN
Dashboard Node
↓
LCD / Motor / LED

## Results
- Successfully established CAN communication between three nodes.
- Displayed temperature and fuel information on LCD.
- Implemented motor control based on temperature threshold.
- Implemented low fuel warning indication.

## Learning Outcomes
- CAN protocol implementation
- SPI interfacing
- External ADC integration
- Sensor interfacing
- LCD interfacing
- Embedded C programming
- Distributed embedded system design

## Future Enhancements
- Speed and RPM monitoring
- Real fuel sensor integration
- Fault diagnostics using CAN
- Interrupt-based CAN communication
- Data logging and wireless monitoring

## Author
**Ramya M**

Electronics and Communication Engineering (ECE)

Embedded Systems Enthusiast
