---
title: 6. Alarm System (INPUT) 
type: docs
weight: 6
BookToC: false
---

# Exercises with the DualMCU Board - MicroPython


## 6. Alarm system

### Objective
Implement a system to generate an alarm sound with motion detection.
>**NOTA** In this practices, you will use the microcontroller **ESP32**.

## Description
The alarm system is fundamental for maintaining security in a space or property. In this section, we will share resources and code to construct a personalized alarm system that can adapt to your specific needs using ESP32 microcontroller with MicroPython.

### Materials 


+ 1x [UNIT DualMCU board](https://uelectronics.com/producto/unit-dualmcu-esp32-rp2040-tarjeta-de-desarrollo/)
+ 1x [Motion sensor PIR (HC-SR505)](https://uelectronics.com/producto/sensores-de-movimiento-pir-hc-sr501-hc-sr505-hy3612-am312/)
+ 1x [3V Buzzer](https://uelectronics.com/producto/buzzer-activo-3v-5v-12v-zumbador/)
+ 1x [Dupont Cables](https://uelectronics.com/producto/cables-dupont-largos-20cm-hh-mh-mm/)

###  Connection Diagram

To proceed, here's a connection diagram between the Motion sensor AM312 and the development board.
![Connection Diagram](/dual/docs/6-Sistema_de_Alarma/images/DIAGRAMA.jpg)

Additionally, for programming the DualMCU, select the configuration for using ESP32.
<div style="text-align: center;">
<img src="/DualMCU_Getting_Started/docs/2-Micropython/images/esp32_or_rasp.jpg" alt="Block Diagram" title="Block Diagram" style="width: 300px;">
</div>

## Code
The following code manages the motion sensor and activates the audible alarm using a buzzer. This code can serve as a starting point for creating a more advanced system.

<div style="text-align: right;">
    <a href="/DualMCU_Getting_Started/docs/6-Sistema_de_Alarma/code/unitRP2040_pir.py" download="unitESP32_pir.py">
        <button style="background-color: #4CAF50; color: white; padding: 10px 20px; border: none; border-radius: 4px; cursor: pointer;">
            Download unitESP32_pir.py
        </button>
    </a>
</div> 

```python
 
from machine import Pin
import time

# Configura el pin del sensor PIR y el buzzer
pir_pin = Pin(16, Pin.IN)  # Reemplaza el número de pin según tu conexión
buzzer_pin = Pin(15, Pin.OUT)  # Reemplaza el número de pin según tu conexión


# Función para activar la alarma
def activate_alarm():
    print("¡Movimiento detectado! Activando alarma...")
    buzzer_pin.on()
    time.sleep(5)  # La alarma suena durante 5 segundos
    buzzer_pin.off()

print("Sistema de alarma PIR activado")

while True:
    if pir_pin.value() == 1:  # El sensor PIR detecta movimiento
        activate_alarm()
    
    time.sleep(0.5)  # Espera 0.5 segundos antes de volver a verificar el sensor PIR

```

## Results
Upon running the script, you will first receive a system-ready message. Subsequently, if motion is detected, a message will be sent to the buzzer, triggering an alert for the movement.
 
<div style="text-align: center;">
<img src="/DualMCU_Getting_Started/docs/6-Sistema_de_Alarma/images/cap.png" alt="Block Diagram" title="Block Diagram" style="width: 600px;">
</div>

## Conclusions 
Creating a system to recognize the GPIO terminal I/O configuration of the DualMCU board with ESP32 is straightforward. The system effectively obtains an input signal through the PIR sensor, triggering the buzzer upon motion detection.



> **NOTE:** Keep in mind that the presented codes are only examples and may require configuration adjustments according to specific needs and requirements.

# Continue with the course [Control Motors DC](/dual/docs/7-control_de_motores_dc/)



* [License](https://www.gnu.org/licenses/gpl-3.0.html) The code presented in this repository is licensed under the GNU General Public License (GPL) version 3.0.
---
⌨️ with ❤️ from [UNIT-Electronics](https://github.com/UNIT-Electronics) 😊

