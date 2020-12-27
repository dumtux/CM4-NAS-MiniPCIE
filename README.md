**Rapberry PI compute module 4 NAS PCB for using JLCPCB.com. (pre-test version)**

#General view of PCB based on processing gbr files on JLCPCB.com

![PCB_view](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/JLC%20PCB%20gbr%20render%20small.png)

Main purpose of design is to make NAS with more reliable SATA connection comparing to USB-to-SATA converters. SATA controllers can be connected through MiniPCIe slot. There are variety of cards in market, mainly my intend was to use this for 2 SATA (see picture below). This is half size card. Cards for 4 SATA with RAID controller also can be connected. 

**Design is made using nighly version of KiCAD 5.99.0**
**Please study Raspberry PI CM4 datasheet**

![card](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/MiniPCIecard.png)

# Differential lines
*PCB was designed by a newcomer. All steps made are listed below. This section is very important and risky. Mistakes can be made.  90 R and 100R impedance differential lines are used.Calculations of differential lines are made using JLCPCB internal [calculator](https://cart.jlcpcb.com/impedanceCalculation)*

Results of calculation - [90R](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/JLCPCB%20Impedance%2090R.png) and [100R](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/JLCPCB%20Impedance%20100R.png)

Those results put in KiCAD.
![KiCAD_Layers](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/KiCAD%20Layers.png)

JLC7628 [Stackup](https://cart.jlcpcb.com/impedance) used all settings transfered to [KiCAD stackup](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/KiCAD%20Stack.png)

All vias minimal diameter is 0.45 as price will be much higher for VIAs of less size.

# PCB description
## Sockets on PCB
- MiniPCIe slot (designed for hlaf-size cards)
- HDMI in order to use device as media player
- Gigabit LAN
- SD card slot for using CM4’s without eMMC
- USB A 2.0 socket for connecting periphery like Zigbee.
- MicroUSB for installing firmware to CM4 and power supply.
All sockets placed on top edge of PCB for more reliable use and easy design of 3D print case.

## Footprints
All sockets footprints selected to be most common. In standard library of  KiCAD I did not found suitable MicroSD socket. And ofcource footprint of CM4 is also taken from Raspberry PI CM4 IO borad. All external footprints are in folder LIBS.
I wanted to install all sockets on one side of the board and there was not much space. MicroUSB socket I put on other side of the board below HDMI. I assumed that for installing firmware you do not need HDMI. May be it is better to put in below microSD card?

## On board connectors.
### Power input. 
There are 2 connectors with 4 pins (GND, +12V, +5V, +3.3V) Connectors can be used for powering board and soldering cable for powering HDDs. 
- +12 V is only used for HDD. Board has 2 interconnected pins, but level +12 V not used on board. MiniPCIe does not have +12V input.
- +5V used for powering CM4 module and giving power to USB and HDMI. Two SMD resettable fuses installed to protect board from short circuit. 
- +3.3 V used for powering PCI-to-SATA module. MiniPCIe slot has connection for another level of voltage.
- 1.5 V. Special connector made above PCIe slot.  Generaly this level is not required. It is planned to use SATA module based on chip ASM1061 that has [Integrated 3.3V to 1.2V switch regulator](https://www.asmedia.com.tw/eng/e_show_products.php?cate_index=166&item=118). 

Initial CM4 IO Borad has more copmplicated power system with different ICs for protecting not only from short circuit but, under voltage, overload etc.

### GPIO.
Left side of board has GPIO connector and small connector for selecting level of GPIO (GPIO_Vref)
- GPIO 2
- GPIO 3
- GPIO 4
- GPIO 12
- GPIO 15
- GPIO 14


### Service conections and LEDs
There is a connector with following signals
- nRPIBOOT
- PI_POWER_LED
- Global_EN
- nEXTRST
- Analog_P1
- Analog_P0
- RUN_PG
- PI_N_LED

### Other connectors
- USG_OTG connector used to connect USB_OTG_ID pin of CM4 for installing firmware to eMMC. 
- USB hub connecor Connector with 4 pins GND, D+, D-, +5V can be used to connect external USB hub if you need it in your project.
- MiniPCIe USB D+/D-. MiniPCIe slot also has connections for D+ and D- another connector used for it. This is not connected to CM4 D+/D- lines.
- One GND connector just for the case.

### KiCAD view
Front
![Front](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/KiCAD%20PCB%20Front.png)

Back
![Back](https://raw.githubusercontent.com/olvint/CM4-NAS-MiniPCIE/main/PICS/KiCAD%20PCB%20Back.png)







