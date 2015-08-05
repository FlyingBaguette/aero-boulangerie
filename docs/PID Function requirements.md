# PID Function requirements
## Intro
The PID used in my previous quad copter project did the job but was missing alot of features which would give far better control. The main one of these was it was missing a sample time rate and as such ran as fast as the Ardunio could run. This caused the integral to become unusable as it would even for small values ramp at incredibly fast rates and as such would cause the quad copter to crash. This version also did not use real/float numbers being on a 8 bit AVR processor which lead to a trade off between efficiency (using 16 bit numbers) or accuracy (32 bit floats).

The new version detailed here is to overcome these major flaws with my original implementation.

## Major functions
* Proportionally adjust the outputs of each motor individually dependent on angle.
* Use integral to increase ramp rate over time.
* Use derivative to remove unwanted oscillation.
* Have a task rate for the PID.
* Use Float/Real numbers (now much more possible thanks to the 32 bit CPU and high speed).
Be integrated as an object/add on instruction to allow the code to be used many times and for different scenarios.

## I/O listing for the object/add on instruction.
### Inputs
* iEn: BOOL Enable PID control
* iFeedbackValue: REAL Current reading 
* iTarget: REAL Desired target

### Settings
* sP: REAL P value
* sI: REAL I value
* sD: REAL D value
* sInvertOutputs: BOOL Outputs need to react opposite to the feedback check this flag

### Outputs
* oOutputValue: REAL Output to create the change required to get the feedback to match the target.

[Good PID Example and tutorial](http://brettbeauregard.com/blog/2011/04/improving-the-beginners-pid-introduction/)
