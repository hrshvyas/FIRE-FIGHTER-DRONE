# FIRE-FIGHTER-DRONE
Interdisciplinary Project at College level.
This project demonstrates a Firefighter Drone designed using affordable components and open-source hardware. The primary goal is to build a drone capable of remote-controlled movement and orientation stabilization for fire detection and response in small-scale indoor or test environments. Communication between ground control and the drone is achieved via NRF24L01 2.4GHz wireless transceivers, while the MPU6050 sensor provides real-time orientation data for balance and stabilization.

## benefits of a Firefighter Drone project:
 1. Enhanced Safety
Reduces human risk by keeping firefighters away from dangerous areas (e.g., high-rise fires, chemical zones).
Can access hard-to-reach or toxic environments without endangering lives.
2. Faster Response Time
Drones can be deployed immediately to survey and act in fire zones.
Real-time thermal imaging helps identify fire hotspots quickly.
3. Intelligent Fire Detection
Uses thermal sensors to detect fire early—even through smoke.
Capable of data-driven decision-making for resource allocation.
4. Remote Fire Suppression
Can extinguish small fires using fire-retardant payloads or sprinklers.
Controlled remotely or autonomously, reducing manual intervention.
5. Cost Efficiency
Lower operational cost compared to helicopters or large firefighting units.
Minimizes property damage by early intervention.
6. Scalability & Upgradability
Can be upgraded with AI, GPS, automated flight control, and computer vision for smart operations.
Useful for urban, forest, and industrial fire scenarios.

## Hardware Components
1.Arduino Uno	1	Main flight controller of the drone 
2.Arduino Nano	2	One for transmitter (remote controller), one for onboard receiver system
3.NRF24L01 Module	2	2.4GHz transceiver modules for wireless communication
4.MPU6050	1	6-axis gyroscope and accelerometer for orientation control
5.ESCs + Brushless Motors	4	For quadcopter movement and control
6'Li-Po Battery	1	Power source for motors and electronics
7.Propellers	4	For drone lift and maneuvering
8.Flame Sensor (optional)	1+	To detect fire/heat sources
9.Frame	1	Lightweight frame to mount all components

## System Architecture
1. Drone Side (Receiver + Flight Control)
Arduino Uno receives flight control signals from the NRF24L01 module.
MPU6050 feeds gyro and accelerometer data to Uno for orientation awareness.
Based on both the received commands and stabilization logic, PWM signals are sent to ESCs to control motors.
Optionally, a flame sensor can be attached to detect fire locations.

2. Remote Controller Side (Transmitter)
An Arduino Nano reads analog inputs (e.g., joystick, potentiometers) for controlling pitch, roll, throttle, and yaw.
These values are transmitted wirelessly to the drone via NRF24L01.

3. Communication Protocol
Uses RF24 library for communication between the two NRF24L01 modules.
Simple data packet structure carrying throttle, yaw, pitch, and roll values.
Additional channels can be used for activating fire-extinguishing features or reading flame sensors.

## Data Flow Summary
sql
[ Transmitter Arduino Nano ]
  -> Reads joystick inputs
  -> Encodes and transmits data via NRF24L01
      ↓
[ Drone Arduino Uno + Nano ]
  <- Receives data via NRF24L01
  <- Reads MPU6050 data for real-time orientation
  -> Controls ESCs based on combined input and sensor feedback
  -> Flame sensor can trigger alert or extinguishing system
  
## Software & Libraries Used
Arduino IDE
RF24 – for NRF24L01 communication
Wire.h – for I2C communication with MPU6050
MPU6050.h – for accessing gyroscope and accelerometer data
Servo.h or custom PWM control – for ESCs

## Features
1. 2.4GHz Wireless Remote Control
2. Gyroscope-Based Stability Control
3. Flame Detection Capability
4. Quadcopter-Style Movement
5. Basic failsafe handling

## Future Enhancements
Add PID controller for better stabilization.
Mount a small CO2 extinguisher and servo-triggered release mechanism.
Add a camera module for FPV monitoring.
GPS module for autonomous navigation and return-to-home function.


## Authors & Credits
Developed by: [Harshwardhan Patil]
Inspired by open-source drone communities and educational robotics projects.
