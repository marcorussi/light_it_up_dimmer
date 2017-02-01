# ble_led_dimmer
A 4 channels LED dimmer over BLE based on Nordic nrf51 chipset. Developed under Ubuntu environment using a nrf51 PCA10028 development kit and a custom board. The firmware is based on S130 from Nordic SDK 11.x.x.

This firmware allows to control 4 LED channels by scanning a compatible advertising packet from a controller device. The controller advertises its current state and the driver associates the scanned value with 4 PWM values that are actuated at every new controller state.
Refer to doc.txt file. 


**Install**

Download Segger JLink tool from https://www.segger.com/jlink-software.html. Unpack it and move it to /opt directory.
Download the Nordic SDK from http://developer.nordicsemi.com/nRF5_SDK/nRF5_SDK_v11.x.x/. Unpack it and move it to /opt directory.

Clone this repo in your projects directory:

    $ git clone https://github.com/marcorussi/light_it_up_dimmer.git
    $ cd light_it_up_dimmer
    $ gedit Makefile

Verify and modify following names and paths as required according to your ARM GCC toolchain:

```
PROJECT_NAME := ble_led_dimmer
NRFJPROG_PATH := ./tools
SDK_PATH := /opt/nRF5_SDK_11.0.0_dc26b5e
LINKER_SCRIPT := led_dimmer_nrf51.ld
GNU_INSTALL_ROOT := /home/marco/ARMToolchain/gcc-arm-none-eabi-4_9-2015q2
GNU_VERSION := 4.9.3
GNU_PREFIX := arm-none-eabi
```

**Flash**

Connect your nrf51 Dev. Kit, make and flash it:
 
    $ make
    $ make flash_softdevice (for the first time only)
    $ make flash

You can erase the whole flash memory by running:

    $ make erase


**DFU Upgrade**

For creating a .zip packet for DFU upgrade run the following command:

nrfutil dfu genpkg liu_dimmer.zip --application ble_led_dimmer_s130.hex --application-version 0xffffffff --dev-revision 0xffff --dev-type 0xffff --sd-req 0xfffe

IMPORTANT: nrf-util version must be 0.5.2 or lower.


