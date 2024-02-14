---
title: 9. Environmental Monitoring System
type: docs
weight: 9
BookToC: false
---

# Exercises with DualMCU - MicroPython

## 9. Environmental Monitoring System
### Objective
Utilize the DTH11 and MQ135 sensors to measure environmental parameters such as humidity, temperature, and air quality in real-time. Visualize the readings in the serial monitor.

>**NOTE:** In this practice, you will use the microcontroller **ESP32**.

### Description 

The Environmental Monitoring System is fundamental for measuring and managing parameters such as temperature, humidity, air quality, and other factors for comfortable and secure environments. To continue, we'll share resources and code to construct an Environmental Monitoring System using the DHT11 and MQ135 sensors with the ESP32 configured with MicroPython.

### Materials
+ 1x <a href="https://uelectronics.com/producto/unit-dualmcu-esp32-rp2040-tarjeta-de-desarrollo/" target="_blank">UNIT DualMCU board</a>
+ 1x <a href="https://uelectronics.com/producto/modulo-ky-015-sensor-de-temperatura-y-humedad/" target="_blank"> Temperature sensor DHT11 </a>
+ 1x <a href="https://uelectronics.com/producto/mq-135-modulo-detector-de-calidad-de-aire/" target="_blank">  Air quality sensor  MQ135</a>
+ 1x <a href="https://uelectronics.com/producto/cables-dupont-largos-20cm-hh-mh-mm/" target="_blank">Cables Dupont</a>

### Connection Diagram


<div style="text-align: center;">
<img src="/dual/docs/9-Sistema_de_monitoreo/images/AR3578Diagrama.jpg" alt="Block Diagram" title="Block Diagram" >
</div>

>**NOTE**
> Remember that when working with the DualMCU, you can switch between microcontrollers using the change switch. For this practice, we will only use the **ESP32** microcontroller, so you should switch the change switch to position "B".
<div style="text-align: center;">
    <img src="/dual/docs/2-Micropython/images/selector.png" alt="Block Diagram" title="Block Diagram" style="width: 600px;">
</div>


###  Code
```python
'''
Unit Electronics 2024
       (o_
(o_    //\
(/)_   V_/_ 

version: 0.0.1
revision: 0.0.1
compiler: MicroPython v1.22.0 on 2023-12-27; Generic ESP32 module with ESP32
'''
from dht import DHT11
from machine import Pin, ADC
from time import sleep

sensor = DHT11 (Pin(4))

# configura entrada de adc en el pin 36

adc = ADC(Pin(36))
# configura el rango de lectura de 0 a 3.3v
adc.atten(ADC.ATTN_11DB)
# configura el rango de lectura de 0 a 4095
adc.width(ADC.WIDTH_12BIT)

while True:
  try:
    sleep(2)
    valor = adc.read()
    #imprime el valor del adc
    print(valor)
    sensor.measure()
    temp = sensor.temperature()
    hum = sensor.humidity()
    temp_f = temp * (9/5) + 32.0
    print('Temperature: %3.1f C' %temp)
    print('Temperature: %3.1f F' %temp_f)
    print('Humidity: %3.1f %%' %hum)
  except OSError as e:
    print('Failed to read sensor.')
```

### Results
This code reads the temperature and humidity from the DHT11 sensor, the air quality from the MQ135 sensor every minute, and prints the read values.

### Conclusions

During this practice, knowledge was acquired about the operation of two sensors, which enable the monitoring of temperature, humidity, and air quality. It is imperative to highlight that, in addition to providing the code and the connection diagram, it is necessary to carry out the calibration of the sensors to optimize their utility in a specific application. It is also important to note the feasibility of connecting the ESP32 to a network, thus allowing the sending of the readings acquired to a server or a database.


> **NOTE:** Keep in mind that the presented codes are only examples and may require configuration adjustments according to specific needs and requirements.



#  Continue with the course [OLED Control (I2C)](/dual/docs/10-control_de_pantalla_oled/)




* [License](https://www.gnu.org/licenses/gpl-3.0.html) The code presented in this repository is licensed under the GNU General Public License (GPL) version 3.0.
---
⌨️ with ❤️ from [UNIT-Electronics](https://github.com/UNIT-Electronics) 😊 