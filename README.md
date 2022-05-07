# Reflow
This is a reflow oven controller based on ideas from ReflowMaster and is intended to work with a kitchen style toaster oven, but can also be adapted to a quartz heater or halogen lamp hack.

![](plots/reflower.svg)

### Control Scheme
The MCU first needs to know how fast the temperature rises at full power, as a mearsure of thermal mass. This value is stored in an internal non-volatile memory.

The based on this, the MCU turns on the load for a certain number of AC cycles, calculated by scaling the duration of the calibration to 10 cycles. After this if the temperature is more than what the calibration curve was, we start reducing the number of cycles. If it is less, we just turn power on and check again after 10 cycles.

This is not a particularly refined or accurate scheme yet, mainly due to my decision to forego having mains voltages on this board and control using SCR phase control.