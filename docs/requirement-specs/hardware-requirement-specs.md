# Hardware requirements specification

Contents
- [Introduction](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/hardware-requirement-specs.md#introduction)
- [Performance requirements](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/hardware-requirement-specs.md#performance-requirements)
## Introduction
This document identifies a list of requirements to ensure the correct hardware is selected for its purpose.

## Performance requirements
It is expected that the processor can:
 - Perform 32 bit calculations
 - Run a RTOS
 - Store a RTOS in memory (FreeRTOS takes 10KB)
 - Inteface with multiple sensors (Minimum 4) over a industry recognised bus
 - Have a clock speed high enough to handle wireless communication whilst recording sensor data
 - Inteface with SD card
 - 
 
It is expected that each sensor should be able to:
 - Reading resolution that is not bigger than the processor architecture
 - Report readings atleast twice per second
 - Communicate on a bus supported by the chosen processor (Likely I2C or SPI)
 
The following requirements are listed as 'Desirable' and are not needed to be fulfilled:
 - Have a clock speed high enough to operate a camera module
 - 
