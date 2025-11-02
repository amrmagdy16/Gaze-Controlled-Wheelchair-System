# ♿ Gaze-Controlled Wheelchair System (MediaPipe + ESP32 + MQTT)

## 🎯 Project Overview & Goal

This project implements a robust, real-time, hands-free control interface for a motorized vehicle or wheelchair, integrating high-level Computer Vision with low-level Embedded Systems and IoT communication.

The primary goal was to achieve reliable, low-latency device control with an unwavering focus on user safety.

### Key Features
* **Real-Time Gaze Tracking:** Implemented using **MediaPipe Face Landmarker** on a **Raspberry Pi**.
* **Low-Latency Control:** Utilizes the **MQTT protocol** for instant command delivery between the Pi and the ESP32.
* **Critical Safety Fail-Safe:** The ESP32 firmware includes a **1-second timeout** that immediately stops all motors if the signal is lost.
* **Hardware Flexibility:** Includes firmware for both **BTS7960** and **L298N-style** motor drivers.

## 📐 System Architecture

The control system operates as a clear three-part pipeline:
1.  **Vision Engine:** Raspberry Pi captures video and publishes direction (e.g., `LEFT`, `EYES_CLOSED`).
2.  **IoT Broker:** MQTT server (IP: `192.168.142.37`) routes the command on the `gaze/direction` topic.
3.  **Actuator:** ESP32 subscribes to the topic and drives the motors.

## ⚙️ Technology Stack

| Component | Hardware/Software | Language/Protocol |
| :--- | :--- | :--- |
| **Vision/Command** | Raspberry Pi / Picamera2 | Python (MediaPipe, paho-mqtt) |
| **Controller** | ESP32 Microcontroller | C++ (Arduino, PubSubClient) |
| **Motor Control** | BTS7960 / L298N-style Drivers | PWM Control |
| **Communication** | Wi-Fi Network | MQTT Protocol |

## 📁 Repository Structure

| Folder | Contents |
| :--- | :--- |
| **`esp32_firmware/`** | All C++ code files (`.ino`) for the ESP32 controller. |
| **`raspi_vision/`** | Python script (`.py`) for gaze detection and the MediaPipe model file (`.task`). |
| **`documentation/`** | Guides and setup instructions, including the Remote Access Guide. |

## 🔧 Installation & Setup

1.  **Wiring:** Refer to the **[Wiring Diagram Image Name, e.g., Wiring_Diagram.png]** for hardware connections.
2.  **Remote Access:** Follow the [Remote Access Guide](documentation/Remote_Access_Guide.md) to set up SSH/VNC for deployment.
3.  **Raspberry Pi Setup:** Install required Python packages: `pip install opencv-python mediapipe paho-mqtt numpy picamera2`.
4.  **ESP32 Setup:** Update your Wi-Fi/MQTT credentials (lines 2-5 of the C++ files) and flash the appropriate `.ino` file to your board.


### Step 10: Post to LinkedIn (The Final Action)

1.  Copy the URL of your finished GitHub repository.
2.  Use the concise, high-impact LinkedIn post (from the previous response).
3.  Paste the post into LinkedIn and be
