# Energy Monitoring System with Modbus-to-MQTT Bridge (Internet Of Things)

## Project Description

An Arduino-based solution that acts as a Modbus RTU to MQTT bridge for a Finder Energy Meter. The primary goal is to enable real-time monitoring of electricity costs and usage. The system utilizes RS485 Half Duplex communication at a baud rate of 9600 and is specifically designed for the Arduino MKR WIFI1010 with the MKR 485 Shield.

## Hardware Requirements

- **Arduino MKR WIFI1010:** The main controller that provides the necessary processing power and WiFi connectivity.
- **Arduino MKR 485 Shield:** Facilitates communication with the Finder Energy Meter using the RS485 Half Duplex protocol.
- **Finder 7E.64.8.230.0210 Energy Meter:** The device being monitored.

## Protocols Utilized

- **Modbus RTU:** A widely used serial communication protocol for industrial applications, used here for communication with the Finder Energy Meter.
- **MQTT (Message Queuing Telemetry Transport):** A lightweight and efficient messaging protocol, employed for transmitting energy-related data in real-time.

## Setup

1. **Configure WiFi:**
   - Set your WiFi credentials (SSID and password) in the sketch to enable the Arduino MKR WIFI1010 to connect to the local network.

2. **Configure MQTT:**
   - Provide the broker's IP address, device name, username, and password in the sketch to establish communication with the MQTT broker.

3. **Set Modbus Parameters:**
   - Adjust the Modbus RTU settings, including the baud rate, to match the specifications of your Finder Energy Meter.

## Working Principle

1. **Initialization:**
   - The Arduino MKR WIFI1010 establishes a WiFi connection and initializes the Modbus RTU client for communication with the Finder Energy Meter.

2. **MQTT Connection:**
   - The system connects to the MQTT broker, subscribing to the topic "energy/main/refreshrate" for remotely setting the refresh rate.

3. **Data Retrieval:**
   - At regular intervals, the system queries the Finder Energy Meter using Modbus RTU to obtain voltage, current, power, frequency, and energy values.

4. **MQTT Publication:**
   - The acquired data is published to specific MQTT topics, making it accessible for remote monitoring.

5. **Remote Configuration:**
   - The system listens for MQTT messages, allowing remote adjustments to the refresh rate via the "energy/main/refreshrate" topic.

6. **Serial Monitoring:**
   - The serial interface provides real-time feedback and status messages, aiding in system monitoring and debugging.

## Notes and Customization

- Replace placeholder values in the sketch (e.g., "**********", "broker_ip", "device_name", "user_name", "user_pw") with your actual configuration.
- Customize Modbus register addresses based on your Finder Energy Meter's protocol by referring to the provided Modbus protocol manual.

