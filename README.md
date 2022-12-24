# DECA Retro Cape 2

### (2 layer - MiSTer module SDRAM version)

DECA Retro Cape 2 is an addon for the [DECA FPGA](https://github.com/DECAfpga/DECA_board) development kit from Arrow/Terasic. The addon is connected to the Beaglebone Black connectors and hence the name of Cape as addons in the Beaglebone world are known.

This cape adds IO interface to the DECA board with all is needed to implement retro computers in this beautiful FPGA. Main IO interfaces are DB15 for VGA, PS2 for keyboard and mouse, DB9 for joystick, MiSTer memory connector, MiSTer user port.

Project has been developed with KiCAD 6.0. 

### Status

STATUS (08/12/22):  Finalizing design of a new revision.  See end of readme for changelog improvements from v0.71.

STATUS (07/04/22):  PCBs received. Started [testing](testing.md).  Do not use without modifying voltage protections. Keyboard and Joystick (DB9 and USB3) protections must be redesigned in the next release.

STATUS (15/03/22):  prototype desing work finished. v0.71 gerbers sent to JLCPCB for manufacturing.

### Credits

I want to give credits to Tom Verbeure from whom I've taken his [original design  files](https://github.com/tomverbeure/arrow_deca_retro_cape) and adapted to my own design. Not much have been left from his design, but the name "DECA Retro Cape" remains.  

Thanks to rest of Hard Team DECA (C.Palmero & Rhoderik) and Telegram groups for the support received  during the development phase.

### **Schematic**

 [arrow_deca_retro_cape.pdf](arrow_deca_retro_cape.pdf) 

### **Features**

* VGA DAC 444
  *  Jumper to make use of VGA to SCART cables for 15 kHz RGB video

* Terasic 2x20 pin connector (for Mister SDRAM modules) + 3 pin for Dual SDRAM/SRAM 
* PS2 keyboard & mouse connectors
* Double Pmod (1/2) for peripherals (VGA Pmod, Hyperram, ...). 
  * Added four central pins for compatibility with RGB module of MuseLabs

* Pmod 3 (SPI + UART). Can act as Pmod host or peripheral 
* DETO Pmod (6 pin) for general usage (3 multiplexed pins)
* Game controller port (selection jumper to enable one or the other)
  * DB9 connector for joystick (Sega megadrive) (solder JP3 for A.Villena MiSTer DB9 addons)
  * USB3 User Port (for SNAC adapters SNES, Atari, ...)

* UART (Rx/Tx) header
* Power supply headers (5V, 3V3, 3V3 LDO, 2V5 LDO, 1V8 analog)

### **Important Usage notes**

* Do not connect/disconnect interfaces while the board is powered.

### **Jumper Selection**

* JP1 jumper select Pmod 3 acting as peripheral (no jumper) or host (with jumper)

* JP2 solder jumper selects 3V3 power supply from Deca board or from LDO (5V to 3V3)

* JP3 solder jumper, if soldered enables compatibility with Antonio Villena's MiSTer DB9 addons

* JP4 jumper closed enables 5V at VGA pin 9 to make use of VGA to SCART cables for 15 kHz RGB video

* JP5 jumper closed power supply 2x20 Terasic connector with +5V

* JP6 jumper closed power supply 2x20 Terasic connector with +3V3

* JP7 solder jumper to select joystick power supply (5V or 2V5 from LDO)

* JP8 jumper select either DB9 interface or USER IO (USB3)


### 3D model

![DECA_retro_cape_1](DECA_retro_cape_1.png)



![DECA_retro_cape_2](DECA_retro_cape_2.png)



### Changelog

v0.5  routed finalized

v0.6  MiSTer SDRAM only version. Changed to 2 layer board.

v0.62 all finished except VGA R2R schematic and routing

v0.65 power header changed, minor aesthetic changes

v0.68 added vga schematic and indiv. R 0805 into layout

v0.70 routing finished including vga

v0.71 finished prototype desing. Gerber sent to JLCPCB for manufacturing

v0.72 updated pinout spreadsheet and Readme with testing notes and improvements to be done

v0.75 Improvements from testing phase. 

* Changed footprint DB15 VGA to fit connectors from Aliexpress (was needed to bend pins)

* DETO Pmod connector change to socket type instead of pin type

* Silkscreen improvements: OSHW logo top

* Removed JTAG footprint

* Change limiting resistor of 180 Ohm to 510 Ohm (ps2 and db9)

* Power header reduced to 1 row instead of 2

* Optimized some traces

* Added solder pad JP3 to enable/disable compatibility with Antonio Villena's MiSTer DB9 addons

* JP4 jumper to enable 5V at VGA pin 9 to make use of VGA to SCART cables for 15 kHz RGB video

* Added PCB Hole for seeing Conf_done, Rx, Tx leds

v0.76 Double pmod 1&2 now compatible with pmod RGB module of MuseLabs (added 4 shared pins)

v0.77 Changes:

* Terasic connector: add jumpers on 5V and 3V3 to disconnect power, so I can connect it to other Terasic powered connectors.
* Replaced 3 pin jumper JP2 with solder jumper on 3V3 power selection
* Added solder jumper to select joystick power supply (5V or 2V5 from LDO)

v0.78 Changes:

* PS2 protection usign 3V9 Zener diodes (3V7 to 4V1).

* Added pulldown optional resistors for ps2 mouse

v0.80 Added Joystick shifter level protection with IC [TXS0108E](https://jlcpcb.com/partdetail/TexasInstruments-TXS0108EPWR/C17206) and jumper JP8 to select either DB9 or USB3 IO interface

v0.81 Improved Readme. Added readme notice in silkscreen. Removed v0.78 pulldown optional resistors for ps2 mouse (one of the pins has a physical pull-up resistor in fpga, so wouldn't work).

v0.82 generated BOM before installing jlcpcb-tools plugin

v0.83 Added jlcpcb parts with jlcpcb tools plugin 

v0.84 updated USB3 footprint

v0.85 updated references folder. choose zener 3V9 reference 

v0.86 added R7 1Ω for increasing ESR on 2V5 LDO output with a ceramic capacitor instead of tantalum. updated BOM and nearly finished jlcpcb parts selecction

### TODO changes 

* Provide to manufacturer component information to solder the PCBs

  


### TODO improvements

* Reduce lenght of board in VGA wing side
* Modify footprint of USB3 for an economical one
* PS2:  Jumpers to activate pull-down resistors to enable USB mode
* If space is needed, make a common ps2 connector for keyb and mouse (ps2 splitter should be used). 
* Jumper on joystick DB9 pin 5 to change power supply to pin 7 in order to allow other joysticks like the Amiga one to work. Comment from telegram: "El Jumper lo puedes poner para cambiar la alimentación entre pin 5 y 7. De esa forma te funcionara ok los dos y podrás conectar cosas como el ratón de amiga. De los joysticks clásicos, la mayoría son totalmente pasivos y los quickshot II utilizan la alimentación de 5v para el autofire."



### Testing

[testing.md](testing.md)
