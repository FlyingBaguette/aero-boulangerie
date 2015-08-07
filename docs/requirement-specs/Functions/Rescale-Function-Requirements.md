# Rescale Function Requirements
## Intro
This function is used for converting units set in one scale into another, for example coverting fahrenheit into celsius. The function must be able to continue to convert beyond the max and min limits of the rescale. This way it also doubles as a liniar scaling function.

## Major functions
* Convert a set of input data into a new scale.
* Not be limited by the min/max scale.
* Accept real numbers

## I/O listing for the object/add on instruction.
### Inputs
* iInputvalue: REAL the value which is to be coverted to a new scale.

### Settings
* sInputLowerDB: REAL the lower deadband (minium) value of the input scale.
* sInputUpperDB: REAL the upper deadband (minium) value of the input scale.
* sOutputLowerDB: REAL the lower deadband (minium) value of the output scale.
* sOutputUpperDB: REAL the upper deadband (minium) value of the output scale.

### Outputs
* oOutputScale: REAL the rescaled value result.
