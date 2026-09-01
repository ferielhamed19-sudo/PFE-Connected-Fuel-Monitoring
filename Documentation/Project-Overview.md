# Project Overview

## Title

Design and Implementation of a Connected Fuel Level Sensor for Vehicle Monitoring and Embedded Diagnostics

## Project Description

This project focuses on the development of an embedded system for fuel monitoring and vehicle diagnostics.

The system collects data from multiple sensors and the vehicle CAN network. The acquired information is processed by an STM32F407 microcontroller and transmitted remotely through a GSM/GPRS communication module.

## Main Objectives

- Monitor fuel level
- Detect abnormal fuel variations
- Monitor vehicle inclination
- Acquire vehicle diagnostic information through CAN/J1939
- Monitor system and backup battery status
- Acquire vehicle GPS information
- Transmit telemetry data remotely
- Improve measurement reliability using digital filtering

## Main Technologies

- STM32F407
- Embedded C
- FreeRTOS
- STM32 HAL
- CAN / SAE J1939
- MQTT
- GSM/GPRS
- GPS
- UART
- I2C
- ADC

## System Components

- STM32F407 microcontroller
- US-100 ultrasonic sensor
- MPU6050 IMU
- DS18B20 temperature sensor
- SIM808 communication module
- CAN/J1939 vehicle interface
- Backup battery system

## Repository Structure

- `Firmware/` — Firmware architecture and implementation overview
- `Hardware/` — Hardware architecture and PCB documentation
- `Documentation/` — Technical project documentation
- `Images/` — Project images and diagrams

## Confidentiality

Some source code, proprietary implementation details, and sensitive configuration information are not included in this public repository.
