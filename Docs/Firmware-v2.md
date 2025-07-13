# KUSBA Pro v2 (ADXL345) Instructions
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
[*] Enable extra low-level configuration options
    Micro-controller Architecture (STMicroelectronics STM32)  --->
    Processor model (STM32G431)  --->
    Bootloader offset (No bootloader)  --->
    Clock Reference (8 MHz crystal)  --->
    Communication interface (USB (on PA11/PA12))  --->
    USB ids  --->
()  GPIO pins to set at micro-controller startup (NEW)
```
7. Exit by typing `Q`, save by pressing `Y`.
8. Build the firmware: `make`
9. Find the ID of your KUSBA PRO in DFU mode using `lsusb`. It should be the device appearing as `STM Device in DFU mode`.
10. Flash the firmware: `make flash FLASH_DEVICE=1234:5678`. Replace `1234:5678` with the ID you found in the above step.
11. Use `ls /dev/serial/by-id/*` to find the serial address of your KUSBA PRO. It'll start with: `usb-Klipper_stm32g431`
12. [Download the `adxlmcu.cfg` file from this repository](https://github.com/xbst/KUSBA-PRO/blob/master/Firmware-v2/adxlmcu.cfg).
13. Upload the `adxlmcu.cfg` file to your config directory. You can do this on Mainsail/Fluidd etc.
14. Edit the `adxlmcu.cfg` file (in Mainsail/Fluidd). Change the MCU serial address (step 12) and the probe points.
15. Save and close.
16. If your KUSBA PRO isn't assembled follow the [assembly](./Mount.md) doc first.
17. Edit your `printer.cfg` file. Add:
```
[include adxlmcu.cfg]
```
18. Do your input shaper testing. When done comment the include line to disable the KUSBA PRO. (If you don't do this and unplug the KUSBA PRO, Klipper won't work.)
```
# [include adxlmcu.cfg]
```
