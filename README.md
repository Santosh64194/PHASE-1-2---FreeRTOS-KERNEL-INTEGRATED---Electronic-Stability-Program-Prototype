# Electronic Stability Program Prototype 🚗

A real-time safety-critical ADAS prototype built using:
- **STM32F446RE Nucleo**
- **FreeRTOS (MPU-enabled)**
- **MPU6050 Gyroscope**
- **I2C Sensor Interface**
- **Task-based memory protection**

## Features
- Reads yaw rate via MPU6050
- Detects understeering/oversteering
- Triggers LEDs for visual feedback
- Demonstrates FreeRTOS MPU for safety

## Tools Used
- STM32CubeIDE
- SEGGER SystemView (optional)
- GitHub for version control

## Getting Started
1. Clone this repo
2. Open `.ioc` file with STM32CubeIDE
3. Build and flash to Nucleo-F446RE
