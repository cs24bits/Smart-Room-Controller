# AutoHome: IoT Smart Room Controller

An IoT-based smart room automation system that integrates ambient light sensing, motion detection, temperature-based control, and air quality monitoring to optimize energy consumption. 

Built utilizing an Arduino Uno and four primary sensors to dynamically control room states based on environmental conditions and occupancy.

## 🛠️ Hardware & Components
* **Microcontroller:** Arduino Uno
* **Sensors:** 
  * LDR (Photoresistor) - Ambient Light
  * HC-SR04 Ultrasonic - Motion/Presence
  * DHT11 - Temperature & Humidity
  * MQ135 - Air Quality / CO2 Concentration
* **Outputs:** LEDs acting as relay triggers for Light, AC, and Air Quality Alerts

## ⚙️ Core Logic & Features
* **Automated Lighting:** Triggers lighting only when ambient light is low (LDR threshold) AND motion is detected (Ultrasonic). Includes a timeout failsafe.
* **AC Hysteresis Control:** Controls AC relay using DHT11 data. Applies strict hysteresis boundaries (turns ON > 26°C, turns OFF < 20°C) to prevent rapid relay toggling and hardware wear.
* **Air Quality Monitoring:** Calculates corrected CO2 PPM utilizing real-time temperature and humidity data from the DHT11 to adjust MQ135 readings. Triggers an alert if PPM exceeds 300.

## 🔌 Pin Mapping
| Component | Arduino Pin |
|-----------|-------------|
| LDR       | A0          |
| MQ135     | A1          |
| DHT11     | D2          |
| AC Relay  | D4          |
| AQ Alert  | D5          |
| Light     | D7          |
| HC-SR04   | D9 (Trig), D10 (Echo) |

## 🚀 Setup & Execution
1. Wire the components according to the Pin Mapping table.
2. Install the `Adafruit_Sensor`, `DHT`, and `MQ135` libraries in the Arduino IDE.
3. Upload `autohome.ino` to the Arduino Uno.
4. Open the Serial Monitor (9600 baud) to view real-time environmental metrics and system states.