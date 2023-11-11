# KUSBA PRO (Nozzle KUSBA)
![](./Images/PCB.jpg)
DeScRiPtIoN

## Purchasing a KUSBA PRO
### United States
- [Isik's Tech](.) (Me)
### European Union
- [Lab4450 - Portugal](.)

This project is licensed under [GPL v3](./LICENSE), meaning vendors are allowed to sell PCBs without paying me. If you'd like to support the development of this and future projects please consider [sponsoring](https://github.com/sponsors/xbst) me on GitHub. You can also subscribe on [Patreon](https://l.isiks.tech/patreon) or [YouTube](https://l.isiks.tech/member).

You can also use the included gerber files to order your own from a PCB manufacturer like [PCBWay](https://www.pcbway.com/setinvite.aspx?inviteid=374841) or [JLCPCB](https://jlcpcb.com/) and you can order the MJF mount from a 3D printing company like [JawsTec](https://www.jawstec.com/3d-printing-service/?aff=6).
<br>

## Instructions

- [Firmware flashing](./Docs/Firmware.md)
- [Measuring resonances](./Docs/Usage.md)
- [Assembling PCB and MJF mount](./Docs/Mount.md)

## KUSBA v2 vs PRO

|             |KUSBA PRO|KUSBA v2.4|
|-------------|---------|----------|
|Picture      |         |          |
|MCU          |STM32F042|RP2040    |
|Accelerometer|LIS2DW   |ADXL345   |
|3.3V Regulator|LP5907MFX-3.3|AMS1117-3.3|
|Flash        |N/A      |W25Q16JVSNIQ|
|Connector    |USB C    |USB C     |
|Firmware     |Klipper  |Klipper, Rampon|
|PCB Size     |26.0 x 17.6 mm|34.0 x 25.0 mm|
|Smallest SMD |0201     |0402      |

## Folders

Delete this.

| Folder | For |
| ------ | --- |
| CAD | CAD models of the PCB and mounts |
| Docs | Guides, extra docs |
| EasyEDA-Source | Source .json files, in version folders |
| Firmware | Klipper .cfg files, if multiple options available, in sub folders |
| Gerbers | Gerbers in `Gerbers.zip`, BOM in `BOM.csv`, CPL in `PNP.csv`|
| Images | Images for docs |
| Mounts | Mounts for the PCB, add a `README.md` |

## YouTube

I am a YouTube content creator. If you want content about these projects & more, please consider [subscribing to my YouTube channel](https://www.youtube.com/channel/UClAWYmCkHjsbaX9Wz1df2mg).
<br>

If you feel like contributing to the development of this project and other projects like this you can sponsor me on [GitHub](https://github.com/sponsors/xbst), subscribe on [Patreon](https://l.isiks.tech/patreon) or [YouTube](https://l.isiks.tech/member).

## Notes
- Readme files in this repo may contain Amazon Associate, Aliexpress affiliate, PCBWay affiliate, JawsTec affiliate links. I make a comission on qualifying purchases.
- This project does not come with any warranty, if you choose to build/use a PCB manufactured using published files in this repository, you are doing this at your own risk!
- If you want to sell PCBs manufactured using published files in this repository, you are allowed to, and you will not owe me any royalties. **You cannot claim that I endorse the sale**. You can check the license file for more information. However, if you **wish** to give me a share you can sponsor me on [GitHub](https://github.com/sponsors/xbst), subscribe on [Patreon](https://l.isiks.tech/patreon) or [YouTube](https://l.isiks.tech/member).
