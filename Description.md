

### 1. Physical Connections

| Component | ESP32 Pin Name | Connection Detail |
| :--- | :--- | :--- |
| **Danger Button** | **Pin 4** | Connect between **Pin 4** and **3.3V**. |
| **Water Probes** | **Pin 5** | One wire to **Pin 5**, one wire to **3.3V**. |
| **Fire Loop** | **Pin 23** | A wire loop running directly from **3.3V** to **Pin 23**. |

---

### 2. Short Description
**Child Safety Monitor:** A physical hardware-based safety monitor that detects environmental emergencies via three dedicated digital triggers and tracks biological health using an **MLX90614** non-contact infrared temperature sensor.

---

### 3. How It Works
* **MLX90614 Temperature Logic:** The sensor sends digital temperature data to **Pin 21** and **Pin 22**. If the baby's skin heat rises above 37.8°C, the dashboard triggers a **"FEVER ALERT."**
* **Fire Logic:** Uses a "Dead-Man's Switch" loop. **Pin 23** must always receive 3.3V. If fire burns and breaks this wire, the signal is lost (LOW), triggering **"BABY ON FIRE."**
* **Water Logic:** Uses conductivity. When water touches both probes, it connects 3.3V to **Pin 5** (HIGH), triggering **"UNDER WATER."**
* **Danger Logic:** A manual override button. When pressed, it sends 3.3V to **Pin 4**, triggering **"BABY IN DANGER!"**
* **Fixed IP Access:** The ESP32 creates its own WiFi. Once connected, you access the dashboard at **192.168.0.9**.

---

### 4. Project Output Details
* **WiFi Name:** `CHILD SAFETY`
* **Password:** `234555444`
* **Access URL:** `http://192.168.0.9`
