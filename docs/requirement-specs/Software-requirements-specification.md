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
- I2C to cover sensor communications
- SPI required for SD card interfacing

UART and others are possabilities if I2C bus becomes heavily used.

The  wireless communications will conform to a defined protocol that needs to handle
- Handshake to establish connection
- Control commands
- Sensor identifier with reading
- Close connection


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
* Create radio link connection: User/passwords could be stored on SD card with a "admin" user/pass stored within the program. A simple pairing mathod can be used to ensure both devices get data from other sources but we could look into adding encryption as a future feature.
* Apply instructions from controller to actuators.
* Use readings from sensors to improve stabilisation

####Performance requirements
* Radio must have the bandwidth to transfer telemetry data of all sensors atleast once per second 
* Program must run fast enough and with a quick enough reponse time to keep the drone controlled in flight.

####Design Constraints
* Requirement 1
* Requirement 2

###Software System attributes
####Reliability
The software must remain responsive to new commands and be able to service a kill command at all times. Deadlock risk and WCET will be calculated to ensure the software is architected in a reliable manor. Task watchdogs are a must. Backup/redudant CPU could also help with this.

####Availability
* After boot-up cycle the software needs to be consistantly avlaible to allow new commands encription/message pairing pending.

####Security
* The main attack vector for AB will be the wireless communications. Encryption and a form of authenication would provide some degree of security to prevent a malicous user snooping sensor data and/or taking control of the aircraft. The downside to implementing these features would be the impact on responsiveness.

####Maintainability
* Code should be construction in such a way to allow easy debug finding and feature addition.
* Code should only ever be uploaded when the batteries are dissconnected. Doing so while power on the motors can lead to undesired behaviour for example on GF's drone upon new code downloaded to thr ardunio while powered the motors will go to 100% throttle uncontrolled for around 10 seconds.

####Portability
* Could should be easily uploadble to AB when powered off and in a safe manner.
