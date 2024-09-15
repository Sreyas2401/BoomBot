# BOOMBOT (CS256 Make Final Project)

This project uses an ESP32 microcontroller to control a robot via Bluetooth. The robot can move forward, turn right, and stop based on distance measurements from an ultrasonic sensor and commands received over Bluetooth.

[BOOMBOT](https://sites.google.com/umass.edu/boombot/)

## Features

### Bluetooth Control
The robot is controlled using Bluetooth commands. It pairs with a device and responds to commands to move forward or stop.

### Ultrasonic Sensor
An HC-SR04 ultrasonic sensor measures the distance to obstacles and helps the robot avoid collisions.

### Motor Control
The robot uses four motor pins to control movement, including forward and reverse motion for both left and right motors.

### Vacuum Motor
A vacuum motor can be activated to simulate some additional functionality.

## Hardware Components

1. **ESP32 Microcontroller**: The main controller for the robot.
2. **HC-SR04 Ultrasonic Sensor**: For measuring distance to obstacles.
3. **DC Motors**: For robot movement.
4. **Motor Driver**: For controlling motor direction and speed.
5. **Vacuum Motor**: An additional motor for extra functionality.

## Pin Configuration

1. **Trig Pin**: GPIO 19 (Used to send a pulse to the ultrasonic sensor)
2. **Echo Pin**: GPIO 18 (Receives the reflected pulse from the ultrasonic sensor)
3. **Left Motor**:
    - Forward: GPIO 23
    - Reverse: GPIO 22
4. **Right Motor**:
    - Forward: GPIO 33
    - Reverse: GPIO 32
5. **Vacuum Motor**: GPIO 2
6. **Enabler Pins**:
    - A: GPIO 12
    - B: GPIO 14

## Setup

1. **Install the Required Library**: Make sure you have the `BluetoothSerial` library installed in your Arduino IDE.
2. **Configure Bluetooth**:
    - You can set a PIN for Bluetooth pairing by defining `USE_PIN` and setting the desired PIN.
3. **Upload Code**:
    - Connect your ESP32 to your computer.
    - Upload the code to your ESP32 using the Arduino IDE.
4. **Pair with Bluetooth Device**:
    - After uploading, your ESP32 will start advertising with the name `ESP32-BT-Slave`.
    - Pair with the ESP32 from your Bluetooth device.

## Usage

- **Move Forward**: Send the command `'1'` via Bluetooth to make the robot move forward.
- **Stop**: Send the command `'0'` to stop the robot.

The robot will measure distances using the ultrasonic sensor and automatically avoid obstacles by turning right if it detects an obstacle within 15 cm.

## Functions

- `moveForward()`: Moves the robot forward and activates the vacuum motor.
- `turnRight()`: Turns the robot 90 degrees to the right and then stops.
- `brake()`: Stops all motors.
- `sort()`: Sorts an array of distance measurements.
- `getMedian()`: Calculates the median distance from the distance measurements.

## Notes

- Ensure that the motor driver and other hardware components are correctly connected according to the pin configuration.
- Adjust the delay in the `turnRight()` function based on your robot’s turning speed and angle requirements.
