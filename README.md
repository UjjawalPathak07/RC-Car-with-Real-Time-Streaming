# RC-Car-with-Real-Time-Streaming
An intelligent car-mounted camera system designed for real-time road monitoring, image/video processing, and object detection to improve vehicle awareness and safety.

## Features
* **Real-Time Video Streaming:** Live video stream hosted via a local web server on the ESP32-CAM[cite: 1].
* **Wireless Motor Control:** Movement controlled via an HC-05 Bluetooth module[cite: 1].
* **Dual Microcontroller System:** Offloads video streaming to the ESP32-CAM while preserving Arduino Uno pins for motor logic[cite: 1].
* **Low-Cost Architecture:** Built entirely using off-the-shelf components and open-source software[cite: 1].

---

## Hardware Components
* **Arduino Uno R3** (ATmega328P microcontroller)[cite: 1]
* **ESP32-CAM Module** (OV2640 camera sensor)[cite: 1]
* **L298N Dual H-Bridge Motor Driver Module**[cite: 1]
* **HC-05 Bluetooth Module**[cite: 1]
* **FTDI USB-to-Serial Adapter** (for ESP32-CAM flashing)[cite: 1]
* **4x DC Gear Motors & Wheels** (6V–12V, 100–150 RPM)[cite: 1]
* **Power Supply:** Rechargeable Battery Pack[cite: 1]
* Chassis Frame, Breadboard, and Jumper Wires[cite: 1]

---

## Software & Tools
* **IDE:** Arduino IDE[cite: 1]
* **Languages:** C++[cite: 1]
* **Libraries:** `BluetoothSerial`, `esp_camera`, `WiFi`

---

## System Architecture & Circuit Workflow

1. **Movement Control:**  
   The user sends control signals (Forward, Backward, Left, Right, Stop) via a smartphone Bluetooth serial app[cite: 1]. The **HC-05 module** receives these commands and forwards them via UART serial interface to the **Arduino Uno**[cite: 1]. The Arduino parses the input and drives the **L298N motor driver** pins to operate the DC motors[cite: 1].

2. **Video Stream:**  
   The **ESP32-CAM** connects to a local Wi-Fi network (or acts as an Access Point) and initializes an HTTP web server[cite: 1]. Users access the video stream directly by entering the assigned IP address into any standard web browser on a laptop or smartphone[cite: 1].

---

## Setup & Installation

### 1. Circuit Connections

* **L298N to Arduino Uno:**
  * Motor control pins connected to Arduino digital output pins[cite: 1].
  * Power inputs connected to the external battery pack[cite: 1].
* **HC-05 to Arduino Uno:**
  * TX pin to Arduino RX[cite: 1].
  * RX pin to Arduino TX[cite: 1].
* **ESP32-CAM:**
  * Powered via the battery pack regulated 5V output[cite: 1].
  * Flashed using an FTDI USB-to-Serial programmer[cite: 1].

---

### 2. Flashing the ESP32-CAM

1. Connect the ESP32-CAM to your computer using the **FTDI adapter**[cite: 1].
2. Connect **GPIO 0** to **GND** on the ESP32-CAM to put it into flashing mode.
3. In **Arduino IDE**, select `ESP32 Wrover Module` under **Tools > Board**.
4. Open the Camera Web Server example sketch, enter your Wi-Fi SSID and password, and click **Upload**.
5. Once uploaded, disconnect GPIO 0 from GND and power cycle the module.
6. Open the Serial Monitor to retrieve the assigned IP address[cite: 1].

---

### 3. Uploading Code to Arduino Uno

1. Connect the Arduino Uno to your PC via USB[cite: 1].
2. Upload the motor control script handling UART serial inputs from the HC-05 module[cite: 1].

---

## How to Run

1. Power on the vehicle via the battery pack[cite: 1].
2. Pair your mobile device to the **HC-05 Bluetooth module**[cite: 1].
3. Open a Bluetooth Serial Controller app and send direction keys to move the car[cite: 1].
4. Connect to the same Wi-Fi network as the ESP32-CAM, open a web browser, and navigate to `http://<ESP32-CAM-IP>` to view the live video feed[cite: 1].

---
