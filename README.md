# CHAMP Firmware
A lightweight implementation of [CHAMP](https://github.com/chvmp/champ) quadruped controller on Teensy series boards. This has been tested on Teensy 3.1, Teensy 3.6, and Teensy 4.0.

For this to work, you need to have a configuration package generated by the [Setup Assistant](https://github.com/chvmp/champ_setup_assistant) that contains a pseudo URDF to help the controller understand the semantics of your robot during runtime.

If you don't have a physical robot yet and would want to get the controller running in simulation you can use CHAMP's [configuration package](https://github.com/chvmp/champ/tree/master/champ_config) or the preconfigured robots found [here](https://github.com/chvmp/robots/tree/master/configs).
## 1. Dependencies

Install [PlatformIO](https://platformio.org/install/cli) 

## 2. Linking your configuration package

Go to your configuration package folder and source the setup.bash. This helps the firmware to find the include path of the pseudo URDF generated by the setup assistant.

    cd <your_package_configuration_folder>
    source setup.bash

## 3. Configuring gait paremeters and hardware components

### Gait Parameters

Gait paremeters can be configured in gait_config.h found in the configuration package.

    cd <your_config_package>/include
    nano gait_config.h

### Hardware Configuration

Enabling the hardware components used in your build can be done in hardware_config.h found in the configuration package.

     cd <your_config_package>/include
    nano hardware_config.h

The generated config file is in simulation mode by default so you don't have to configure anything if you just want to run in simulation.

## 4. Compiling

On the same terminal where you sourced the configuration package's bash file, run:

    cd firmware
    pio run -e <teensy_board>

where teensy_board can be:
- teensy31
- teensy36
- teensy40

For example, compiling the code for Teensy 4.0 board will be: 

    pio run -e teensy40

## 5. Uploading the firmware

On the same terminal where you sourced the configuration package's bash file, run:

    pio run --target upload -e <teensy_board>