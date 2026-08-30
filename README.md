# Connected Fuel Monitoring and Vehicle Diagnostic System

## Overview

This project presents the design and development of a connected fuel monitoring and vehicle diagnostic system for heavy-duty vehicles.

The system monitors fuel level and vehicle parameters in real time and transmits relevant data to a remote monitoring platform.

## Objectives

- Monitor fuel level in real time
- Detect abnormal fuel variations
- Monitor vehicle inclination
- Measure fuel temperature
- Read vehicle data through CAN/J1939
- Transmit data using IoT communication
- Provide remote monitoring and alerts

## System Architecture

The system is based on an STM32F407 microcontroller and integrates sensors, vehicle communication and IoT technologies.

STM32F407 → Sensors / CAN-J1939 → Data Processing → MQTT → Backend → Dashboard

## Technologies

- STM32F407
- Embedded C
- FreeRTOS
- CAN Bus
- J1939
- MQTT
- SIM808
- GPS/GPRS
- Node.js
- PostgreSQL
- WebSocket

## Hardware

- STM32F407
- US-100 ultrasonic sensor
- MPU6050
- DS18B20
- SIM808 GSM/GPRS/GPS module

## Features

- Fuel level monitoring
- Temperature compensation
- Vehicle inclination detection
- CAN/J1939 vehicle diagnostics
- GPS positioning
- MQTT communication
- Real-time monitoring

## Project Status

Completed as an engineering graduation project.

## Future Improvements

- Improve anomaly detection algorithms
- Add advanced diagnostics
- Improve offline data storage
- Develop predictive maintenance features

## Author

Feriel Hamed  
Junior Embedded Systems & IoT Engineer
