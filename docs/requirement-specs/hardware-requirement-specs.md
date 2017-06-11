# Hardware requirements specification

Contents
- [Introduction](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/hardware-requirement-specs.md#introduction)
- [Build requirements](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/hardware-requirement-specs.md#build-requirements)
- [Performance requirements](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/hardware-requirement-specs.md#performance-requirements)

## Introduction
This document identifies a list of requirements to ensure the correct hardware is selected for its purpose.

## Build requirements
 - The entire drone to weigh under 3kg preferably 2/2.5kg
 - Be resilient to rain and weather conditions
 - Have "wings" that produce lift
 - Have an aerodynamic body to reduce drag
 - Be able to carry at least 2x 11.1V 3000mah batteries
 - Payload "area" to house more batteries or other equipment
 - A motherboard that houses and connects all other electronics/sensors
 - 4 Motors to create lift in hover mode and allow forward momentum when in flight mode.
 - Elivators if required to allow control in normal (none hover) flight.

## Performance requirements
It is expected that the processor can:
 - Perform 32 bit calculations
 - Run a RTOS
 - Store a RTOS in memory (FreeRTOS takes 10KB, uC/OS-III takes 24KB)
 - Interface with multiple sensors (Minimum 4) over a industry recognised bus e.g. I2C
 - Have a clock speed high enough to handle wireless communication whilst recording sensor data.
 - Interface with SD card
 - Low power consumption from devices
 - Allow for different devices to be split onto different communication channels e.g. each gyroscope and accelerometer "pair" would be on a separate I2C channel.
 
It is expected that each sensor should be able to:
 - Have a reading resolution that is not bigger than the processor architecture
 - Report readings at least twice per second, at least 10 times a second for accelerometers and gyroscopes.
 - Communicate on a bus supported by the chosen processor (Likely I2C or SPI)
 
The following requirements are listed as 'Desirable' and can be omitted:
 - Camera module, separate to the main control circuits in its entirety to ensure no communication channels etc get overloaded.
 - In the payload area to have a simple interface to allow extra equipment to power itself and interface with the drone e.g. for the breadbox data logger. This would also include extra batteries plugging into the system for longer flight times.

