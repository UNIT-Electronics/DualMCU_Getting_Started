---
title: 2. MicroPython & ESP32
type: docs
weight: 2
BookToC: false
---
# DualMCU: MicroPython


--------------------------------------

In this section, we will provide a basic example of installing MicroPython on the DualMCU ESP32 microcontroller. Our objective is to streamline this process, enabling you to seamlessly integrate it into your projects.

- [Firmware ESP32](#esp32-firmware-update)
- [Firmware RP2040](#rp2040-firmware-update)

To begin, follow the simple connection diagram: connect the DualMCU unit using a USB Type-C connector. This initial step will allow you to explore and familiarize yourself with the functionality of MicroPython efficiently.

We hope this guide simplifies the process, providing you with a better understanding and utility for future projects!

![pc](/DualMCU_Getting_Started/docs/3-Led_intermitente/images/pc_dual.jpg)


Remember, when working with DualMCU, you have the flexibility to interchange between microcontrollers using the change interrupt.


<div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/docs/2-Micropython/images/selector.png" alt="Block Diagram" title="Block Diagram" style="width: 600px;">
</div>

>**NOTE**
> If the UNIT DUALMCU ESP32 is not recognized, it will be necessary to install the [ CH340 DRIVER](/DualMCU_Getting_Started/docs/3-Led_intermitente/images/CH341SER.EXE). 



## Environment Configuration

Before starting, we recommend configuring your environment with the following settings:

1. <a href="https://thonny.org/" target="_blank"> Install Thonny </a> to facilitate the firmware download to the DualMCU ESP32.

1. Navigate to "Run" -> "Config interpreter" 

<div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/docs/2-Micropython/images/find.png" alt="Block Diagram" title="Block Diagram" >
</div>

When you do this, the following window will open:

<div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/docs/2-Micropython/images/config_intepeter.png" alt="Block Diagram" title="Block Diagram" style="width: 600px;">
</div>


### ESP32 Firmware Update
Start the DualMCU UNIT with the ESP32 microcontroller in **Position A** by pressing the FLASH button and connecting the device to the PC.

<div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/docs/2-Micropython/images/flash.png" alt="Block Diagram" title="Block Diagram" style="width: 600px;">
</div>

1. Click on **"Install or Update MicroPython"**.

2. A new window will open.
    - It is recommended to use the following configuration:
        - Variant: Espressif ESP32/WROOM
        - Version: 1.20.0

<div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/docs/2-Micropython/images/instalador.png" alt="Block Diagram" title="Block Diagram">
</div>

3. Press install (wait for the installation to finish).

Select the board you want to work with at the bottom of Thonny. You can find this option in a format similar to the one shown in the following image for the ESP32. Note that the COM port is assigned by the machine and may vary.

<div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/docs/2-Micropython/images/target.png" alt="Block Diagram" title="Block Diagram">
</div>

### RP2040 Firmware Update
Start the DualMCU UNIT with the RP2040 microcontroller in **Position B** by pressing the `BOOT` button and connecting the device to the PC.

<div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/2-Micropython/images/RP2040-Boot_button.jpg" alt="Block Diagram" title="Block Diagram" style="width: 600px;">
</div>

1. Click on **"Install or Update MicroPython"**.

2. A new window will open.
    - It is recommended to use the following configuration:
        - Variant: Raspberry Pi Pico/Pico H
        - Version: 1.22.2

<div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/docs/2-Micropython/images/config_intepeter_rp.png" alt="Block Diagram" title="Block Diagram">
</div>

3. Press install (wait for the installation to finish).

Select the board you want to work with at the bottom of Thonny. You can find this option in a format similar to the one shown in the following image for the RP2040. Note that the COM port is assigned by the machine and may vary.

<div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/docs/2-Micropython/images/target_rp.png" alt="Block Diagram" title="Block Diagram">
</div>

## Loader your firts "Hello, World" 🌎
Once your device is configured and tested, we recommend creating your "Hello, World" using the following code practices:

 <div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/docs/2-Micropython/images/explorando.png" alt="Block Diagram" title="Block Diagram" style="width: 800px;">
</div>

Copy and paste the following code:


```py
print("Hello, world!")

```

**Run code**.  You can find a green button at the top part of the interface:

<div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/docs/2-Micropython/images/buton.png" alt="Block Diagram" title="Block Diagram">
</div>


You will see the result in the serial shell:


<div style="text-align: center;">
    <img src="/DualMCU_Getting_Started/docs/2-Micropython/images/result.png" alt="Block Diagram" title="Block Diagram">
</div>

This simple step introduces you to the MicroPython environment and establishes the foundation for the following exercises. Explore and enjoy your MicroPython programming experience!




# Next course [LED Blinking](/DualMCU_Getting_Started/docs/3-led_intermitente/)





⌨️ with ❤️ from [UNIT-Electronics](https://github.com/UNIT-Electronics) 😊