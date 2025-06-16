# AutoShade - Smart Rain Sensing System

This is a practical IoT project designed to automatically protect outdoor items from rain using a shade controlled by a servo motor.

---

## Project Overview
The system uses an **ESP32 microcontroller** to read data from a water sensor, which detects rain by measuring moisture levels. The ESP32 sends this information to an **Arduino Uno** via UART communication. 
- If rain is detected (sensor value > 200), the Arduino displays **"Rain Detected"** on a 16x2 LCD screen and moves the servo to **0°** to close the shade.
- If no rain is detected, it shows **"Clear Weather"** and moves the servo to **90°** to open the shade.

---

## Repository Structure

- **`src/` (Project Files)**
  - `MQTT/`: Python scripts and configurations for the MQTT broker.
  - `Ardino-UNO.txt`: C++ source code for the Arduino Uno microcontroller.
  - `ESP-32.txt`: C++ source code for the ESP32 microcontroller.
  - `assembly.txt`: Hardware assembly instructions.
  - `connections.txt`: Detailed wiring pinouts for components.
- **`docs/` (Documentation)**
  - `report.md`: Detailed project report, including methodology, data flow diagrams, and future works.
  - `proposal.pdf` & `report.pdf`: Official documentation submitted for the project.
- **`assets/` (Images)**
  - Visual assets and circuit diagrams demonstrating the built module and its components.

---

## Components Used
| Component | Quantity | Description |
|-----------|----------|-------------|
| **ESP32 Devkit V1** | 1 | Reads water sensor data, sends status to Arduino via UART. |
| **Arduino Uno R3** | 1 | Controls the LCD and servo based on ESP32 data. |
| **Water Sensor** | 1 | Detects rain by measuring moisture (connected to ESP32 GPIO34). |
| **16x2 LCD (LM016L)** | 1 | Displays the current weather status. |
| **SG90 Servo Motor** | 1 | Moves the physical shade to 0° (rain) or 90° (clear). |
| **Resistor (3.9kΩ)** | 1 | Adjusts LCD contrast. |

---

## How It Works
1. **Sensing:** The water sensor continuously measures moisture. The ESP32 reads these analog values.
2. **Processing & Communication:** The ESP32 determines the weather status (Rain if value > 200, Clear if ≤ 200). It acts as an MQTT client and also communicates directly with the Arduino Uno via UART (TX2 to RX0).
3. **Actuation & Display:** The Arduino Uno receives the weather status. It updates the 16x2 LCD with the appropriate message and triggers the SG90 servo motor to either retract or deploy the physical shade.


---

## Course

**Subject**: Computer Organization and Assembly Language (COAL) Lab  
**Semester**: 4th 