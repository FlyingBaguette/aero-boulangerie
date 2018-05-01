# Software requirements specification

Contents
- [Introduction](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#introduction)
- [System overview](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#system-overview)
- [The Product](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#the-product)
- [User Interfaces](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#user-interfaces)
- [Hardware interfaces](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#hardware-interfaces)
- [Software interfaces](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#software-interfaces)
- [Communication Interfaces](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#communication-interfaces)
- [Memory Constraints](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#memory-constraints)
- [Product Functions](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#product-functions)
- [User Characteristics](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#user-characteristics)
- [Constraints, assumptions and dependencies](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#constraints,-assumptions-and-dependencies)
- [Specific requirements](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#specific-requirements)
- [Software System attributes](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#software-system-attributes)
- [Portability](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/sw-req-spec-dough-edition.md#portability)

## Introduction
This document describes the function software design specification for the "Dough" edition of aero boulangerie. The "Dough" edition will be the first prototype with only critical/major functionallity included in the design.

## System overview
The software handles the control of the drone as well as reading various sensors and communications to ensure stable flight and remote commands.

## The Product
### User Interfaces
The user will interface with the drone via local control e.g. radio transmitter, this allows the user to take direct control of the drone for flight control but the software will still keep things in check e.g. stability.

### Hardware interfaces
The drone would use 1 main CPU supporting 32 bit precision at reasonable speed. Any extra protocols supported out of the box if ideal.

The whole system, apart from the rotors, will run at 3.3V and 5.5V to ensure low power consumption and a reduction in voltage step changers.

Gyroscopes/Accelerometers should use a 3 voting system with them being flight critical sensors to ensure accurate sensor readings as well as able to tolerate a single sensor failure. Initial version will just use 1 sensor for lower costs. Must support I2C bus preferbally with the higher speeds supported.

The main communication method for any extra addon devices will be I2C.

2.4GHZ Controller/Reciver to be used for local control of the QAD copter. Most 2.4GHZ recivers use PWM to transmit the data.

SD card support for a "black/bread box" will be used for flight logging. This also allows for mission planner saved data as well as remote/images and possible video support.

Motor control hardware will use 4xESC for control of each motor, ESC's are controlled via PWM in most cases and as such the CPU needs to support this. 

The method for rotating the propeller motors will ethier rotate only the motor maybe using 1 servo to move 2 motors via a connecting rod rather than having 1 servo per motor.

Standard GPIO for things such as relay control, LED outputs, PWM outs etc.

### Software interfaces
CPU choosen to be a STMMicro 32bit CPU programmed via Windows/Linux enviroment.

### Communication Interfaces
- I2C to cover sensor communications
- SPI required for SD card interfacing
- Enable printing to the UART to allow for bluetooth module to be used for debugging

UART and others are possibilities if I2C bus becomes heavily used, as such the I2C bus should be set to a high a speed as possible.

### Memory Constraints
512kb of flash memory for the program.
SD card support for data logging, data storage of large data e.g. height maps etc.

### Product Functions
* Fly in the usual quad copter drone method.
* Fly in forward flight.
* Log flight data.

### User Characteristics
The user will be able to locally/manually control the drone with software assistance.

### Constraints, assumptions and dependencies
* Dough version of the product is a highly cut down version to allow focus on the main functionality.

### Specific requirements
#### Functional requirements
* Apply instructions from controller to actuators.
* Use readings from sensors to ensure stabilisation

#### Performance requirements
* Program must run fast enough and with a quick enough response time to keep the drone controlled in flight.

#### Design Constraints
Varibles must used in groups to ensure fast processing and efficent data storage.

### Software System attributes
#### Reliability
The software must remain responsive to new commands and be able to service a kill command at all times.

#### Availability
* After boot-up cycle the software needs to be consistently available to allow new commands encryption/message pairing pending.

#### Security
* The main attack vector for the Dough edition will be the radio communications. Though this is highly low it is more likely interference may interupt local control and as such AB Dough edition needs to e program to handle loss of coms.

#### Maintainability
* Code should be construction in such a way to allow easy debug finding and feature addition.
* Code should only ever be uploaded when the batteries are disconnected. Doing so while power on the motors can lead to undesired behaviour for example on GF's drone upon new code downloaded to the ardunio while powered the motors will go to 100% throttle uncontrolled for around 10 seconds.

#### Portability
* Should be easily uploaded to AB when powered off and in a safe manner.
