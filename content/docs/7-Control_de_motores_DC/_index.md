---
title: 7. Control Motors DC
type: docs
weight: 7
BookToC: false
---

# Exercises with DualMCU - MicroPython

## 7. Control Motors DC
### Objective
Configure a direct current (DC) motor control system with the assistance of the L298N driver.

>**NOTE** In this practices, you will use the microcontroller **RP2040**.

### Description 
Control systems are integral parts of our current society, with multiple applications ranging from control temperatures to sustaining a space station in orbit.

The definition of a control system involves a combination of processes that, with the help of a set of tools, enables us to achieve a desired output performance in response to a specific input reference.

A DC motor control system can be easily adapted for various applications, as mentioned below:

   - Vehicle Propulsion
   - Mobile Robots
      - Drones
      - Wheeled or Tracked Robots
   - Cooling Systems
      - Fan Control
      - Smoke Extraction
   - Conveyor Systems
      - Conveyor Belts
   - Automation Systems
      - Smart Blinds/Curtains
   - Home Appliances and Tools
      - Vacuum Cleaners
      - Blenders
      - Dremel
      - Grinder 
      - Drills

While there are many more applications, this provides a broad idea of the diverse uses for DC motors.

This practice will focus on creating a system to precisely control the speed and direction of DC motors using an ESP32 or RP2040 device with MicroPython.


### Materials
- 1x <a href="https://uelectronics.com/producto/unit-dualmcu-esp32-rp2040-tarjeta-de-desarrollo/" target="_blank">UNIT DualMCU board</a>
- 2x <a href="https://uelectronics.com/producto/l298n-modulo-driver-motor-a-pasos/" target="_blank">Control Motors DC.</a>
- 1x <a href="https://uelectronics.com/producto/cables-dupont-largos-20cm-hh-mh-mm/" target="_blank">Driver L298N</a>
- 1x <a href="https://uelectronics.com/producto/cable-de-alambre-estanado-24awg-25cm-100-piezas/" target="_blank">Cable 24 AWG</a>
- 1x <a href="https://uelectronics.com/producto/cables-dupont-largos-20cm-hh-mh-mm/" target="_blank">Cables Dupont</a>
- Power Supply 12 V

+ Optionally, we recommend robotics kits that come with motors and drivers:
- 1x [Educational 4WD Robot Kit with Accessories](https://uelectronics.com/producto/kit-carrito-4wd-robot-educacional-con-accesorios/)
- 1x [Line Following Robot Kit with Accessories](https://uelectronics.com/producto/kit-carrito-robot-seguidor-lineas-con-accesorios/)

### Connection Diagram

Diagrama para controlar un motor
<div style="text-align: center;">
<img src="/dual/docs/7-Control_de_motores_DC/images/UnMotor_bb.png" alt="Block Diagram" title="Block Diagram" style="width: 600px;">
</div>

## Connection Diagram control two motors

<div style="text-align: center;">
<img src="/dual/docs/7-Control_de_motores_DC/images/DosMotores_bb.png" alt="Block Diagram" title="Block Diagram" style="width: 700px;">
</div>

###  Code
Once the connections for a direct current (DC) motor are made, you can control that motor using the L298N controller without using PWM with the help of the following code. Keep in mind that the motor can only be turned on or off, and its speed cannot be controlled.

> **NOTE:** Code designed for MicroPython using the DualMCU with the RP2040 microprocessor. Remember that you can switch between microcontrollers using the USB selector.
 
<div style="text-align: center;">
    <img src="/dual/docs/2-Micropython/images/esp32_or_rasp.jpg" alt="Block Diagram" title="Block Diagram" style="width: 300px;">
    </div>


<div style="text-align: right;">
    <a href="/dual/docs/7-Control_de_motores_DC/code/unitRP2040_motors1.py" download="unitRP2040_motors1.py">
        <button style="background-color: #4CAF50; color: white; padding: 10px 20px; border: none; border-radius: 4px; cursor: pointer;">
            Download unitRP2040_motors1.py
        </button>
    </a>
</div>

```python
from machine import Pin
import time

# Configura los pines para controlar el L298N
l298n_enable = Pin(7, Pin.OUT)  # Conecta a EN del L298N
l298n_input1 = Pin(14, Pin.OUT)  # Conecta a IN1 del L298N
l298n_input2 = Pin(9, Pin.OUT)  # Conecta a IN2 del L298N

# Habilita el motor
l298n_enable.on()
# Control del motor
l298n_input1.on()
l298n_input2.off()

#Espera 5s
time.sleep(5)
#Deshabilita el motor
l298n_enable.off()

#Espera 1s
time.sleep(1)
#Habilita el motor
l298n_enable.on()
# Control del motor, sentido contrario
l298n_input1.off()  
l298n_input2.on()  

#Espera 5s
time.sleep(5)
l298n_enable.off()


```

The next step is to control the motor speed, for which you will need to use PWM (Pulse Width Modulation). The maximum speed of the motor is achieved with the value 65536. We recommend testing with different values to find the speeds suitable for your projects.

#### Check the PWM values for different speeds, starting with the minimum and maximum values.

<div style="text-align: right;">
    <a href="/dual/docs/7-Control_de_motores_DC/code/unitRP2040_motors2.py" download="unitRP2040_motors2.py">
        <button style="background-color: #4CAF50; color: white; padding: 10px 20px; border: none; border-radius: 4px; cursor: pointer;">
            Download unitRP2040_motors2.py
        </button>
    </a>
</div>

```python
from machine import Pin, PWM
import time

# Configura los pines para controlar el L298N
l298n_enable = Pin(7, Pin.OUT)  # Conecta a EN del L298N
l298n_input1 = Pin(14, Pin.OUT)  # Conecta a IN1 del L298N
l298n_input2 = Pin(9, Pin.OUT)  # Conecta a IN2 del L298N

# Habilita el motor
l298n_enable.on()

# Prepara el PWM
pwm1 = PWM(l298n_input1)
pwm1.freq(1000)

pwm2 = PWM(l298n_input2)
pwm2.freq(1000)

# Define la velocidad del motor (ajusta el valor según sea necesario)
motor_speed =  65536 #Velocidad máxima

pwm1.duty_u16(motor_speed)
pwm2.duty_u16(0)

time.sleep(5)

motor_speed =  40000

pwm1.duty_u16(motor_speed)
pwm2.duty_u16(0)

time.sleep(2)

motor_speed =  65536 #Velocidad máxima

pwm1.duty_u16(0)
pwm2.duty_u16(motor_speed)

time.sleep(5)

motor_speed =  40000

pwm1.duty_u16(0)
pwm2.duty_u16(motor_speed)

time.sleep(2)

l298n_enable.off()

```
Determining workspace structure

Deciding which workspace information to collect

Gathering workspace info

Based on the previous codes, we can control two DC motors at the same time using the L298N driver with the help of the following code, where we control the speed, direction, and the turning on and off of the motors.

<div style="text-align: right;">
    <a href="/dual/docs/7-Control_de_motores_DC/code/unitRP2040_motors3.py" download="unitRP2040_motors3.py">
        <button style="background-color: #4CAF50; color: white; padding: 10px 20px; border: none; border-radius: 4px; cursor: pointer;">
            Download unitRP2040_motors3.py
        </button>
    </a>
</div>

```py
from machine import Pin, PWM
import time

# Configura los pines para controlar el L298N
l298n_enableA = Pin(7, Pin.OUT)  # Conecta a ENA del L298N
l298n_input1 = Pin(14, Pin.OUT)  # Conecta a IN1 del L298N
l298n_input2 = Pin(9, Pin.OUT)  # Conecta a IN2 del L298N
l298n_enableB = Pin(4, Pin.OUT)  # Conecta a ENB del L298N
l298n_input3 = Pin(8, Pin.OUT)  # Conecta a IN3 del L298N
l298n_input4 = Pin(11, Pin.OUT)  # Conecta a IN4 del L298N

# Habilita el motor
l298n_enableA.on()
l298n_enableB.on()

# Prepara el PWM
pwm1 = PWM(l298n_input1)
pwm1.freq(1000)
pwm2 = PWM(l298n_input2)
pwm2.freq(1000)
pwm3 = PWM(l298n_input3)
pwm3.freq(1000)
pwm4 = PWM(l298n_input4)
pwm4.freq(1000)

# Define la velocidad del motor (ajusta el valor según sea necesario)
motor_speed =  65536 #Velocidad máxima

pwm1.duty_u16(motor_speed)
pwm2.duty_u16(0)
pwm3.duty_u16(motor_speed)
pwm4.duty_u16(0)

time.sleep(5)

motor_speed =  40000

pwm1.duty_u16(motor_speed)
pwm2.duty_u16(0)
pwm3.duty_u16(motor_speed)
pwm4.duty_u16(0)

time.sleep(2)

motor_speed =  65536 #Velocidad máxima

pwm1.duty_u16(0)
pwm2.duty_u16(motor_speed)
pwm3.duty_u16(0)
pwm4.duty_u16(motor_speed)

time.sleep(5)

motor_speed =  40000

pwm1.duty_u16(0)
pwm2.duty_u16(motor_speed)
pwm3.duty_u16(0)
pwm4.duty_u16(motor_speed)

time.sleep(2)

l298n_enableA.off()
l298n_enableB.off()

```

###  Results


![Demo gif](/dual/docs/7-Control_de_motores_DC/images/carrito.gif)

### Conclusions
This activity notably exemplifies control systems, having successfully developed a control system for DC motors. This achievement not only lays the foundation for various future projects, but also introduces several key concepts of MicroPython, PWM (Pulse Width Modulation), and a better approach to the Dual MCU development board.### Conclusions
This activity notably exemplifies control systems, having successfully developed a control system for DC motors. This achievement not only lays the foundation for various future projects, but also introduces several key concepts of MicroPython, PWM (Pulse Width Modulation), and a better approach to the Dual MCU development board.


> **NOTE:** Keep in mind that the presented codes are only examples and may require configuration adjustments according to specific needs and requirements.


# Continue with the course  [Threads](/dual/docs/8-hilos/)

* [License](https://www.gnu.org/licenses/gpl-3.0.html) The code presented in this repository is licensed under the GNU General Public License (GPL) version 3.0.

#### References

Nise, N. (2019). Control Systems Engineering.v Editorial Wiley.

---
⌨️ with ❤️ from [UNIT-Electronics](https://github.com/UNIT-Electronics) 😊