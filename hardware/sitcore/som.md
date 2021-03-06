# SITCore System on Modules
---
![G400S](images/system-on-modules.jpg)

## Overview
The SITCore SoMs provide a low cost way to add .NET computing power to any embedded product. They are available as a 200 pin SO-DIMM with and without WiFi (G400 compatible), a 91 pad surface mount module (G120 compatible), or a 105 pad surface mount module (G120E compatible). The SITCore SoMs let's you design IoT products that are secure, easily integrated with the cloud, and can be easily managed and updated from the cloud for deployments of one to a million or more. The surface mount versions are great for harsh or high vibration environments.

## Ordering Part Number
* 91 Pad Surface Mount: SCM20260N
* 105 Pad Surface Mount: SCM20260E
* 200 Pin SO-DIMM: SCM20260D

## Specifications

| Spec               | All SITCore SoMs          |
|--------------------|---------------------------|
| Processor Type     | ARM Coretex-M7 32 Bit     |
| Speed              | 480 MHz                   |
| Internal RAM       | 1 MByte                   |
| Internal Flash     | 2 MByte                   |
| Instruction Cache  | 16 KByte                  |
| Data Cache         | 16 KByte                  |
| Temperature Range  | -40C to +85C              |

*Note: Resources are shared between your application and the operating system.*

## Peripherals

| Peripheral            | SCM20260N              | SCM20260E              | SCM20260D              |
|-----------------------|------------------------|------------------------|------------------------|
| GPIO (all support IRQ)|                        |                        |                        |
| SPI                   | 3                      | 3                      | 3                      |
| I2C                   | 2                      | 3                      | 3                      |
| UART/USART            | 7 (4 with handshaking) | 8 (4 with handshaking) | 8 (4 with handshaking) |
| CAN                   | 2                      | 2                      | 2                      |
| PWM                   | 21                     | 23                     | 27                     |
| ADC                   | 21                     | 21                     | 21                     |
| DAC                   | 2                      | 2                      | 2                      |
| SD/SDIP/MMC           | 1                      | 1                      | 1                      |
| Quad SPI              | 1                      | 1                      | 1                      |
| USB Host              | 1                      | 1                      | 1                      |
| USB Client            | 1                      | 1                      | 1                      |
| Ethernet              | 1                      | 1                      | 1                      |
| LCD TFT               | 1                      | 1                      | 1                      |
| Camera                | 1                      | 1                      | 1                      |

*Note: As many pins share peripherals, not all peripherals will be available.*

### Using Interrupts (IRQs)

The microcontrollers we use in our SITCore line of products do not support concurrent interrupts with the same pin number, even if the pins are on different ports (the port is denoted by the second letter of the GPIO pin name -- PA1 is pin 1 on port A). Therefore, interrupts are available on only 16 pins at any given time. For example, pins PA1 and PB1 cannot be used as interrupt pins at the same time, but PA1 and PB2 can. PA1 and PA2 can also be used with interrupts simultaneously.

## Features
* Low power modes including three independently controllable power domains
* RTC
* Watchdog
* Threading
* TCP/IP with SSL
  * Full .NET socket interface
  * Ethernet
  * PPP
* Graphics
  * Images
  * Fonts
  * Controls
* File System
  * Full .NET file interface
  * SD cards
  * USB drives
* Native extensions
  * Runtime Loadable Procedures
  * Device register access
* Signal controls
  * Generation
  * Capture
  * Pulse measurement
    
## SCM20260N Pinout
[SCM20260N Pinout](pdfs/scm20260n.pdf)

## SCM20260E Pinout
[SCM20260E Pinout](pdfs/scm20260e.pdf)

## SCM20260D Pinout
[SCM20260D Pinout](pdfs/scm20260d.pdf)                                                                                                   

## Getting Started
As the SITCore modules are based on the SITCore chipset, please refer to the [SITCore SoC page](soc.md) for information on device startup, loading TinyCLR OS firmware, and writing and deploying your application.

## Design Considerations

### Footprints

We recommend no traces or vias under the module. Dimensions are in inches.

#### SCM20260N Recommended Footprint
![SCM20260N Pinout](images/g120-footprint.jpg)

#### SCM20260E Recommended Footprint
![SCM20260E Footprint](images/scm20260e-footprint.jpg)

### SCM20260D SO-DIMM Socket
![200 pin DDR2 SO-DIMM socket](images/200-pin-ddr2-so-dimm.jpg)

The SCM20260D uses the same 200 pin SO-DIMM socket that was originally made for DDR2 memory modules. You can make a custom SO-DIMM SITCore circuit board by adding the appropriate SO-DIMM socket to your circuit board.

> [!Tip]
> Make sure to expose the required pins in your design. Specific pins are needed for device programming, updates, recovery, and WiFi firmware updates. See device specifications for details.

SO-DIMM stands for Small Outline Dual Inline Memory Module. There are two different 200 pin SO-DIMM sockets, those made for DDR memory and those made for DDR2 memory. They are identical except for the orientation notch which is in a slightly different position. These sockets are not interchangeable. There is also a 204 pin SO-DIMM socket for DDR3 memory with the notch positioned closer to the center of the module.

> [!Note]
> Our UCMs are only compatible with DDR2 type 200 pin SO-DIMM sockets.

Here is a link to the manufacturer's web page for the connector we use on our boards: [EMBOSS ASSY DDR2 SODIMM SOCKET 200P 5.2H](http://www.te.com/usa-en/product-1565917-4.html)

### Required Pins
Exposing the following pins is required in every design to enable device programming, updates, and recovery:
* LDR
* APP
* Reset
* Desired debug interface(s)
* MODE if required to select a debug interface

### Power Supply
A typical clean power source, suited for digital circuitry, is needed to power the SITCore SoMs. The voltage should be within 10% of 3.3 volts.

### Reset
The reset pin is not pulled in any direction. Designs must be sure to use an appropriate pull-up resistor.

### Oven Reflow Profile

SITCore SoMs are not sealed for moisture. Baking modules before reflow is recommended and required in a humid environment. The process of reflow can damage the SoM if the temperature is too high or exposure is too long.

The lead-free reflow profiles used by GHI Electronics are shown below. The profiles are based on AIM SAC 305 solder (3% silver, 0.5% copper). The thermal mass of the assembled board and the sensitivity of the components on it affect the total dwell time. Differences in the two profiles are where they reach their respective peak temperatures as well as the time above liquids (TAL). The shorter profile applies to smaller assemblies, whereas the longer profile applies to larger assemblies such as back-planes or high-density boards. The process window is described by the shaded area. These profiles are only starting-points and general guidance. The particulars of the oven and the assembly will determine the final process.

[![Reflow Chart](../netmf/images/reflow-profile.gif)](http://files.ghielectronics.com/downloads/Documents/Datasheets/WS483%20SAC305%20Solder%20Paste%20Datasheet.pdf)


## SITCore Dev Boards

We offer SITCore development boards to get you started as quickly and easily as possible. These boards allow you to start programming in minutes, and are suitable for both prototypes and production. Click [here](dev.md) for details.
