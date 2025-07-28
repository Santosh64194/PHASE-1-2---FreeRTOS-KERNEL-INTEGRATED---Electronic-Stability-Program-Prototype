# Phase 1 & 2 – FreeRTOS Kernel Integrated Electronic Stability Program Prototype

A real-time, safety-critical embedded prototype developed using:

- **STM32F446RE Nucleo Board** (chosen for its MPU support)
- **FreeRTOS (MPU-enabled)**
- **MPU6050 Gyroscope Sensor**
- **I2C Sensor Interface**

---

## Phase 1 – Bare-Metal Implementation

In this phase, we implemented core functionality for the Electronic Stability Program using bare-metal programming with STM32 HAL drivers. The application involved three key components:

- **mpu_int()** – Initializes the MPU6050 sensor  
- **mpuread()** – Continuously reads yaw rate (gyro Z-axis) values and stores them in a global variable `yaw_dps`  
- **controlunit()** – Reads `yaw_dps`, checks thresholds, and controls GPIOs (e.g., LEDs) for visual feedback  
- **loggertask()** – Reads the shared `yaw_dps` value for monitoring/logging purposes  

These were implemented in a `task1.c` source file using STM32CubeIDE and HAL libraries.

---

## Phase 2 – FreeRTOS Kernel Integration

After verifying bare-metal functionality, we migrated to a **FreeRTOS-based multithreaded application**, enabling real-time task scheduling and memory protection in later phases.

### Tasks Created

- **Task 1 – `mpu_int()`**  
  - One-time initialization task  
  - Deleted after setup using `vTaskDelete()` and `vTaskDelay()`

- **Task 2 – `mpuread()`**  
  - Real-time data acquisition from the MPU6050 gyroscope  
  - Stores yaw rate in shared global variable

- **Task 3 – `controlunit()`**  
  - Reads shared data and activates GPIOs based on control logic

- **Task 4 – `loggertask()`**  
  - Reads and logs yaw rate data for monitoring

---

## Features

- Real-time yaw rate sensing using MPU6050
- Understeering detection
- LED-based visual indication system
- Modular FreeRTOS-based architecture for safety-critical applications

---

## Tools Used

- **STM32CubeIDE** – Development and debugging
- **GitHub** – Version control and documentation

---

