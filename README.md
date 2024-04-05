# ICM42605
Arduino library for communicating with the [ICM42605](https://invensense.tdk.com/products/motion-tracking/6-axis/icm-42605/) six-axis Inertial Measurement Units (IMU).

It is based on the ICM42688 library, as the register interface between the two gyros is almost identical.



# Description
The InvenSense ICM42605 supports I2C, up to 400 kHz, and SPI communication, up to 1 MHz for register setup and 24 MHz for data reading. The following selectable full scale sensor ranges are available:

| Gyroscope Full Scale Range | Accelerometer Full Scale Range |
|----------------------------|--------------------------------|
| +/- 15.6 (deg/s)           | -                              |
| +/- 31.2 (deg/s)           | -                              |
| +/- 62.5 (deg/s)           | -                              |
| +/- 125 (deg/s)            | -                              |
| +/- 250 (deg/s)            | +/- 2 (g)                      |
| +/- 500 (deg/s)            | +/- 4 (g)                      |
| +/- 1000 (deg/s)           | +/- 8 (g)                      |
| +/- 2000 (deg/s)           | +/- 16 (g)                     |

The ICM42605 samples the gyroscopes, and accelerometers with 16 bit analog to digital converters. It also features programmable digital filters, a precision clock, an embedded temperature sensor, programmable interrupts (including wake on motion), and a 2kB byte FIFO buffer.

Refer to the ICM42688 library from which this library forked until the documentation is ported, proof-read and updated.

# Wiring and Pullups

Please refer to the datasheet. This library should work well for other breakout boards or embedded sensors, please refer to your vendor's pinout diagram.

For best results ensure the power supply to the gyro is noise-free, when making custom PCBs follow the guidelines applicable to all MEMS devices
when placing components.  Review application notes from multiple vendors and then make your own decisions.   e.g. do not place directly in-line between mounting holes, etc.

## I2C

The ICM42605 pins should be connected as:
   * 3V3: this should be a 3.0V to 3.6V power source.
   * GND: ground.
   * INT1: (optional) used for the interrupt output setup in *enableDataReadyInterrupt* and *enableWakeOnMotion*. Connect to interruptable pin on microcontroller.
   * SDA: connect to SDA.
   * SCL: connect to SCL.

4.7 kOhm resistors should be used as pullups on SDA and SCL, these resistors should pullup with a 3.3V source.

## SPI

The ICM42605 pins should be connected as:
   * 3V3: this should be a 3.0V to 3.6V power source.
   * GND: ground.
   * INT1: (optional) used for the interrupt output setup in *enableDataReadyInterrupt* and *enableWakeOnMotion*. Connect to interruptable pin on microcontroller.
   * SDI: connect to MOSI.
   * SCK: connect to SCK.
   * SDO: connect to MISO.
   * CS: connect to chip select pin. Pin 10 was used in the code snippets in this document and the included examples, but any digital I/O pin can be used.

Some breakout boards, including the Embedded Masters breakout board, require slight modification to enable SPI. Please refer to your vendor's documentation.
