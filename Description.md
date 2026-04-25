

### 1. Full Connection Table



| Component | ESP32 Pin | Connection Logic |
| :--- | :--- | :--- |
| **I2C SDA** | **Pin 21** | Connect to **SDA** on both MLX90614 and MAX30105. |
| **I2C SCL** | **Pin 22** | Connect to **SCL** on both MLX90614 and MAX30105. |
| **Danger Button** | **Pin 4** | One side to **Pin 4**, other side to **3.3V**. |
| **Water Sensor** | **Pin 5** | Two wires placed near water; one to **Pin 5**, one to **3.3V**. |
| **Fire Loop** | **Pin 23** | A wire jumping directly from **3.3V** to **Pin 23**. |
| **Microphone** | **Pin 34** | Connect the **Out** pin of the mic to **Pin 34**. |
| **Power (All)** | **3.3V & GND** | All sensors and buttons must share the ESP32’s 3.3V and GND. |

---

### 2. How It Works
1.  **Fixed Networking:** The ESP32 creates its own WiFi network. When you connect, it serves as a web host at `192.168.0.9`. 
2.  **Safety Logic:**
    * **Fire:** Uses a "Continuity Loop." If fire burns the wire, the 3.3V signal to Pin 23 is lost (LOW), triggering the alert.
    * **Water:** Uses a "Bridge." Water conducts electricity between 3.3V and Pin 5 (HIGH) to trigger the alert.
3.  **Biologicals:** The **I2C Hub** allows two sensors to talk over just two wires. The **MLX90614** reads heat without contact, and the **MAX30105** detects blood flow via IR light.
4.  **Translation:** When you click "Listen" on the website, your phone's browser records Bangla speech and uses a Google API to display English text instantly.

---

### 3. Short Description
The **Child Safety Monitor** is an all-in-one IoT solution for caregivers. It uses an ESP32 to monitor physical hazards (Fire/Water) and biological health (Body Temperature/Heart Rate) in real-time. It features a built-in Bangla-to-English voice translator accessible via a permanent local IP address, ensuring safety and communication are always just one click away.

**Output IP:** `192.168.0.9`  
**WiFi:** `CHILD SAFETY` | **Pass:** `234555444`
