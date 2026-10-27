# Embedded Driver

This driver integrates the LIS3DH accelerometer and NeoMatrix LED board with the Adafruit Feather RP2040. The Feather RP2040 is based off of the Raspberry Pi Pico. The LIS3DH driver intializes the device to send measurements over I2C. The NeoMatrix driver powers and initializes the NeoMatrix board to receive and display pixel values. 

An example program `level.cpp` is included in this repository. It detects tilt with the accelerometer and turns on a red LED on the NeoMatrix that corresponds to the angle of the tilt. If there is no tilt, then the four center LEDs will display a green hue.

## Directory Structure

This directory contains:
- A *src* directory, containing all the source code.
- `CMakeLists.txt` and `pico_sdk_import.cmake`. These are used for building source code.
- **IMPORTANT**: While it is not included in this repository, it is required to have the *pico-sdk* repository in the root (*embedded_driver*) directory.

## Prerequisites
- Linux or Windows with WSL.
- *pico-sdk* in the root directory.

## Building & Loading

1) Start from the *embedded_driver* root directory.
2) Clone *pico-sdk* to the root directory. 
3) `mkdir` and `cd` into a build directory.
4) From *build*, specify the path to the pico-sdk directory with the exact command:

<p align="center"><code>export PICO_SDK_PATH=../pico-sdk</code></p>

5) To build, run the following:

<p align="center"><code>cmake -DPICO_BOARD=adafruit_feather_rp2040 ..</code></p>

6) Run `make` to produce the required files. We are interested in `level.uf2` in particular.
7) Start the Feather RP2040 in BOOTSEL mode.
8) Drop `level.uf2` (or any executable) into the *RPI-RP2* drive. The Feather RP2040 will begin executing automatically.