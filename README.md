# Thermometry-Sensor-Instructions


Starting with the empty circuit boards:

Finished schematic:

<img src="https://user-images.githubusercontent.com/108306069/180638077-1676d7af-37d4-4900-81e7-8d532505efff.png" width="40%" height="40%" />


<img src = "https://user-images.githubusercontent.com/108306069/180638084-9f4401e8-8b92-4297-a38c-d2ef5e9d8e3c.jpg" width="30%" height="30%" />

<img src = "https://user-images.githubusercontent.com/108306069/180638138-ed8431ed-e6fe-4d70-b511-20ef9f321969.jpg" width="20%" height="20%" />
<img src = "https://user-images.githubusercontent.com/108306069/180638139-28253d3c-6404-44e0-8641-dd005f827168.jpg" width="20%" height="20%" />

Highlighted Schematic:

<img width="480" alt="Screen Shot 2022-07-24 at 1 06 48 AM" src="https://user-images.githubusercontent.com/108306069/180638238-5b6b8076-db8e-48e9-a57a-634a00a3c19e.png" >


<img width="417" alt="Screen Shot 2022-07-24 at 1 08 24 AM" src="https://user-images.githubusercontent.com/108306069/180638297-c3f823bd-0eec-4a62-8e48-fff99ad0ff64.png">


<img width="209" alt="Screen Shot 2022-07-24 at 1 08 46 AM" src="https://user-images.githubusercontent.com/108306069/180638304-716aab9d-0b48-4e20-99e5-422189077b5f.png">


Solder:
The order in that I added pieces (this is not the best order to go in).
- 22 Ohm Resistors onto pads R1-R12, skipping R-13
- 0 Ohm Resistor onto R-13 pad
- DB15 Connector on the J1 pad
- LCD Connectors on the ILI9341TFT1 and ILI9341TFT2 pads
- Make sure the keying slot is facing the right direction. On the main board, the slot should be facing toward the MAX31856 pads and away from the Teensy pad.
- On the small board, make sure the slot is facing away from the ILI9341TFT3 Through Holes.
- The 1A Fuse on the F1 pad 
- A 47 uF capacitor on CP1 pad, below the Fuse.
- 0.1 uF Ethernet Capacitor on pad C1.
- The name of the pad isn’t visible on the schematic; the capacitor is next to the Ethernet Plugin
- An Ethernet plugin on the Teensy-Ethernet1 pad.
- The opening of the connector should also be facing away from the board.
- A Black Barrel Power Jack connector on the J2 pad.
- Make sure that this connector is also facing the correct direction; the main connector should be facing away from the middle of the board
- The Receptacle Connectors are placed on the long row of ThroughHole pins on the Teensy pad





Parts:
| LOC | Part | Digikey PN | Color on Schematic |
| -- | -- | -- | -- |
| J1 |  DB15 | LD15S33E4GV00LF-ND | yellow |
| J2 | Barrel 2x5.5mm | CP-002A-ND | Dark Blue |
|Teensy Conn| 24POS RCPT| SAM1093-24-ND| Orange |
|Teensy Conn| 6POS 2mm RCPT| DUPIIN - 2141-2X03G00SB | Purple |
|Teensy header| 30POS 2.54mm | S1012EC-30-ND | Orange |
|Teensy header| 6POS 2mm | 17-2842126-3-ND| Purple |
| Ethernet Conn | 100 Base T | 1278-1052-ND | Red |
| LCD Conn | 2x CONN HEADER 14POS | AE11367-ND| Green |
| R1-12 | 22 Ohm 0805 | A126437CT-ND | -- |
| R13 | 0 Ohm 0805 | A106066CT-ND | -- |
| CP1 | 47 uF 1206 | ?? | Teal |
| F1 | 1A Fuse | F6777CT-ND | Pink |
| C1 | 0.1 uF Ethernet Cap | BC1084CT-ND | Light Blue circle |
| MCU1 | 2x 24POS Recpt | SAM1093-24-ND | -- |



<img src = "https://user-images.githubusercontent.com/108306069/180638956-a9f4992f-68ad-4474-b62a-6bd775c51de7.jpg" width="20%" height="20%" /> <img src = "https://user-images.githubusercontent.com/108306069/180638962-3a38320f-b663-4d13-9c31-de228481b4fa.jpg" width="20%" height="20%" /> 

| Before | After |
| -- | -- |
| <img src = "https://user-images.githubusercontent.com/108306069/180639314-f5aa12a2-a3c6-4d54-afb0-247e3312ce83.jpg)" width="40%" height="40%" /> | <img src = "https://user-images.githubusercontent.com/108306069/180639360-1db0e3e9-5da4-40e8-9666-7f6b3f4f33b6.jpg)" width="40%" height="40%" /> |







