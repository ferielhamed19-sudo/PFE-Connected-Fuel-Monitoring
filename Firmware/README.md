# Firmware

## Overview

This firmware powers an embedded fuel monitoring, vehicle diagnostic, and fleet tracking system.

It acquires real-time data from local sensors and the vehicle's CAN/J1939 bus, processes the information locally to evaluate driver behavior and detect anomalies such as abnormal fuel variations, and transmits packaged data through a cellular communication module.

## Hardware Platform

- **Microcontroller:** STM32F407VGTX (ARM Cortex-M4)
- **Development Environment:** STM32CubeIDE
- **Software Framework:** STM32 HAL
- **Operating System:** FreeRTOS

## Software Architecture

The firmware is based on a concurrent FreeRTOS architecture.

Mutexes and message queues are used to support thread-safe communication and data exchange between acquisition, processing, logging, debugging, and communication tasks.

## FreeRTOS Tasks

- **`CAN_J1939_Task`** *(High Priority)*  
  Continuously monitors the CAN bus and extracts SAE J1939 vehicle parameters and Diagnostic Trouble Codes (DTCs).

- **`Task_Sensors`** *(Normal Priority)*  
  Acquires data from the ultrasonic sensor, MPU6050, DS18B20, battery voltage circuit, and water detector. Digital filtering is applied to selected measurements.

- **`Task_Logger`** *(Normal Priority)*  
  Manages data persistence and stores configuration and telemetry records in the STM32 internal Flash memory.

- **`Task_Comm`** *(Normal Priority)*  
  Packages processed data into JSON payloads and manages communication through the GSM/GPRS module.

- **`Task_Debug`** *(Low Priority)*  
  Handles debugging and logging through SWV and UART without blocking critical system operations.

- **`defaultTask`**  
  Handles basic system operations, including refreshing the Independent Watchdog (IWDG).

## Hardware Interfaces

- **CAN:** SAE J1939 vehicle communication
- **UART / USART:** GSM/GPRS communication and serial debugging
- **I2C:** Communication with the MPU6050 IMU
- **ADC:** Battery voltage measurement
- **Timer Input Capture:** Ultrasonic echo pulse measurement
- **One-Wire:** DS18B20 temperature sensor communication
- **GPIO:** Sensor triggering and water detection

## Sensors and External Modules

- **SIM808:** GSM/GPRS communication module
- **MPU6050:** 6-axis accelerometer and gyroscope
- **Ultrasonic Sensor:** Fuel level distance measurement
- **DS18B20:** Digital temperature sensor
- **Battery Voltage Circuit:** Analog voltage measurement using a voltage divider
- **Water Detector:** Detection of water presence

## Main Functionalities

- Fuel level monitoring
- Detection of abnormal fuel variations
- CAN/J1939 vehicle diagnostics
- Vehicle parameter monitoring
- Diagnostic Trouble Code (DTC) processing
- Driver behavior analysis
- Eco-driving analysis
- Anti-sabotage monitoring
- Remote telemetry transmission
- Sensor health monitoring

## Data Processing

The firmware implements digital signal processing techniques to improve measurement reliability.

- **Moving Average Filter:** Reduces measurement noise
- **Median Filter:** Removes abnormal measurement spikes
- **Fuel Analytics:** Processes fuel level variations
- **Flash Storage Management:** Stores non-volatile configuration and telemetry data

Flash storage mechanisms include data integrity verification and recovery mechanisms to improve reliability.

## Communication

Telemetry, diagnostic information, and alerts are structured into JSON payloads.

The processed data is transmitted to the cellular communication module through UART for remote communication.

## Reliability and Error Handling

The firmware includes several mechanisms to improve system reliability:

- **Independent Watchdog (IWDG):** Helps recover the system from software freezes or task lockups
- **Sensor Health Monitoring:** Tracks sensor status and detects failures or disconnections
- **Flash Data Integrity:** Uses validation mechanisms to detect corrupted data and recover default configurations when required

## Confidentiality

The complete firmware source code is not publicly available due to project confidentiality.

This public repository presents the firmware architecture, technologies, hardware interfaces, and main engineering concepts without exposing sensitive source code, credentials, proprietary algorithms, or company-specific information.
