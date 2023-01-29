# Testing DECA Retro Cape 2 



## Tests v0.90 PCB

- [x] DB15 VGA connector
  - [x] SCART JP4 jumper (5V on pin 9) to activate TVs for 15 KHz video output (test: PCXT, Pooyan)
  
- [x] Mister module connector: tested with dual memory module and XS 2.2
  - [x] 3 extra pins. Test with dual memory module
  - [x] JP6 jumper for 3V3 power supply
  - [x] JP5 jumper for 5V power supply
  
- [x] PS2 mouse: PCXT, MiSTery
  - [x] voltage on FPGA pins < 3V3 (Test: 2.75 V)
  
- [x] PS2 keyboard: all cores tested
  - [x] voltage on FPGA pins < 3V3.  (Test: 3.16V)
  
- [x] DB9 / USB3
  
  - [x] Without joystick connected, keyboard is working fine
  
  - [x] DB9 joystick  (tested with megadrive 6 buttons) (Pooyan, SNES 6 buttons test)
    - [x] voltage on FPGA pins < 2V5  (test: 2.49V)
    - [ ] DB9 Mux JP3 solder jumper for Villena addons compatibility  **(untested)**
  
  - [x] USB3 user IO: tested with USB3 to DB9 SNAC  (tested with megadrive 6 buttons) (SNES 6 buttons test)
    - [x] voltage on FPGA pins < 2V5
    - [x] JP9 I/O 
    - [ ] JP9 3V3 **(untested)**

  - [x] DB9 / USB3 JP8 jumper selection  **(gives undesired results)**
  
    Without any jumper placed, if I connect a megadrive pad either to DB9 or USB3 it works and the corresponing pin of the jumper (USB3 / DB9)  gets 5V though the gamepad itself.
  
    **CAUTION: Do not connect devices simultaneously into DB9 and USB3 connectors. Doing so may lead to unpredictabily results and damage the FPGA board.**
  
- [x] PMOD
  - [x] Pmod 1 (tested with Pmod VGA digilent)

  - [x] Pmod 2 (tested with Pmod VGA digilent)

    

  - [x] Pmod 3
    - [x] JP1 jumper to act as Pmod host

  - [ ] Pmod DETO

  - [x] Extended pins for Pmod1 & Pmod2 

    - [x] 5V
    - [ ] 4 extra central pins for e.g.  RGB module of MuseLabs

- [x] UART Serial connector J15

- [x] Power supply connector J10
  - [x] 2V5 (LDO)
  - [x] 5V (FPGA)
  - [x] 3V3VP (FPGA)
  - [x] GND
  - [x] 3V3LDO (LDO) (0V as LDO is not assembled)

