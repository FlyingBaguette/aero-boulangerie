# Software requirements specification

Contents
- [Introduction](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#introduction)
- [System overview](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#system-overview)
- [The Product](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#the-product)
- [User Interfaces](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#user-interfaces)
- [Hardware interfaces](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#hardware-interfaces)
- [Software interfaces](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#software-interfaces)
- [Communication Interfaces](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#communication-interfaces)
- [Memory Constraints](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#memory-constraints)
- [Product Functions](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#product-functions)
- [User Characteristics](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#user-characteristics)
- [Constraints, assumptions and dependencies](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#constraints,-assumptions-and-dependencies)
- [Specific requirements](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#specific-requirements)
- [Software System attributes](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#software-system-attributes)
- [Portability](https://github.com/FlyingBaguette/aero-boulangerie/blob/master/docs/requirement-specs/Software-requirements-specification.md#portability)

##Introduction
This doucment describes the function software design specfication for the "aero boulangerie".

##System overview
The software handles the control of the drone as well as reading various sensors and communications to ensure stable flight and remote commands.

##The Product
###User Interfaces
The user will interface with the drone in 2 ways.
* Local control - This is done within the range of the choosen local communication medium allow the user to take direct control of the drone for flight control but the software will still keep things in check e.g. stability.
* Remote control - This is for remote missions e.g. a misson planner. For example a number of setpoints (lat, long, altitute etc) would be setup to allow the drone to remotely fly to the destination and carry out any desired functions.

###Hardware interfaces
The drone would use 1 main CPU supporting 32 bit precision at resonable speed. A backup CPU could be used for either offloading overhead to GPIO or handling CPU heavy tasks such as a video camera. The main CPU would need to a least support 1 I2C bus, preferably 2 or 3.

The whole system where possible will run at 3.3V to ensure low power consumption.

Gyroscopes/Accelerometers should use a 3 voting system with them being flight critical sensors to ensure accurate sensor readings as well as able to tolorate a single sensor failure. Must support I2C bus.

The main communication method will be I2C.

SD card support for a "black/bread box" will be used for flight logging. This also allows for mission planner saved data as well as remote/images and possible video support.

Motor control hardware will be detailed at a later stage, as will the method for rotating the propellor motors.
GPS module (with magnometer potentially) for remote flight, I2C bus.

Standard GPIO for things such as relay control, LED outputs, PWM outs, high powered light etc.

Ultrasonic sensors for close range object detection. Preferable I2C bus but could use the analgoue ADC in a pinch.
Altuitute sensor to measure height, I2C bus.

Local communcation to use a wifi/bluetooth module, I2C.

3G/4G module to support remote communications, I2C.


###Software interfaces
To be defined once CPU has been choosen...

###Communication Interfaces
I2C predonmantly. Though SPI, UART and others are possabilities if I2C bus becomes heavily used.

###Memory Constraints
512kb of flash memory for the program.
SD card support.

###Product Functions
* Fly in the usual quad copter drone method.
* Fly in forward flight.
* Wireless communcate with a controller/base station.
* Carry out commands from the controller/base station.
* Log flight data.

###User Characteristics
The user will be able to either locally/manually control the drone with software assistance or have the ability to upload mission plans etc.

###Constraints, assumptions and dependencies
To write...

###Specific requirements
####Functional requirements
* Requirement 1
* Requirement 2

####Performance requirements
* Requirement 1
* Requirement 2

####Design Constraints
* Requirement 1
* Requirement 2

###Software System attributes
####Reliability
test text test test test text

####Availability
test text test test test text

####Security
test text test test test text

####Maintainability
test text test test test text

####Portability
test text test test test text
