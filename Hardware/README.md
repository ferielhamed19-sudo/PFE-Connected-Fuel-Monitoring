# Hardware

## Overview

This documentation presents the hardware architecture of an embedded IoT edge computing system designed for vehicle monitoring.

The system interfaces directly with the vehicle's CAN bus, local sensors, and a cellular communication module. A backup power management system supports continued operation when the main power source is unavailable.

## System Architecture

The hardware architecture is centered around an STM32 microcontroller responsible for sensor data acquisition, vehicle communication, and peripheral management.

Data is collected from local sensors and the vehicle communication network, processed by the embedded firmware, and transmitted remotely through a cellular communication module.

## Microcontroller

- **MCU:** STM32F407VGTX
- **Architecture:** ARM Cortex-M4 (32-bit) with Floating-Point Unit (FPU)
- **Function:** Central processing unit responsible for executing the embedded firmware and managing CAN, UART, I2C, 1-Wire, ADC, and timer peripherals.

## Power Supply and Backup System

The system includes a power management architecture with a backup battery.

- **Main Input:** Vehicle power input stepped down to 5.0V through a Buck converter.
- **Backup Power:** 3.7V–4.2V LiPo battery managed by a TP4056 charge controller.

### Voltage Rails

- **LiPo Direct (3.7V–4.2V):** Powers the SIM808 module.
- **5.0V Rail:** A Boost converter provides power for the ultrasonic sensor.
- **3.3V Rail:** An LDO regulator provides power for the STM32 and 3.3V logic.

### Battery Monitoring

The LiPo battery voltage is scaled using a 10kΩ/10kΩ voltage divider and monitored by the STM32 through:

**PC5 (ADC1_IN15)**

## Sensors

### US-100 Ultrasonic Sensor

Used for fuel level distance measurement.

The sensor operates in **Trigger/Echo mode**:

- **TRIG:** PA0
- **ECHO:** PA1

### DS18B20 Digital Temperature Sensor

Measures ambient temperature.

The temperature measurement is used to compensate for variations in the speed of sound during ultrasonic distance measurement.

### MPU6050 IMU

A 6-axis accelerometer and gyroscope used for:

- Vehicle tilt monitoring
- Fuel level correction
- Acceleration monitoring
  
### Water Detection Sensor

A dedicated water detection circuit is used to detect the presence of water in the fuel tank.

This functionality helps identify potential fuel contamination and can trigger an alert when water is detected.

## Communication Module

### SIM808

The SIM808 module provides:

- **GSM/GPRS:** Remote telemetry transmission through TCP/MQTT
- **GPS:** Vehicle position and speed acquisition

## Vehicle Communication

### Direct CAN / SAE J1939 Interface

The STM32 native CAN peripheral communicates directly with the vehicle network.

The system processes SAE J1939 vehicle data and Diagnostic Trouble Codes (DTCs).

## Hardware Interfaces

The STM32 uses several interfaces:

- **CAN:** SAE J1939 vehicle communication
- **UART:** SIM808 communication and serial debugging
- **I2C (400kHz):** MPU6050 communication
- **Timer Input Capture:** Ultrasonic echo pulse measurement
- **1-Wire:** DS18B20 temperature sensor communication
- **ADC:** Backup battery voltage monitoring through PC5

## Data Processing Support

The embedded system uses digital filtering to improve measurement stability.

- **Moving Average Filter:** Reduces measurement noise
- **Median Filter:** Removes abnormal measurement spikes

These filters are applied to improve the reliability of ultrasonic fuel level measurements.

## PCB Design

- **EDA Tool:** Altium Designer

The public repository presents the high-level hardware architecture without exposing proprietary schematic or manufacturing files.

## Confidentiality

This repository provides high-level hardware documentation for portfolio and educational purposes.

The following information is intentionally excluded:

- Proprietary schematic source files
- PCB manufacturing files
- Gerber files
- Sensitive communication credentials
- Server configurations
- Proprietary algorithm parameters
