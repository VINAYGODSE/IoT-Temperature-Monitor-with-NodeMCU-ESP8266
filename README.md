# IoT-Temperature-Monitor-with-NodeMCU-ESP8266
Build a system that uses a NodeMCU ESP8266 to read temperature from a sensor (e.g., DHT11) and send it to a serial monitor or a basic web server. This demonstrates embedded C programming, IoT communication, and real-time data handling—skills transferable to Zoho’s “high-volume, low-latency applications” requirement.


# IoT Temperature Monitor
A simple embedded systems project using NodeMCU ESP8266 and DHT11 sensor to monitor temperature and humidity in real-time.

## Features
- Reads temperature and humidity every 2 seconds.
- Outputs data to Serial Monitor.
- (Optional) Serves data via a web server over Wi-Fi.

## Hardware
- NodeMCU ESP8266
- DHT11 Sensor
- Breadboard, jumper wires

## Setup
1. Connect DHT11: VCC to 3.3V, GND to GND, Data to D4 (GPIO 2).
2. Install Arduino IDE and ESP8266 board support.
3. Add `DHT sensor library` via Library Manager.
4. Update Wi-Fi credentials in code (if using web server).
5. Upload code and open Serial Monitor (115200 baud).

## Circuit Diagram
![Circuit](circuit_diagram.png)
