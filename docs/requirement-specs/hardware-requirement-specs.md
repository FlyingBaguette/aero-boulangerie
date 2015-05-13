# Hardware requirements specification

Contents
- [Introduction](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/hardware-requirement-specs.md#introduction)
- [Build requirements](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/hardware-requirement-specs.md#build-requirements)
- [Performance requirements](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/hardware-requirement-specs.md#performance-requirements)

## Introduction
This document identifies a list of requirements to ensure the correct hardware is selected for its purpose.

## Build requirements
 - The entire drone to weigh under 3kg preferablly 2/2.5kb
 - Be resilliant to rain and weather conditions
 - Have "wings" that produce lift
 - Have an aerodynamic body to reduce drag
 - Be able to carry at least 2x 11.1V 3000mah batteries
 - Payload "area" to house more batteries or other equipment
 - A motherboard which houses and connects all other eletronics/sensors

## Performance requirements
It is expected that the processor can:
 - Perform 32 bit calculations
 - Run a RTOS
 - Store a RTOS in memory (FreeRTOS takes 10KB, uC/OS-III takes 24KB)
 - Inteface with multiple sensors (Minimum 4) over a industry recognised bus
 - Have a clock speed high enough to handle wireless communication whilst recording sensor data
 - Inteface with SD card
 - 
 
It is expected that each sensor should be able to:
 - Have a reading resolution that is not bigger than the processor architecture
 - Report readings atleast twice per second
 - Communicate on a bus supported by the chosen processor (Likely I2C or SPI)
 
The following requirements are listed as 'Desirable' and are not needed to be fulfilled:
 - Have a clock speed high enough to operate a camera module
 - 
