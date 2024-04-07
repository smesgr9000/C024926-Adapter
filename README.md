# C024926-Adapter

drop in replacement for Atari 7800 game ROMs DIP-28 for Atari C024926 or CO24926 PCBs. So if you game died but you want to reuse the original PCB to fix your cartridge.
The PCB will slot in the PINs on the PCB an can be used for 32kB-ROMs.

![C024926-Adapter installed on an C024926-1 Rev. 1](<./C024926.jpg>)

## Order PCB
To order the latest version either use KiCad or use release zip from GitHub.
To generate the Gerber files yourself, open _microcade.kicad_pcb_ in KiCad. Use _Fabrication Output_ > _Gerber_ and select an output folder and agree with _Plot_ with the default configruation. Also use _Fabrication Output_ > _Drill Files_ than select the same output folder and agree with _Generate Drill File_.

- enter length/width (36.4 x 18 mm)
- 2 layers
- 0.8mm thickness (my recommendation, other is possible too)
- FR4
- TG 150-160
- 6/6mil Min Tracking
- 0.3mm Hole Size
- Solder Mask - any is fine
- Silkscreen - any is fine
- No Edge Connector
- Finish - any is fine but would suggest HASL
- Tending Vias
- 1oz Finish Copper

Upload a zip containing the above generated files or use the release zip. Currently the price for 5 boards should be 5$.

## Progamm the EEPROM

Use your IC burner to program your dump back on the EPROM. Be aware to burn data without any headers. If you want to program the EEPROM after soldering set both Jumpers JP1 and 2 to "Prg" and wire your burner by crossing pin 1 and 27. See below:

Burner Pins | C024926-Adapter | header pin | C024926 pin description
--- | --- | --- | ---
27 | 1 | J1 1 | Write Enabled (WE)
2 | 2 | J1 2 | A12
3 | 3 | J1 3 | A7
4 | 4 | J1 4 | A6
5 | 5 | J1 5 | A5
6 | 6 | J1 6 | A4
7 | 7 | J1 7 | A3
8 | 8 | J1 8 | A2
9 | 9 | J1 9 | A1
10 | 10 | J1 10 | A0
11 | 11 | J1 11 | I/O0
12 | 12 | J1 12 | I/O1
13 | 13 | J1 13 | I/O2
14 | 14 | J1 14 | GND
15 | 15 | J2 14 | I/O3
16 | 16 | J2 13 | I/O4
17 | 17 | J2 12 | I/O5
18 | 18 | J2 11 | I/O6
19 | 19 | J2 10 | I/O7
20 | 20 | J2 9 | Chip Enabled (CE)
21 | 21 | J2 8 | A10
22 | 22 | J2 7 | Output Enabled (OE)
23 | 23 | J2 6 | A11
24 | 24 | J2 5 | A9
25 | 25 | J2 4 | A8
26 | 26 | J2 3 | A13
1 | 27 | J2 2 | A14
28 | 28 | J2 1 | VCC 

## Soldering

To finish the board two ICs and 2.54mm headers are required. Optional are two 1.27mm headers with shunts. This is needed if eeprom should be programmed soldered in.

Reference | Part | Amount | Description
--- | --- | --- | ---
U1 | Atmel/Microchip AT28C256-15SU | 1 | 256Kbit parallel EEPROM
U2 | Diodes 74AHCT1G04SE-7 | 1 | inverter SOT353
J1, J2 | Würth 61301411121 | 2 | 14pol 2.54mm header
JP1, JP2 | Sullins GRPB031VWVN-RC | 2 | optional, 3pol 1.27mm header
JP1, JP2 | Harwin M50-1900005 | 2 | optional, 1.27mm shunt

if jumper isn't used please bridge pin 1 and 2 "Use", see picture above.

## Jumper

- Use: Default, if the adapter is used in the cartridge
- Prg: If the EEPROM should be programmed see chapter "Programm the EEPROM"
