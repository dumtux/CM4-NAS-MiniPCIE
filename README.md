# Rapberry PI compute module 4 NAS PCB for using JLCPCB.com. (pre-test version)

General view of PCB based on processing gbr files on JLCPCB.com

![PCB_view](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/JLC%20PCB%20gbr%20render%20small.png)

Main purpose of design is to make NAS with more reliable SATA connection comparing to USB-to-SATA converters. SATA controllers can be connected through MiniPCIe slot. There are variety of cards in market, mainly my intend was to use this for 2 SATA (see picture below). This is half size card. Cards for 4 SATA with RAID controller also can be connected. 

![card](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/MiniPCIecard.png)

## Sockets on PCB
- MiniPCIe slot (designed for hlaf-size cards)
- HDMI in order to use device as media player
- Gigabit LAN
- SD card slot for using CM4’s without eMMC
- USB A 2.0 socket for connecting periphery like Zigbee.
- MicroUSB for installing firmware to CM4 and power supply.
All sockets placed on top edge of PCB for more reliable use and easy design of 3D print case.

## Differential lines
*PCB was designed by a newcomer. All steps made are listed below. This section is very important and risky. Mistakes can be made.  90 R and 100R impedance differential lines are used.Calculations of differential lines are made using JLCPCB internal [calculator](https://cart.jlcpcb.com/impedanceCalculation)*

Results of calculation - [90R](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/JLCPCB%20Impedance%2090R.png) and [100R](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/JLCPCB%20Impedance%20100R.png)

Those results put in KiCAD.
![KiCAD_Layers] (https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/KiCAD%20Layers.png)

JLC7628 [Stackup](https://cart.jlcpcb.com/impedance) used all settings transfered to [KiCAD stackup](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/KiCAD%20Stack.png)

All vias minimal diameter is 0.45 as price will be much higher for VIAs of less size.

