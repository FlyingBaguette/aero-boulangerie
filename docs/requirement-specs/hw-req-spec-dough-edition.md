# Hardware requirements specification Dough Edition

Contents
- [Introduction](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/hw-req-spec-dough-edition.md#introduction)
- [Build requirements](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/hw-req-spec-dough-edition.md#build-requirements)
- [Performance requirements](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/hw-req-spec-dough-edition.md#performance-requirements)

## Introduction
This document identifies a list of requirements for the "Dough" edition of aero boulangerie. The "Dough" edition will be the first prototype with only critical/major functionallity included in the design.

## Build requirements
 - The entire drone to have a low weight to aid in flight time and motor spec.
 - Have "wings" that produce lift
 - A crude aerodynamic body to protect internal components at speed.
 - Be able to carry at least 2x 11.1V 3000mah batteries
 - Be able to carry all of its own eletronics.
 - A simple Payload "area" to house more batteries or other equipment such as testing equipment.
 - 4 Motors to create lift in hover mode and allow forward momentum when in flight mode.
 - 2 or 4 Servos to handle motor/wing rotation.
 - Elevators to allow control in normal (none hover) flight.

## Performance requirements
It is expected that the processor can:
 - Perform 32 bit calculations
 - Interface with multiple sensors (Minimum 3: Radio reciever, Accelerometer and Gyroscope) over a industry recognised bus e.g. I2C
 - Have a clock speed high enough to handle wireless communication/radio communication.
 
It is expected that each sensor should be able to:
 - Have a reading resolution that is not bigger than the processor architecture
 - Report readings at least twice per second, at least 10 times a second for accelerometers and gyroscopes.
 - Communicate on a bus supported by the chosen processor (Likely I2C or SPI)
 
The following requirements are listed as 'Desirable' and can be omitted:
 - In the payload area to have a simple interface to allow extra equipment to power itself and interface with the drone e.g. for the breadbox data logger. This would also include extra batteries plugging into the system for longer flight times.

