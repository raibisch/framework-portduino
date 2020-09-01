# Portduino

This is an experiment with getting the Arduino API so that it can run on top of the Linux OS.

You don't want this yet ;-)

## Description

Someone wanted Meshtastic for a new linux based tablet, so I'm making a new new thing (which might be useful for other projects).

I'm going to implement the arduino libs/API layer and support the following device level access from (blessed) user-space regular apps:

- SPI
- I2C
- Interrupt handlers (they won't know they are actually in userspace)
- GPIO control
- Serial (but actually being done through any Unix file descriptor - so could be pipes/files/devices)
- Any of the above can be implemented by particular 'Drivers' - so either the mainboard kernel-space SPI/I2C controller or via external USB to SPI/I2C/GPIO adapters

(This is the portion of Arduino that my project needs - and I bet this is sufficient for most Arduino projects)

## Secondary goals

Eventually a variant of this library will allow removing SoftDevice from the NRF52 targets - for a dramatic flash/RAM savings (this will be built on top of [Apache MyNewt](https://mynewt.apache.org/))

## TODO (short term)

- Use https://github.com/arduino/ArduinoCore-nRF528x-mbedos as a model?
- Get hello world building as an app
- Add SimGPIO
- Add SimSPI
- Add SimI2C
- Build and run Meshtastic on top of this new framework
- Add CS341SPI driver (USB to SPI chip)
- Implement InterruptHandler via threads
- Have meshtastic talk to radio over that chip

## TODO (long term)

- Announce and request feedback
- Change into an actual real platformio "framework"
- Send in platformio PR
- Make a variant that runs on top of MyNewt
- Unify Threading wrappers with the FreeRTOS versions
