# Web-Controlled 8x8 LED Matrix using ESP8266

This project uses an ESP8266 microcontroller (e.g., NodeMCU or ESP-01) connected to a MAX7219-based 8x8 LED matrix to display custom messages sent from a web interface. The matrix can be updated remotely in real-time using MQTT.

## 🔧 Features

- Control LED matrix display wirelessly via the internet
- Supports custom text messages
- Uses MQTT for communication
- Clean and responsive display with LedControl library
- Simple setup, lightweight code

## 🧠 Project Overview

This project allows anyone to send messages to an 8x8 LED matrix using a web interface. The ESP8266 receives these messages over MQTT and displays them on the LED matrix using the MAX7219 driver.

This is a simple yet powerful example of IoT, showing how microcontrollers can receive and react to live data from the internet.

## 🖥️ Tech Stack

- **Microcontroller:** ESP8266 (e.g., NodeMCU, ESP-01)
- **Display Module:** MAX7219 8x8 LED matrix
- **Library:** LedControl
- **Communication:** MQTT (via [PubSubClient](https://github.com/knolleary/pubsubclient))
- **MQTT Broker:** HiveMQ Public Broker
- **Web Interface:** Any MQTT-compatible web client (e.g., [HiveMQ Web Client](https://www.hivemq.com/demos/websocket-client/))

## ⚙️ Hardware Setup

| Component         | Connection to ESP8266 |
|-------------------|------------------------|
| MAX7219 DIN       | GPIO13 (D7)            |
| MAX7219 CLK       | GPIO14 (D5)            |
| MAX7219 CS/LOAD   | GPIO15 (D8)            |
| VCC               | 5V                     |
| GND               | GND                    |

**Power Notes:**
- If you're using ESP-01, make sure to regulate voltage properly.
- MAX7219 needs 5V for stable display; ESP8266 works on 3.3V.

## 📝 How It Works

1. ESP8266 connects to your Wi-Fi network.
2. It subscribes to an MQTT topic (e.g., `LedMatrix/Control`).
3. You send a message (e.g., "HI", "123") from the web interface to that topic.
4. ESP8266 receives the message and displays it on the LED matrix using the LedControl library.

## 📦 Dependencies

- `LedControl.h`
- `ESP8266WiFi.h`
- `PubSubClient.h`

Install them via Arduino IDE Library Manager.

## 📡 MQTT Configuration

- **Broker:** `broker.hivemq.com`
- **Port:** `1883`
- **Subscribe Topic:** `LedMatrix/Control`
- **Message Format:** Plain text

Example:  
Send `"HELLO"` to `LedMatrix/Control` to display "HELLO".

## 📷 Preview

*(Insert image or gif of the LED matrix showing a message, if you have one)*

## 🚀 Getting Started

1. Clone this repository
2. Open the `.ino` file in Arduino IDE
3. Enter your Wi-Fi SSID and password in `wifi_setup()` or define them as constants
4. Flash the code to your ESP8266
5. Open HiveMQ WebSocket Client and publish to the topic

## 🧪 Future Improvements

- Add scrolling text support
- Support for multiple LED matrices (daisy-chained)
- Include message history
- Add web dashboard for easier input

## 📜 License

This project is open-source and free to use under the MIT License.

---

Made with ❤️ using ESP8266 and a little bit of Python (on the web/MQTT side).
