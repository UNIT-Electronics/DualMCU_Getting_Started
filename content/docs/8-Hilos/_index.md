---
title: 8. Threads
type: docs
weight: 8
BookToC: false
---

# Exercises with DualMCU - MicroPython

## 8.   Threads
###	 Objective

Create a simple usage of threads implemented on the ESP32 microcontroller.

>**NOTA**  In this practices, you will use the microcontroller **ESP32**.
## Description

Threads are a powerful way to perform multiple tasks concurrently in a software program. In MicroPython for ESP32, threads allow the division of program execution into multiple sequences of instructions, which can enhance the efficiency and responsiveness of applications on platforms like DualMCU ESP32.

The following code implements two threads in MicroPython for ESP32. One thread increments a shared variable, while the other prints the shared value. This is a basic example of working with threads in MicroPython.

>**NOTE**
> Remember that when working with the DualMCU, you can switch between microcontrollers using the change switch. For this practice, we will only use the **ESP32** microcontroller, so you should switch the change switch to position "B".

<div style="text-align: center;">
    <img src="/docs/2-Micropython/images/selector.png" alt="Block Diagram" title="Block Diagram" style="width: 600px;">
</div>

###	 Materials

- <a href="https://uelectronics.com/producto/unit-dualmcu-esp32-rp2040-tarjeta-de-desarrollo/" target="_blank">UNIT DualMCU board</a>
- <a href="https://uelectronics.com/producto/cable-usb-tipo-c-3a-6a/" target="_blank"> USB Type C</a>


### Connection Diagram
![pc](/docs/3-Led_intermitente/images/pc_dual.jpg)

### Code

The code creates two threads: one to increment a shared variable and another to print the shared value.

The threads run for 10 seconds before terminating.



```py
'''
Unit Electronics 2023
        >o)
        (_>
file: share_data.py
author: Cesar
version: 0.0.1
revision: 0.0.1
context: This code facilitates the sharing of data within a counter through the utilization of threads.

ESP32
'''
import _thread
import time

shared_variable = 0

def increment_thread():
    global shared_variable
    for _ in range(10):
        shared_variable += 1
        time.sleep(1)

def print_thread():
    global shared_variable
    for _ in range(10):
        print("Valor compartido:", shared_variable)
        time.sleep(1)

# Crear y lanzar los hilos
_thread.start_new_thread(increment_thread, ())
_thread.start_new_thread(print_thread, ())

time.sleep(10)

```

## Results

In the image provided below, a screenshot of the output obtained when using threads is presented. The visual representation offers a more concrete view of how the threads are interacting and sharing data during the execution of the code.

![pc](/docs/8-Hilos/images/shell.png)

## Conclusion
The  code for MicroPython for ESP32 shows the implementation of threads to facilitate concurrent data exchange. The main functionality focuses on two threads: one to increment a shared variable and another to print that value. This basic example provides a practical introduction to the use of threads in a MicroPython environment.


> **NOTE:** Keep in mind that the presented codes are only examples and may require configuration adjustments according to specific needs and requirements.

# Continue with the course [Environmental Monitoring System](/docs/9-sistema_de_monitoreo/)

* [License](https://www.gnu.org/licenses/gpl-3.0.html) The code presented in this repository is licensed under the GNU General Public License (GPL) version 3.0.

---
⌨️ with ❤️ from [UNIT-Electronics](https://github.com/UNIT-Electronics) 😊 