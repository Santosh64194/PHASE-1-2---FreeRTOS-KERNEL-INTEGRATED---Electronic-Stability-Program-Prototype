# PHASE 1,2 - FreeRTOS KERNEL INTEGRATED - Electronic Stability Program Prototype 

A real-time safety-critical prototype built using:
- **STM32F446RE Nucleo**
- **FreeRTOS (MPU-enabled)**
- **MPU6050 Gyroscope**
- **I2C Sensor Interface**

# Phase 1 - Bare metal program for the aforementioned units in STM32F446RE MCU 
STM32F446RE -chosen because of presence of MPU for later use 
We used HAL STM32 Library functions and implemented the functionality of the 3 units - created source file task1.c - defined 4 functions: 
 mpu_int() [innitialises the MPU6050 sensor]
 mpuread() -[continuously read real time yaw rate values - gyro values from the 16 bit GYRO_Z Register and store it in the shared resource GLOBAL varibale yaw_dps,
controlunit() -[To read the shared resouce yaw_dps and compare and GPIO control]
loggertask() - to simply read the global variable. 

# Phase 2 - FreeRTOS integration 
With the bare metal program done- we moved to the FreeRTOS KERNEL INTEGRATION for multithreading application. 
TASK 1 - One-time task - mpu_int()- immediately deleted after configuration using TASK DELETION API - vTaskDelay(). 
TASK2 - mpuread() - real time sensor data acquisition.
TASK3 - controlunit() 
TASK4 - loggertask() 

## Features
- Reads yaw rate via MPU6050
- Detects understeering
- Triggers LEDs for visual feedback

## Tools Used
- STM32CubeIDE
- SEGGER SystemView
- GitHub for version control

  


