# DECA Retro Cape 2 (2 layer - MiSTer module SDRAM version)

**STATUS** (15/03/22):  prototype desing work finished. v0.71 gerbers sent to JLCPCB for manufacturing.

**STATUS** (07/04/22):  PCBs received. Started testing. Joystick (DB9 and USB3) part must be redesigned in the next release. See end of readme for changelog and improvements from v0.71

Project has been developed with KiCAD 6.0. 

I want to give cretits to Tom Verbeure from whom I've taken his [original design  files](https://github.com/tomverbeure/arrow_deca_retro_cape) and adapted to my own design. Not much have been left from his design, but the name "DECA Retro Cape" remains.  



### **Schematic**

 [arrow_deca_retro_cape.pdf](arrow_deca_retro_cape.pdf) 

### **Features**

* VGA DAC 444
* Terasic 40 pin connector (for Mister SDRAM modules) + 3 pin for Dual SDRAM/SRAM 
* PS2 keyboard & mouse connectors
* Double Pmod (1/2) for peripherals (VGA Pmod, Hyperram, ...)
* Pmod 3 (SPI + UART) host or peripheral 
* DETO Pmod (6 pin) for general usage (3 multiplexed pins)
* DB9 connector for joystick (Sega megadrive) compatible with A.Villena MiSTer DB9 addons
* USB3 User Port (for SNAC adapters SNES, Atari, ...)
* UART (Rx/Tx) header
* Power supply header (5V, 3V3, 3V3 LDO, 2V5 LDO, 1V8 analog)

### 3D model

![DECA_retro_cape_1](DECA_retro_cape_1.png)



![DECA_retro_cape_2](DECA_retro_cape_2.png)



### **Jumper Selection**

* JP1 jumper select Pmod 3 acting as peripheral (no jumper) or host (with jumper)

* JP2 jumper selects 3V3 power supply from Deca board or from LDO (5V to 3V3)

  

### Changelog

v0.5  routed finalized

v0.6  MiSTer SDRAM only version. Changed to 2 layer board.

v0.62 all finished except VGA R2R schematic and routing

v0.65 power header changed, minor aesthetic changes

v0.68 added vga schematic and indiv. R 0805 into layout

v0.70 routing finished including vga

v0.71 finished prototype desing. Gerber sent to JLCPCB for manufacturing.



### TODO changes / improvements

* footprint DB15 VGA does not fit connectors buyed in China (needed to bend pins)
* DETO Pmod connector change to socket type instead of pin type
* Modify footprint of USB3 for an economical one
* make bigger open hardware logo top layer
* remove vs/hs testpoints ?   1V8 ? power header ?
* U5 LDO 2V5 footprint do not correspond to LDO_2V5_NCV4274AST25T3G component
* 2V5 LDO gives 2.5 without connecting Deca. With Deca connected output goes to 2.74 V. With Sega megadrive connected goes to 2.64 V. Atari joystick 2.74V.
* Change limiting resistor of 180 Ohm to 510 Ohm
  * ps2 keyboard change R to 510 Ohm
  * ps2 mouse add pulldown footprints and R 180 Ohm, so I can have 1 ps2 keyb and 1 usb keyb

* BAT54S protection
  * It does not work very well
  * Put Resistors in front of BAT54, not after
  * Change joystick 2V5 protection  for voltage dividers ??
  * ps2 BATs give 3.6V at GPIOs

* PCB Hole for conf leds

