# KUSBA PRO Firmware Flashing

Note: Make sure to use an up-to-date version of Klipper with LIS2DW accelerometer support.

<br>

<details>
  <summary>Klipper Prep. (enabling resonance testing)</summary>
  
0. Run the following commands in order. This will take some time. (Based on the [official Klipper docs](https://www.klipper3d.org/Measuring_Resonances.html#software-installation))
```
~/klippy-env/bin/pip install -v numpy
sudo apt update
sudo apt install python3-numpy python3-matplotlib libatlas-base-dev
```

</details>

<br>

1. Connect your KUSBA PRO via a USB cable to your Raspberry Pi while holding down the button.
2. SSH into your Raspberry Pi.
3. Go to the Klipper directory: `cd ~/klipper`
4. Clean remaining files from previous build: `make clean`
5. Choose the options for the build: `make menuconfig`
6. Use these settings:
```
[ ] Enable extra low-level configuration options
    Micro-controller Architecture (STMicroelectronics STM32)  --->
    Processor model (STM32F042)  --->
    Bootloader offset (No bootloader)  --->
    Communication interface (USB (on PA11/PA12))  --->
    Optional features (to reduce code size)  --->
```
7. Enter the `Optional features (to reduce code size)` menu. Disable LCD devices:
```
[*] Support GPIO "bit-banging" devices
[ ] Support LCD devices
[*] Support external sensor devices
[*] Support lis2dw 3-axis accelerometer
[*] Support software based I2C "bit-banging"
[*] Support software based SPI "bit-banging"
```
8. Exit by typing `Q`, save by pressing `Y`.
9. Build the firmware: `make`
10. Find the ID of your KUSBA PRO in DFU mode using `lsusb`. It should be the device appearing as `STM Device in DFU mode`.
11. Flash the firmware: `make flash FLASH_DEVICE=1234:5678`. Replace `1234:5678` with the ID you found in the above step.
12. Disconnect your KUSBA PRO. Connect it again.
13. Use `ls /dev/serial/by-id/*` to find the serial address of your KUSBA PRO. It'll start with: `usb-Klipper_stm32f042`
14. [Download the `adxlmcu.cfg` file from this repository](../Firmware/adxlmcu.cfg).
15. Upload the `adxlmcu.cfg` file to your config directory. You can do this on Mainsail/Fluidd etc.
16. Edit the `adxlmcu.cfg` file (in Mainsail/Fluidd). Change the MCU serial address (step 13) and the probe points.
17. Save and close. If your KUSBA PRO is assembled already move to the [measuring resonances](./Usage.md) doc, otherwise follow the [assembly](./Mount.md) doc first.