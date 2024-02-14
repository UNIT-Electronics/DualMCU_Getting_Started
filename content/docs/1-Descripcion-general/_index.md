---
title: 1. Board Features
type: docs
weight: 1
BookToC: false
---

<!-- # 8-bit enhanced USB microcontroller CH559 -->
# DualMCU Introduction - MicroPython  
<!-- 
## 1. Descripción general
El módulo DualMCU representa una innovadora fusión entre el microcontrolador Raspberry Pi RP2040 y el chip Espressif ESP32 WROOM, consolidados en un único y eficiente dispositivo. Este diseño aprovecha plenamente los núcleos duales Arm® Cortex®-M0+ de 32 bits, proporcionando una base sólida para la implementación de proyectos de Internet de las cosas (IoT) con conectividad Bluetooth® y Wi-Fi.

En términos de potencia de procesamiento, la DualMCU integra dos microprocesadores de 32 bits: un Cortex M0+ de Raspberry RP2040 que opera a 133 MHz y un Espressif ESP32 que alcanza hasta 240 MHz. Esta combinación estratégica permite capitalizar al máximo las capacidades de ambos microcontroladores en una única tarjeta de desarrollo. Con un tamaño de PCB de 36 mm x 84 mm y utilizando tecnología de montaje superficial, la DualMCU alberga cuatro núcleos programables, destacando por sus funciones inalámbricas avanzadas y un consumo de energía excepcionalmente bajo.

Para obtener información detallada y recursos adicionales, se recomienda visitar el repositorio oficial de la DualMCU.

En el contexto de sus características técnicas, la DualMCU se presenta como una tarjeta de desarrollo única en su clase, amalgamando los microcontroladores ESP32 y RP2040. Esta unión posibilita la creación de proyectos de IoT con conectividad Bluetooth® y Wi-Fi, entre otras funcionalidades. Pero, ¿qué distingue a esta placa de desarrollo? A continuación, resaltamos sus principales atributos técnicos.


<table>
    <tr>
        <td>
            <img src="/docs/1-Descripcion-general/images/dual.png" alt="Block Diagram" title="Block Diagram" style="width: 500px;">
        </td>
        <td>
            <strong>Fabricante:</strong> UNIT ELECTRONICS<br>
            <strong>Color de PCB:</strong> Negro<br>
            <strong>Dimensiones:</strong> 84mm x 36mm x 6.6mm<br>
            <strong>Peso:</strong> 22.57g<br>
            <strong>MCUs:</strong> RP2040 Dual Core + ESP32 WROOM-32E<br>
            <strong>USB a UART:</strong> CH340C<br>
            <strong>Conectores:</strong> 2 x I2C JST-SH Pitch 1mm, 1 MicroSD, USB Tipo C y JST-SH 2p Pitch 2mm: Conexión para batería.<br>
            <strong>Incluye:</strong> Tira header macho doble 2.54mm (2×3, 2×20 pines)<br>
            <strong>Memoria:</strong> W25Q16JVUXIQ 2MB NOR Flash, 532MHz Quad SPI y 66MB/S Tasa de transferencia continua de datos.<br>
            <strong>Alimentación:</strong> 3.3V LDO 600mA, 3.3V Power/Enable pin, VUSB Output/VIN: 3.2 a 6V DC, Interfaz para cargar baterías de 200mA con led incorporado.<br>
            <strong>SWITCH:</strong> Power Switch, Selector de comunicación USB, DIP Switch para comunicación UART, Botón de RESET y Cargador de arranque para reinicios rápidos de RP2040 y Boton de RESET y FLASH/BOOT.<br>
            <strong>LED´S:</strong> RGB WS2812B NoePixel: Conexión a RP2040 GPIO, RGB Cátodo común: Conexión a ESP32 GPIO y Builtin Led: Led de propósito general conectado al GPIO25 RP2040.<br>
            <strong>MICROSD CARD:</strong> Conexión a ESP32 y Interfaz de comunicación: VSPI.
        </td>
    </tr>
</table>


---


##  Características
Ahora, centrémonos en la disposición de elementos de la placa, ya que es crucial comprender la ubicación de cada componente para facilitar su uso.

**Vista frontal** ![Block_Diagram](/docs/1-Descripcion-general/images/Front_View_DualMCU_Topology.jpg "Block Diagram")

| Ref. | Descripción | Ref. | Descripción
|----------|----------|----------|-------|
|  U1  | Microcontrolador Raspberry Pi RP2040   |   U4  | Circuito integrado de conversión USB CH340C |
|  U2  | Módulo Wi-Fi/Bluetooth® Espressif ESP32 WROOM    |   U5  | Circuito integrado de gestión de carga de batería MCP73831 |
|  U3  | Circuito integrado de memoria flash de 2 MB W25Q16JVUXIQ  |   U6  | Regulador de voltaje LDO 3.3V AP2112K |
|  L1  | LED de encendido   |   L2  | LED de carga |
|  L3  | LED (GPIO25)   |   L4  | WS2812B LED |
|  L5  | LED RGB 2020  |   J1  | Conector USB tipo C macho |
|  PB1  | Botón de reinicio RP2040   |   PB2  |  Botón de arranque RP2040 |
|  PB3  | Botón de flasheo ESP32     |   PB4  | Botón de reinicio ESP32 |
|  JP1  |GPIO Pines de la RP2040    |   JP2  | ESP32 GPIO Header |
|  JP3  |RP2040 (SWD) Debug Header    |   JST1  | Conector JST I2C RP2040  |
|  JST2  | Conector JST I2C ESP32  |   JST3  | Conector JST para batería de litio (LiPo) |
|  SW2  | Selector de comunicación USB   |   SW3  | Interruptor DIP UART |

**Vista reverso**

![Block_Diagram](/docs/1-Descripcion-general/images/Back_View_DualMCU_Topology.jpg "Block Diagram")

| Ref. | Description | Ref. | Description
|----------|----------|----------|-------|
|  U7  | Soporte para el circuito integrado criptográfico ATECC608A-MAHDA-T   |   J2  |  Conector para tarjeta microSD |
|  SW1  | Interruptor de encendido   |   SB1  | Puente de soldadura del LED de carga (desconectado por defecto) |
|  SB2  | Puente de soldadura del sensor VBUS (desconectado por defecto) |   SB3  | Regulador de voltaje LDO 3.3V AP2112K |
|  SB4  | uente de soldadura del reinicio ESP32 (desconectado por defecto)   |   SB5  |  Puente de soldadura del selector de señal SCL para ATECC608A-MAHDA-T (desconectado por defecto)|
|  SB6  | Puente de soldadura del selector de señal SDA para ATECC608A-MAHDA-T (desconectado por defecto)|   B1  |Pads de soldadura para batería de litio (LiPo) |

---
---
#  Continua con el curso [Micropython y el ESP32](/docs/2-micropython/) -->

--------------------------------------------------------------------------
# General Description
The DualMCU module represents a powerful platform that combines the Raspberry Pi RP2040 and the Espressif ESP32 WROOM chip, creating an efficient device. This design incorporates dual Arm® Cortex®-M0+ 32-bit cores, providing a robust foundation for IoT projects with Bluetooth and Wi-Fi connectivity.

In terms of processing power, the DualMCU integrates two 32-bit microprocessors: a Cortex M0+ from Raspberry RP2040 operating at 133 MHz and an Espressif ESP32 running at up to 240 MHz. This configuration allows for the maximum capabilities of both microcontrollers on a single compact board. With a PCB size of 36 mm x 84 mm, utilizing surface-mount technology, it ensures low power consumption.

For information on resources, it is recommended to refer to the <a href="https://github.com/UNIT-Electronics/DualMCU" target="_blank">official repository.</a>

In the context of technical features, the DualMCU stands out as a unique development board in its class, showcasing unparalleled capabilities.


<table>
    <tr>
        <td>
            <img src="/docs/1-Descripcion-general/images/dual.png" alt="Block Diagram" title="Block Diagram" style="width: 500px;">
        </td>
        <td>
            <strong>Manufacturer:</strong> UNIT ELECTRONICS<br>
            <strong>PCB Color:</strong> Black<br>
            <strong>Dimensions:</strong> 84mm x 36mm x 6.6mm<br>
            <strong>Weight:</strong> 22.57g<br>
            <strong>MCUs:</strong> RP2040 Dual Core + ESP32 WROOM-32E<br>
            <strong>USB to UART:</strong> CH340C<br>
            <strong>Connectors:</strong> 2 x I2C JST-SH Pitch 1mm, 1 MicroSD, USB Type C, and JST-SH 2p Pitch 2mm: Battery Connection.<br>
            <strong>Includes:</strong> Double 2.54mm Male Header Strip (2×3, 2×20 pins)<br>
            <strong>Memory:</strong> W25Q16JVUXIQ 2MB NOR Flash, 532MHz Quad SPI, and 66MB/S Continuous Data Transfer Rate.<br>
            <strong>Power:</strong> 3.3V LDO 600mA, 3.3V Power/Enable pin, VUSB Output/VIN: 3.2 to 6V DC, Interface for charging 200mA batteries with built-in LED.<br>
            <strong>Switch:</strong> Power Switch, USB Communication Selector, DIP Switch for UART communication, RESET Button, and Bootloader for quick restarts of RP2040. RESET and FLASH/BOOT Button.<br>
            <strong>LEDs:</strong> WS2812B NeoPixel RGB LEDs connected to RP2040 GPIO, Common-cathode RGB LED connected to ESP32 GPIO, and Built-in LED: General-purpose LED connected to RP2040 GPIO25.<br>
            <strong>MICROSD CARD:</strong> Connection to ESP32 and Communication Interface: VSPI.
                    </td>
    </tr>
</table>

## Features

Now, let's focus on the layout of the board elements, as it is crucial to understand the location of each component for ease of use.

**Front View**![Block_Diagram](/dual//docs/1-Descripcion-general/images/Front_View_DualMCU_Topology.jpg "Block Diagram")

| Ref. | Description | Ref. | Description
|----------|----------|----------|-------|
|  U1  | Raspberry pi RP2040 Microcontroller   |   U4  | CH340C USB bus convert IC |
|  U2  | Espressif ESP32 WROOM Wi-Fi/Bluetooth® Module   |   U5  | MCP73831 Battery Charge Management IC |
|  U3  | W25Q16JVUXIQ 2MB Flash IC   |   U6  | AP2112K 3v3 LDO Voltage Regulator |
|  L1  | Power On LED   |   L2  | Charge LED |
|  L3  | Builtin LED (GPIO25)   |   L4  | WS2812B LED |
|  L5  |RGB 2020 LED   |   J1  | Male USB Type C Connector |
|  PB1  |RP2040 Reset Button   |   PB2  | RP2040 Boot Button |
|  PB3  |ESP32 Flash Button    |   PB4  | ESP32 Reset Button |
|  JP1  |RP2040 GPIO Header    |   JP2  | ESP32 GPIO Header |
|  JP3  |RP2040 (SWD) Debug Header    |   JST1  | RP2040 I2C JST Connector |
|  JST2  |ESP32 I2C JST Conector   |   JST3  | JST Connector for LiPo Battery |
|  SW2  |USB Communication Selector   |   SW3  | UART DIP Switch |

**Back View**![Block_Diagram](/docs/1-Descripcion-general/images/Back_View_DualMCU_Topology.jpg "Block Diagram")


| Ref. | Description | Ref. | Description
|----------|----------|----------|-------|
|  U7  | Support for the ATECC608A-MAHDA-T Crypto IC   |   J2  | Micro SD Card Connector |
|  SW1  | Power Switch   |   SB1  | Charge LED Solder Bridge (default disconnected) |
|  SB2  | VBUS Sense Solder Bridge (default disconnected) |   SB3  | AP2112K 3v3 LDO Voltage Regulator |
|  SB4  | ESP32 Reset Solder Bridge (default disconnected)   |   SB5  | SCL Signal Selector Solder Bridge for ATECC608A-MAHDA-T (default disconnected)|
|  SB6  | SDA Signal Selector Solder Bridge forATECC608A-MAHDA-T (default disconnected)|   B1  | Lipo Battery Solder Pads |


#  Next course [MicroPython & ESP32](/docs/2-micropython/)
⌨️ with ❤️ from [UNIT-Electronics](https://github.com/UNIT-Electronics) 😊