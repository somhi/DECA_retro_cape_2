# DECA Retro Cape 2 (2 layer - MiSTer module SDRAM version)

**STATUS** (07/04/22):  PCBs received. Started [testing](testing.md). **Keyboard and Joystick (DB9 and USB3) protections must be redesigned in the next release**. See end of readme for changelog and improvements from v0.71

STATUS (15/03/22):  prototype desing work finished. v0.71 gerbers sent to JLCPCB for manufacturing.



Project has been developed with KiCAD 6.0. 

I want to give credits to Tom Verbeure from whom I've taken his [original design  files](https://github.com/tomverbeure/arrow_deca_retro_cape) and adapted to my own design. Not much have been left from his design, but the name "DECA Retro Cape" remains.  

### **Schematic**

 [arrow_deca_retro_cape.pdf](arrow_deca_retro_cape.pdf) 

### **Features**

* VGA DAC 444
* Terasic 2x20 pin connector (for Mister SDRAM modules) + 3 pin for Dual SDRAM/SRAM 
* PS2 keyboard & mouse connectors
* Double Pmod (1/2) for peripherals (VGA Pmod, Hyperram, ...)
* Pmod 3 (SPI + UART) host or peripheral 
* DETO Pmod (6 pin) for general usage (3 multiplexed pins)
* DB9 connector for joystick (Sega megadrive) (solder JP3 for A.Villena MiSTer DB9 addons)
* USB3 User Port (for SNAC adapters SNES, Atari, ...)
* UART (Rx/Tx) header
* Power supply header (5V, 3V3, 3V3 LDO, 2V5 LDO, 1V8 analog)

### 3D model

![DECA_retro_cape_1](DECA_retro_cape_1.png)



![DECA_retro_cape_2](DECA_retro_cape_2.png)



### **Jumper Selection**

* JP1 jumper select Pmod 3 acting as peripheral (no jumper) or host (with jumper)

* JP2 jumper selects 3V3 power supply from Deca board or from LDO (5V to 3V3)

* JP3 solder jumper, if soldered enables compatibility with Antonio Villena's MiSTer DB9 addons

* JP4 jumper closed enables 5V at VGA pin 9 to make use of VGA to SCART cables for 15 kHz RGB video

  

### Changelog

v0.5  routed finalized

v0.6  MiSTer SDRAM only version. Changed to 2 layer board.

v0.62 all finished except VGA R2R schematic and routing

v0.65 power header changed, minor aesthetic changes

v0.68 added vga schematic and indiv. R 0805 into layout

v0.70 routing finished including vga

v0.71 finished prototype desing. Gerber sent to JLCPCB for manufacturing.

v0.72 updated pinout spreadsheet and Readme with testing notes and improvements to be done

v0.75 Improvements from testing phase. See below



#### v0.75 changes

* Changed footprint DB15 VGA to fit connectors from Aliexpress (was needed to bend pins)

* DETO Pmod connector change to socket type instead of pin type

* Silkscreen improvements: OSHW logo top

* Removed JTAG footprint

* Change limiting resistor of 180 Ohm to 510 Ohm (ps2 and db9)

* Power header reduced to 1 row instead of 2

* optimized some traces

* added solder pad JP3 to enable/disable compatibility with Antonio Villena's MiSTer DB9 addons

* JP4 jumper to enable 5V at VGA pin 9 to make use of VGA to SCART cables for 15 kHz RGB video

* Added PCB Hole for seeing conf_done, rx, tx leds

  
  
  
  
  

### TODO changes 

* Double pmod compatible with RGB module of MuseLabs
* Protections
  * For ps2 use 3V6 (or 4V) zeners.  BAT54 could be used also with 3V3 supplied by Deca
  * Joy pull-up not working with the zener protections, gives 1 V so cores get crazy.
  * Jumpers per activar els pull-down del ps2 per passar a mode USB
  * PS2 mouse add pulldown footprints and R 180 Ohm, so I can have 1 ps2 keyb and 1 usb keyb
  * BAT54S protection
    * Put Resistors in front of BAT54, not after   -> test with keyboard
    * Change joystick 2V5 protection  for voltage dividers ??
    * DETO3_JOY_MUX is a 3V3 gpio. Add zenner 3v3 not 2v4

* Jumpers
  * solder jumper per alimentació joy de 5V o de 2V5
  * solder jumper per alimentació pmods de 3v3vp o 3v3ldo /treure el jumper actual)
  * jumper al pin 5 del db9 per evitar problemes als joystics raros ?
    * No, no les pasa nada. El Jumper lo puedes poner para cambiar la alimentación entre pin 5 y 7. De esa forma te funcionara ok los dos y podrás conectar cosas como el ratón de amiga. De los joysticks clásicos, la mayoría son totalmente pasivos y los quickshot II utilizan la alimentación de 5v para el autofire.

* Rename repository


### TODO improvements

* Mounting holes for stacking MIDI2SBC pcb

* Terasic connector, add jumpers on 5V & 3V3 to disconnect, so I can connect it to the Sockit GPIO board

* Reduce lenght of board in VGA wing side

* Modify footprint of USB3 for an economical one

* If space is needed, make a common ps2 for keyb and mouse (ps2 splitter should be used). 

* Provide to manufacturer component information to solder the PCBs

  

### Component selection

* U5 LDO 2V5 footprint do not correspond to LDO_2V5_NCV4274AST25T3G component

  

### Testing

[testing.md](testing.md)
