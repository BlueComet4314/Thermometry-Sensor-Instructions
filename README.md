# Thermometry-Sensor-Instructions



## Finished Sensor:

### V1 with old mini Controller:


<img src = "https://user-images.githubusercontent.com/108306069/180639728-da122901-7785-490f-8541-07e176c8003f.jpg" width="30%" height="30%" /> <img src = "https://user-images.githubusercontent.com/108306069/180639732-4a652e38-5c96-459b-b6cc-5a22cece129e.jpg" width="30%" height="30%" />
<img src = "https://user-images.githubusercontent.com/108306069/180639743-0a02138f-b131-4d3f-869e-5574912ddfaf.jpg" width="30%" height="30%" />

### V2 with new minicontroller:

<img src = "https://user-images.githubusercontent.com/108306069/180685188-c0f67bbc-1eb3-444f-8481-792b022677f2.jpg" width="40%" height="40%" /> <img src = "https://user-images.githubusercontent.com/108306069/180685219-8be5ff90-ff56-4a7b-890c-3c6aa682cf0f.jpg" width="40%" height="40%" />

### V3 with thermocouple and PT100 inputs

- Finished Thermo Sensor, tested temperature readout with Liquid Nitrogen - ~77 Kelvin. 
  - Small margin of error on TCPs +/- 3 Kelvin.

<img src = "https://user-images.githubusercontent.com/108306069/181170964-011baca8-69f6-4f5b-88f1-50cd95f96876.jpg" width="40%" height="40%" />



## Starting with the empty circuit boards:

Finished schematic:

<img src="https://user-images.githubusercontent.com/108306069/180638077-1676d7af-37d4-4900-81e7-8d532505efff.png" width="40%" height="40%" /> 

Finished Board:

<img src = "https://user-images.githubusercontent.com/108306069/180638084-9f4401e8-8b92-4297-a38c-d2ef5e9d8e3c.jpg" width="30%" height="30%" />

<img src = "https://user-images.githubusercontent.com/108306069/180638138-ed8431ed-e6fe-4d70-b511-20ef9f321969.jpg" width="20%" height="20%" /> <img src = "https://user-images.githubusercontent.com/108306069/180638139-28253d3c-6404-44e0-8641-dd005f827168.jpg" width="20%" height="20%" />



Parts:
| LOC | Part | Digikey PN | Color on Schematic |
| -- | -- | -- | -- |
| J1 |  DB15 | LD15S33E4GV00LF-ND | yellow |
| J2 | Barrel 2x5.5mm | CP-002A-ND | Dark Blue |
|Teensy Conn| 24POS RCPT| SAM1093-24-ND| Orange |
|Teensy Conn| 6POS 2mm RCPT| DUPIIN - 2141-2X03G00SB | Purple |
|Teensy header| 30POS 2.54mm | S1012EC-30-ND | Orange |
|Teensy header| 6POS 2mm | WM20513-ND | Purple |
| Ethernet Conn | 100 Base T | 1278-1052-ND | Red |
| LCD Conn | 2x CONN HEADER 14POS | AE11367-ND| Green |
| R1-12 | 22 Ohm 0805 | A126437CT-ND | -- |
| R13 | 0 Ohm 0805 | A106066CT-ND | -- |
| CP1 | 47 uF 1206 | ?? | Teal |
| F1 | 1A Fuse | F6777CT-ND | Pink |
| C1 | 0.1 uF Ethernet Cap | BC1084CT-ND | Light Blue circle |
| MCU1 | 2x 24POS Recpt | SAM1093-24-ND | -- |


## Highlighted Schematic:

<img width="480" alt="Screen Shot 2022-07-24 at 1 06 48 AM" src="https://user-images.githubusercontent.com/108306069/180638238-5b6b8076-db8e-48e9-a57a-634a00a3c19e.png" >


<img width="417" alt="Screen Shot 2022-07-24 at 1 08 24 AM" src="https://user-images.githubusercontent.com/108306069/180638297-c3f823bd-0eec-4a62-8e48-fff99ad0ff64.png"> <img width="209" alt="Screen Shot 2022-07-24 at 1 08 46 AM" src="https://user-images.githubusercontent.com/108306069/180638304-716aab9d-0b48-4e20-99e5-422189077b5f.png">



## Soldering:
The order in that I added pieces (this is not the best order to go in).
- **22 Ohm Resistors** onto pads R1-R12, skipping R-13
- **0 Ohm Resistor** onto R-13 pad
- **DB15 Connector** on the J1 pad
- **LCD Connectors** on the ILI9341TFT1 and ILI9341TFT2 pads
  - Make sure the keying slot is facing the right direction. On the main board, the slot should be facing *toward* the MAX31865 pads and *away* from the Teensy pad.
  - On the **small** board, make sure the slot is facing *away* from the ILI9341TFT3 Through Holes.
- The **1A Fuse** on the F1 pad 
- A **47 uF capacitor** on CP1 pad, below the Fuse.
- **0.1 uF Ethernet Capacitor** on pad C1.
  - The name of the pad isn’t visible on the schematic; the capacitor is next to the Ethernet Plugin
- An **Ethernet plugin** on the Teensy-Ethernet1 pad.
  - The opening of the connector should also be facing *away* from the board.
- A **Black Barrel Power Jack connector** on the J2 pad.
  - Make sure that this connector is also facing the correct direction; the main connector should be facing *away* from the middle of the board
- The **Receptacle Connectors** are placed on the long row of ThroughHole pins on the Teensy pad:

<img src = "https://user-images.githubusercontent.com/108306069/180638956-a9f4992f-68ad-4474-b62a-6bd775c51de7.jpg" width="40%" height="40%" /> 

- Similarly, long **connector headers** (length 24) and smaller (3x2) connector headers will be soldered to the Teensy 4.1 board:
  - The 3x2 connector has it's *shortest* side soldered to the Teensy
  - The long 24 pin connector has it's *longest* side solder to the Teensy

<img src = "https://user-images.githubusercontent.com/108306069/181919947-589803b9-3c0a-4296-adec-bf5b955ecb33.jpg" width="25%" height="25%" /> <img src = "https://user-images.githubusercontent.com/108306069/181919948-7f15019d-8140-42b7-aea9-99a95137dfb5.jpg" width="42%" height="42%" />


- The pins (connected to the Teensy) will be put into the Recepticle connectors already soldered to the main board:

<img src = "https://user-images.githubusercontent.com/108306069/181172550-0d29fc93-3e87-45c5-93e3-dfb6dbc3ec84.jpg" width="20%" height="20%" /> <img src = "https://user-images.githubusercontent.com/108306069/181172567-f0d6f51a-caa4-4dad-b8c4-823b8bbb318a.jpg" width="20%" height="20%" /> <img src = "https://user-images.githubusercontent.com/108306069/181172573-9c1763ad-7686-44b1-8bba-2d3ff5003451.jpg" width="20%" height="20%" />


### Sensor Boards:

#### Parts Used

| Board Type | Purpose | Digikey Pin |
| -- | -- | -- |
| Adafruit MAX31865 | RTD | 1528-1804-ND |
| Adafruit MAX31856 | Thermocouple Amplifier | 1528-1772-ND |
| Adafruit BME 280 | Temperature, Humidity, Pressure | 1528-1359-ND |

- Five Adafruit MAX 31865 boards (Resistance Temperature Detectors (RTDs)) are soldered to their respective places along one end of the main board.
  - These for pin holes are normally where two wire clamps would go. However, instead, we are going to put 3 Connector headers here.  The MAX 31865 boards do not have Connectors that are wide enough for the 4 pins, so break apart the receptacle headers into singular pieces.


<img src = "https://user-images.githubusercontent.com/108306069/181920039-1a44e52b-00bb-43bd-bdd3-d3d7f7bd06a8.jpg" width="25%" height="25%" />

 <img src = "https://user-images.githubusercontent.com/108306069/181920138-42bf636e-e0b3-4abb-a5d2-f194df4a10ec.jpg" width="40%" height="40%" /> <img src = "https://user-images.githubusercontent.com/108306069/181920141-11c5d22f-c9d0-45af-85e8-5ba06314fb83.jpg" width="40%" height="40%" />



<img src = "https://user-images.githubusercontent.com/108306069/181175433-eba0cc57-0372-44fe-94a2-c6e2bdbae26a.jpg" width="35%" height="35%" />


- Two Adafruit MAX31856 boards (Thermocouple Amplifiers) are soldered to other side of board:


<img src = "https://user-images.githubusercontent.com/108306069/181175257-f38b23bc-bbe1-4071-92da-5e653a874c01.jpg" width="35%" height="35%" /> <img src = "https://user-images.githubusercontent.com/108306069/181175021-fc2dc400-9023-4525-9681-a0582e45d439.jpg" width="35%" height="35%" />


- One BME 280 Board (Temperature, Humidity, Pressure):

<img src = "https://user-images.githubusercontent.com/108306069/181176123-2502de2a-f2b0-4295-82b8-a4fbc86d7f7d.jpg" width="35%" height="35%" />
<img src = "https://user-images.githubusercontent.com/108306069/181176235-8fb24f9e-967a-4424-92e5-b60690b69af9.jpg" width="30%" height="30%" />


#### MAX31856 - RTD Board
- The RTD boards (in our version) were modified for a 3 wire configuration.
- Initially, the connection line on the copper plates - between the 4 and 3 wire pads(image) - needs to be severed.
  - Taking an exact-o knife, the copper line is cut/scraped away.

<img src = "https://user-images.githubusercontent.com/108306069/181443437-a7d02452-e05f-4367-acda-826065b1d67f.jpg" width="30%" height="30%" /> <img src = "https://user-images.githubusercontent.com/108306069/181443445-44dd36ed-dc8b-4a6f-8277-9e1c49840136.jpg" width="30%" height="30%" />


| Before | After |
| -- | -- |
| <img src = "https://user-images.githubusercontent.com/108306069/180639314-f5aa12a2-a3c6-4d54-afb0-247e3312ce83.jpg" /> | <img src = "https://user-images.githubusercontent.com/108306069/180639360-1db0e3e9-5da4-40e8-9666-7f6b3f4f33b6.jpg" width="60%" height="60%" /> |
|  | <img src = "https://user-images.githubusercontent.com/108306069/180639441-cf0101d0-a4c2-4110-ae81-d2ce6c5f3acc.jpg" width="50%" height="50%" /> <img src = "https://user-images.githubusercontent.com/108306069/180639509-22d139d0-4a20-4f01-860d-3ac06800104d.jpg" width="42%" height="42%" /> |



- The two 3 wire pads need to then be soldered together

(picture)

Nothing needs to be changed for the BME or Thermocouple amplifiers

























