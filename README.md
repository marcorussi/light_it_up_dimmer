# ble_led_dimmer
A RGBW LED dimmer over BLE based on Nordic nrf51 chipset. Developed under Ubuntu environment using a nrf51 PCA10028 development kit. The firmware is based on S130 from Nordic SDK 11.x.x.

This firmware allows to control a RGBW LED strip by scanning a compatible advertising packet from another device.


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

