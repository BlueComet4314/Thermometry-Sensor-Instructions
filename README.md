# Table of Contents

<u>**Intro**</u>
- [Overview of Thermometry Sensors](#overview)
- [Accessories used](#accessories-used)
- [Sensor Board Versions](#sensor-versions)
- [Test data](#tests)
    
    - [Room Temperature Test](#u-room-temp-test-u)
    - [Liquid Nitrogen Test](#u-liquid-nitrogen-test-u)
    - [Vacuum Test](#u-cold-test---inside-vacuum-for-nexo-distillation-column-u)
     
      - [Thermosiphon Set up](#thermosiphon-set-up)


<u>**Instructions**</u>

- [Thermometry Sensor](#thermometry-sensor-1)
- [Thermocouples](#thermocouples)
- [PT100 (RTD) Boards](#pt100-rtd-boards)

  - [RTD Sensor](#sensor)
  - [Parts](#parts)
  - [Oshpark Schematic](#oshpark-schematic)
- [Wiring](#wiring)

  - [QWIIC cables to 3 Wire cable](#pt100-board-to-db15-wires-3-wire-configuration)
  - [DB15 Connector Layout for soldering](#db15-layout)

    - [Visual of wires connected to DB15](#to-db-15-images)
- [Casing](#casing)

- [Test Board](#test-board)


<u>**Final Documentation**</u>

- [Set-up Instructions](#set-up-instructions)
- [Final Images](#final-images)
- [Flange](#flange)
- [Trouble Shooting](#trouble-shooting)





# Overview

## [Original Github - bungernut/nEXO_Thermometry](https://github.com/bungernut/nEXO_Thermometry)

These sensor boards were built to read and display thermometry data. They were orignialy used for an experiment made by LUX-ZEPPLIN (LZ) to measure data within their cryogenic systems. Later, a group from the nEXO group based their design (with permission) off of the group from LZ. This document details the process of creating the Thermometry Sensor boards for the nEXO experiment at SLAC National Accelerator Laboratory. The boards at nEXO are also used for cryogenic purposes inside of a cryogenic distillation column. 

The Thermometry Boards are able to detect temperature, pressure, and humidity using five PT100 pads and two thermocouples. The pads are soldered to a small .5" circuit board and connected to the main Thermo board through a series of cables (which will be detailed out below). The small PT100 boards contain a 4-40 sized hole for a small screw, which will allow the boards to be attached to specific places inside of the cryogenic system (more into this later). 

The thermocouples are attached to two Adafruit MAX31856 - Thermocouple Amplifier boards. 

[Back to Top](#table-of-contents)

# Accessories used


## Thermometry Sensor:


### - Normal parts
| LOC | Part | Digikey PN |
| -- | -- | -- |
| J1 |  DB15 | LD15S33E4GV00LF-ND |
| J2 | Barrel 2x5.5mm | CP-002A-ND |
|Teensy Conn| 24POS RCPT| SAM1093-24-ND|
|Teensy Conn| 6POS 2mm RCPT| 23-0791077002-ND |
|Teensy header| 30POS 2.54mm | S1012EC-30-ND |
|Teensy header| 6POS 2mm | WM20513-ND |
| Ethernet Conn | 100 Base T | 1278-1052-ND |
| LCD Conn | 2x CONN HEADER 14POS | AE11367-ND|
| R1-12 | 22 Ohm 0805 | A126437CT-ND |
| R13 | 0 Ohm 0805 | A106066CT-ND |
| CP1 | 47 uF 1206 | 490-16309-1-ND |
| F1 | 1A Fuse | F6777CT-ND |
| C1 | 0.1 uF Ethernet Cap | BC1084CT-ND |
| MCU1 | 2x 24POS Recpt | SAM1093-24-ND |

### - Sensor Boards
| Board Type | Purpose | Digikey Pin |
| -- | -- | -- |
| Adafruit MAX31865 | RTD | 1528-1804-ND |
| Adafruit MAX31856 | Thermocouple Amplifier | 1528-1772-ND |
| Adafruit BME 280 | Temperature, Humidity, Pressure | 1528-1359-ND |

### - Microcontroller

Teensy 4.1 -
  - 1568-DEV-16771-ND

## - PT100 Boards


### - Equipment

- Need a USBC cable for power and uploading arduino software onto microcontroller
- An Ethernet Cable
- Computer or laptop compatible with Arduino software
- Soldering Iron
- tweezers
- needle nose pliers







[Back to Top](#table-of-contents)

# Sensor Versions


## <u> V1 with old test board: </u>

<img src = "https://user-images.githubusercontent.com/108306069/180639728-da122901-7785-490f-8541-07e176c8003f.jpg" width="30%" height="30%" /> <img src = "https://user-images.githubusercontent.com/108306069/180639732-4a652e38-5c96-459b-b6cc-5a22cece129e.jpg" width="30%" height="30%" />
<img src = "https://user-images.githubusercontent.com/108306069/180639743-0a02138f-b131-4d3f-869e-5574912ddfaf.jpg" width="30%" height="30%" />


## <u> V2 with new test board: </u>

<img src = "https://user-images.githubusercontent.com/108306069/180685188-c0f67bbc-1eb3-444f-8481-792b022677f2.jpg" width="50%" height="50%" /> <img src = "https://user-images.githubusercontent.com/108306069/180685219-8be5ff90-ff56-4a7b-890c-3c6aa682cf0f.jpg" width="45%" height="45%" />

## <u> V3 with test thermocouples and Copper block inputs </u>

<img src = "https://user-images.githubusercontent.com/108306069/181170964-011baca8-69f6-4f5b-88f1-50cd95f96876.jpg" width="50%" height="50%" />

(picture of copper blocks)

## <u> V4 - Finished (Final) Board: </u>

- Completed PT100 pads/circuit boards and two thermocouples

<img src = "https://user-images.githubusercontent.com/108306069/183540359-ea371047-1c70-486d-84a8-376f889c4bae.jpg" width="50%" height="50%" /> <img src = "https://user-images.githubusercontent.com/108306069/183540362-a6e5615e-7300-4030-a3be-22b11449a82e.jpg" width="45%" height="45%" />


[Back to Top](#table-of-contents)
# Tests

## <u> Room Temp Test </u>

- With PT100 inputs and short Thermocouples

### readings:

| Sensor | 1st Reading | 2nd Reading | 3rd Reading | Actual temperature | 
| -- | -- | -- | -- | -- |
| RTD 1 | 296.58 K | 296.48 K | 296.31 K |  | 
| RTD 2 | 295.57 K | 295.54 K | 295.64 K |  |
| RTD 3 | 296.08 K | 296.11 K | 296.42 K |  |
| RTD 4 | 296.01 K | 295.98 K | 295.87 K |  |
| RTD 5 | 295.98 K | 295.94 K | 296.04 K |  |
| TC 1 | 295.45 K | 295.53 K | 295.86 K |  |
| TC 2 | 295.09 K | 295.11 K | 295.17 K |  |


## <u> Liquid Nitrogen Test </u>

- With Original Copper PT100 blocks and long Thermocouples
- Finished Thermo Sensor, tested temperature readout with Liquid Nitrogen - ~ 77 Kelvin. 
  - Small margin of error on TCs +/- 3 Kelvin.

Liquid Nitrogen ranfes from 63 K - 77.2 Kelvin

###  Readings:

| Sensor | 1st Reading | 2nd Reading | 3rd Reading | Actual temperature | 
| -- | -- | -- | -- | -- |
| RTD 1 | 76.00 K | 75.97 K | 76.06 K | 77.2 K |
| RTD 2 | 76.18 K | 76.15 K | 76.27 K | 77.2 K |
| RTD 3 | 76.09 K | 76.09 K | 76.18 K | 77.2 K |
| RTD 4 | 76.03 K | 76.03 K | 76.09 K | 77.2 K |
| RTD 5 | 75.75 K | 75.69 K | 75.72 K | 77.2 K |
| TC 1 | 81.86 K | 81.72 K | 82.15 K | 77.2 K |
| TC 2 | 80.08 K | 80.31 K | 80.28 K | 77.2 K |


## <u> Cold Test - Inside vacuum for nEXO Distillation Column </u>

### Thermosiphon set up:



<img src = "https://user-images.githubusercontent.com/108306069/184038434-a6cbc5ee-32a0-496f-91f1-35d18373e046.jpg" width="60%" height="60%" />

The thermosiphon acts as an evaporator for the Liquid Xenon Cell in which it is located. The thermosiphon will be pumping Liquid Nitrogen through it's main two tubes connected at the top:

<img src = "https://user-images.githubusercontent.com/108306069/184044204-3818bdc9-bebf-4102-854a-fe845508ea35.jpg" width="60%" height="60%" />

Once the entire distillaiton column is completed, Gaseous Xenon will be pumped into the main chamber (where the Thermosiphon is located) inside of a smaller enclosed space. This is attached directly below the thermosiphon.


PT100 sensors are screwed into specific places on the thermosiphon. To test, we used PT100 sensor blocks used by a different experiment - LZ. We compared the new PT100s (RTDs) to the previous ones - with the knowledge that LZ's worked - in order to discern any unusual readings from the new PT100s

There are two PT100's from LZ, and four PT100s from nEXO. From now on, I will label the new PT100s as RTD, and the old RTDs as LZ. They are labeled on the Thermosiphon as shown:

##### Front Side view:

<img src="https://user-images.githubusercontent.com/108306069/184040527-e4ccb5d4-3682-4ab1-801c-1d8b744ef3c8.png" width="60%" height="60%" />

##### Back Side view:

<img src="https://user-images.githubusercontent.com/108306069/184040604-15123de5-772b-485e-8ff4-fd65ef4b4c60.png" width="60%" height="60%" />

LZ1 and RTD 4 are in parallel with each other on the Aluminium block - They should be reading relatively the same temperatures.
LZ2 and RTD 1 are also in parallel with each other on the Copper block - They should be reading the same temperatures as well.

#### **Note:**

<img src = "https://user-images.githubusercontent.com/108306069/184043248-99a460e7-974e-4453-9f7a-95cef09b9bd0.jpg" width="60%" height="60%" />

- The *top* of the Thermosiphon - (Copper block) is where the cool Liquid Nitrogen will enter, this is the coldest area
    -  RTDs 1 and 2, and LZ 2 are located here
- The *very bottom* of the block (aluminium block) is where the heater is located - the warmest area.
    - RTDs 3 and 4, and LZ 1 are located here

### Set Thermosiphon temperature at 170 K	(Aluminium block).

| PT100 |	Measurement (K) |
| -- | -- |
| RTD1	| 158.16 |
| RTD2	| 147.29 |
| RTD3	| 169.99 |
| RTD4	| 170.31 |
| -- | -- |
| LZ1 |	170.83 |
| LZ2 |	157.61 |

- This is very promising information - RTDs 3 and 4, and LZ 1 are located directly on the heater, reading near exactly 170 K. In addition, LZ1 and RTD4 sensor readings are very close to each other - roughly .5 K apart from one another




[Back to Top](#table-of-contents)

# Instructions: 

# Thermometry Sensor

### OshPark link:

[Thermometry_Board_V2](https://oshpark.com/shared_projects/bG9Ms06A)


### Finished schematic:

<img src="https://user-images.githubusercontent.com/108306069/180638077-1676d7af-37d4-4900-81e7-8d532505efff.png" width="40%" height="40%" /> 

### Initial Board:

<img src = "https://user-images.githubusercontent.com/108306069/180638084-9f4401e8-8b92-4297-a38c-d2ef5e9d8e3c.jpg" width="30%" height="30%" />

<img src = "https://user-images.githubusercontent.com/108306069/180638138-ed8431ed-e6fe-4d70-b511-20ef9f321969.jpg" width="20%" height="20%" /> <img src = "https://user-images.githubusercontent.com/108306069/180638139-28253d3c-6404-44e0-8641-dd005f827168.jpg" width="20%" height="20%" />



Parts:
| LOC | Part | Digikey PN | Color on Schematic |
| -- | -- | -- | -- |
| J1 |  DB15 | LD15S33E4GV00LF-ND | yellow |
| J2 | Barrel 2x5.5mm | CP-002A-ND | Dark Blue |
|Teensy Conn| 24POS RCPT| SAM1093-24-ND| Orange |
|Teensy Conn| 6POS 2mm RCPT| 23-0791077002-ND | Purple |
|Teensy header| 30POS 2.54mm | S1012EC-30-ND | Orange |
|Teensy header| 6POS 2mm | WM20513-ND | Purple |
| Ethernet Conn | 100 Base T | 1278-1052-ND | Red |
| LCD Conn | 2x CONN HEADER 14POS | AE11367-ND| Green |
| R1-12 | 22 Ohm 0805 | A126437CT-ND | -- |
| R13 | 0 Ohm 0805 | A106066CT-ND | -- |
| CP1 | 47 uF 1206 | 490-16309-1-ND | Teal |
| F1 | 1A Fuse | F6777CT-ND | Pink |
| C1 | 0.1 uF Ethernet Cap | BC1084CT-ND | Light Blue circle |
| MCU1 | 2x 24POS Recpt | SAM1093-24-ND | -- |

[Back to Top](#table-of-contents)
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


[Back to Top](#table-of-contents)

### Sensor Boards:

#### Parts Used

| Board Type | Purpose | Digikey Pin | Amount |
| -- | -- | -- | -- |
| Adafruit MAX31865 | Resistance Temperature Detector | 1528-1804-ND | Five |
| Adafruit MAX31856 | Thermocouple Amplifier | 1528-1772-ND | Two |
| Adafruit BME 280 | Temperature, Humidity, Pressure Detector | 1528-1359-ND | One |

- Five Adafruit MAX 31865 boards (Resistance Temperature Detectors (RTDs)) are soldered to their respective places along one end of the main board.
  - These for pin holes are normally where two wire clamps would go. However, instead, we are going to put 3 Connector headers here.  The MAX 31865 boards do not have Connectors that are wide enough for the 4 pins, so break apart the receptacle headers into singular pieces.


<img src = "https://user-images.githubusercontent.com/108306069/181920039-1a44e52b-00bb-43bd-bdd3-d3d7f7bd06a8.jpg" width="55%" height="55%" />

 <img src = "https://user-images.githubusercontent.com/108306069/181920138-42bf636e-e0b3-4abb-a5d2-f194df4a10ec.jpg" width="40%" height="40%" /> <img src = "https://user-images.githubusercontent.com/108306069/181920141-11c5d22f-c9d0-45af-85e8-5ba06314fb83.jpg" width="40%" height="40%" />


The individual pins will go in three specific places; one pin in the F- hole, one in the RTD+, and the last in th F+ hole. The front of the Adafruit board has just the F- and F+ label - the RTD+ hole is directly to the left of the F+ slot (see image). The full labels can also be seen on the very back. 


<img src = "https://user-images.githubusercontent.com/108306069/187054805-c953127b-f872-4fbc-a5ba-3dc6903071c7.jpg" width="80%"/>


<img src ="https://user-images.githubusercontent.com/108306069/187054814-ae1196d0-239b-4c44-93dc-ff568f831fd4.jpg" width=80% />


<img src = "https://user-images.githubusercontent.com/108306069/181175433-eba0cc57-0372-44fe-94a2-c6e2bdbae26a.jpg" width="50%" height="50%" />


- Two Adafruit MAX31856 boards (Thermocouple Amplifiers) are soldered to other side of board:


<img src = "https://user-images.githubusercontent.com/108306069/181175257-f38b23bc-bbe1-4071-92da-5e653a874c01.jpg" width="35%" height="35%" /> <img src = "https://user-images.githubusercontent.com/108306069/181175021-fc2dc400-9023-4525-9681-a0582e45d439.jpg" width="35%" height="35%" />


- One BME 280 Board (Temperature, Humidity, Pressure):

<img src = "https://user-images.githubusercontent.com/108306069/181176123-2502de2a-f2b0-4295-82b8-a4fbc86d7f7d.jpg" width="45%" height="45%" />
<img src = "https://user-images.githubusercontent.com/108306069/181176235-8fb24f9e-967a-4424-92e5-b60690b69af9.jpg" width="45%" height="45%" />


## MAX31856 - RTD Board
- The RTD boards (in our version) were modified for a 3 wire configuration.
- Initially, the connection line on the copper plates - between the 4 and 3 wire pads (ass seen in below images) - needs to be severed.
  - Taking an exact-o knife, the copper line is cut/scraped away.

## Before

<img src = "https://user-images.githubusercontent.com/108306069/183705753-a459558c-e3a5-4364-98cc-3f706cf5fabd.jpg" width="50%" height="50%"/> 


<img src = "https://user-images.githubusercontent.com/108306069/181443437-a7d02452-e05f-4367-acda-826065b1d67f.jpg" width="30%" height="30%" /> <img src = "https://user-images.githubusercontent.com/108306069/181443445-44dd36ed-dc8b-4a6f-8277-9e1c49840136.jpg" width="30%" height="30%" />


## After
<img src = "https://user-images.githubusercontent.com/108306069/183706656-addcf999-cf3f-4ec3-9eaa-95f944c6f043.jpg" width="60%" height="60%" />

<img src = "https://user-images.githubusercontent.com/108306069/183706736-f2eb818f-f915-4d97-beaa-b10d0270bd2a.jpg" width="60%" height="60%" /> 
<img src = "https://user-images.githubusercontent.com/108306069/183706820-2c4dccbe-210b-4160-a0f3-18130e1b46a4.jpg" width="50%" height="50%" /> 



- The two 3 wire pads need to then be soldered together



<img src = "https://user-images.githubusercontent.com/108306069/183702550-97961d95-3650-4c10-a858-08f2cdb1fe40.jpg" width="50%" height="50%" />


Nothing needs to be changed for the BME or Thermocouple amplifiers

[Back to Top](#table-of-contents)

# Thermocouples


The thermocouples used in this sensor are type 'T', with Copper and Constantan (Cu-Con) metals. This type of thermocouple can measure tempuratures from -250 degrees Celsius (23.15 K) to 350 degrees Celsius (623.15 K), which is very helpful to measure accurate temperatures in cryogenic conditions.

Thermocouples themselves always consist of two different types of metals that are joined together at one end - whether with solder or welding is up to the person. When the soldered end of the thermocouple is heated or cooled a voltage is created that can be associated with a specific temperature.

The thermocouples in our system will be used in conjunction with the Adafruit MAX31856 (Thermocouple Amplifier) boards. We'll need two - preferably long (roughly two and a half feet long) in order to test temperature readings. You can also make two short thermocouples in order to quickly test room temperature without the hastle of the long wires.

First, strip both ends of the thermocouple wires - the outer plastic, then the individuals (as shown in the images below).

Leave one side of the wire alone, that will be inserted into the connectors on the thermocouple amplifiers.
On the other end, twist the two metals and solder the wires together.

<img src = "https://user-images.githubusercontent.com/108306069/184797978-875eb3f6-0d54-40ae-a58f-71dc5eee1eac.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/184797980-2b07f6f5-91d4-435a-9811-92fedaaa957c.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/184797981-82fad48f-1704-4114-9ee3-c38b7d32de4a.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/184797982-a81cf862-99a1-4ac6-b710-d1bf91d4642b.jpg" width="48%" height="48%" />


<img src = "https://user-images.githubusercontent.com/108306069/184797984-be74ec2f-2472-46f0-8b26-a14d1fa91c11.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/184797985-349ff1dd-66df-4d0f-b85b-1d4ba747c348.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/184797986-8c6c7884-4de2-402e-9d6a-dd6a6c5a505d.jpg" width="48%" height="48%" />




The two ends that were not soldered together will be inserted into the terminal block (the black fastener), the Copper wire will be placed in the positive port (right hole) and the Constantan wire will be placed into the negative port (left hole).

Screw the top until the wires rest tightly inside the terminal block.

<img src = "https://user-images.githubusercontent.com/108306069/184805117-dcde885e-2d76-4d93-8e5a-e100852c7875.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/184805121-ee6cd491-92a6-4038-940c-528f8b567b45.jpg" width="48%" height="48%" />

<img src = "https://user-images.githubusercontent.com/108306069/184806560-3b6ca52e-71c3-46db-adff-15a50cf7afdc.jpg" width="48%" height="48%" />




Full Sensor with short thermocouples and Test board:

<img src = "https://user-images.githubusercontent.com/108306069/184806520-f2504c28-adb8-4823-b3b6-62ac52206db0.jpg" width="60%" height="60%" />

Full sensor with long thermocouples, connected to copper sensor blocks:

<img src = "https://user-images.githubusercontent.com/108306069/181170964-011baca8-69f6-4f5b-88f1-50cd95f96876.jpg" width="60%" height="60%" />





[Back to Top](#table-of-contents)

# PT100 (RTD) Boards

These boards were designed to measure and read out temperatures taken from a PT100 (RTD) sensor, which is transmitted to the Adafruit MAX 31865 boards using a QWIIC JST Conncector. The board itself is designed to lever and flatten the white RTD pad against the surface of an object (as seen in images below). 

The board was designed with a 4-40 screw hole in order to lever the PT100 pads onto the surface (in nEXO's case - the Thermosiphon as explained [above](#thermosiphon-set-up)):


<img src = "https://user-images.githubusercontent.com/108306069/184951746-3d9781f4-3e90-45ee-a319-53f1975df39f.jpg" width="80%" height="80%" />

<img src = "https://user-images.githubusercontent.com/108306069/184952454-4f8a7b08-593c-4097-a2c9-51678762b16a.jpg" width="60%" height="60%" />

----

<img src = "https://user-images.githubusercontent.com/108306069/184951745-5f80ee6f-18ba-4bc3-85bd-5df7187f7dcd.jpg" width="80%" height="80%" />
<img src = "https://user-images.githubusercontent.com/108306069/184952451-c3b241d5-560c-49d6-adca-50b395936aa7.jpg" width="60%" height="60%" />




Full Set Up

<img src = "https://user-images.githubusercontent.com/108306069/184950659-782837f7-7d89-4b54-8d48-7881b280e1de.jpg" width="48%" height="48%" />


<img src = "https://user-images.githubusercontent.com/108306069/184950651-861cfc07-9899-45eb-b866-f16872eb4698.jpg" width="48%" height="48%" />

<img src = "https://user-images.githubusercontent.com/108306069/184950662-61a63287-75ee-48fd-843a-6d65c137ffc9.jpg" width="48%" height="48%" />


### Boards:

<img src = "https://user-images.githubusercontent.com/108306069/184798246-4e013e32-0c95-4a86-936d-31fb06b9b0be.jpg" width="48%" height="48%" />


### Sensor:

<img src="https://user-images.githubusercontent.com/108306069/184969295-23648c81-804a-42bb-b3d2-1c7f80b1928e.png" width="48%" height="48%" />

---
## Parts:
---

| Part | Store | Pin |
| -- | -- | -- |
| PT100 - RTD | Digikey | 1759-1021-ND |
| Qwiic JST Connector | Mouser Electronics | 474-PRT-16766 |
| 4 Position Cable | Digikey | 1568-PRT-17257-ND |

[Back to Top](#table-of-contents)


### <u> OshPark Schematic:</u>

[PT100 Level Board - V2](https://oshpark.com/shared_projects/1DKsv6yt)



### <u> Comparisons: </u>

with penny:

<img src = "https://user-images.githubusercontent.com/108306069/184798241-0bbd25b9-b909-4962-983e-b0059b872fcb.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/184798242-a41971a1-3661-47c6-b173-a4070373a6c7.jpg" width="48%" height="48%" />

<img src = "https://user-images.githubusercontent.com/108306069/184798243-900d006e-df9b-4ceb-81c1-b156dcc14dbd.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/184798244-b7bac9e2-b7d5-40ac-bbb6-55a04a2c51d4.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/184798245-7f464741-0f0c-41e6-a66d-0577741e8255.jpg" width="48%" height="48%" />

[Back to Top](#table-of-contents)



### <u>completed</u>


<img src = "https://user-images.githubusercontent.com/108306069/184798247-97b44e98-79d8-4d36-9f35-07704dedc6bc.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/184798250-efc112f6-208a-4ca2-93cb-04ed21375a96.jpg" width="48%" height="48%" />

back <img src = "https://user-images.githubusercontent.com/108306069/184798253-8b540f9c-14ed-4fb1-9387-312c0a8043bb.jpg" width="48%" height="48%" />


side <img src = "https://user-images.githubusercontent.com/108306069/184798254-52c8c02e-8b04-428b-8215-11323210e509.jpg" width="48%" height="48%" />

Make sure that the ends of the RTD wires after soldered are snipped short.

[Back to Top](#table-of-contents)



full comparisons:

<img src = "https://user-images.githubusercontent.com/108306069/184798255-164ce5cf-6c33-44c3-a01d-942c3d9cd700.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/184798256-335c2450-7c80-474a-94a2-6643f4cf7475.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/184798258-bb97a8a4-cba2-403e-8e52-9b3c1d01a697.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/184798260-c2317e7e-282b-4c94-b463-5d3f2655efab.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/184798261-e6a00067-6130-4e04-b76c-b88df7d5d8cb.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/184798262-79985214-8987-45cd-a599-e24f5544ab8b.jpg" width="48%" height="48%" />

<img src="https://user-images.githubusercontent.com/108306069/184798263-ab4ef19c-5ebb-42a2-ac35-c9d8b32cce67.png" width="70%" height="70%" />




[Back to Top](#table-of-contents)

# Wiring

## PT100 Board to DB15 wires (3 wire configuration)

### Materials:

- Heat-shrink
- Three Wire cable
- 4 position cable (digikey)

The PT100 wires are connected to the Adafruit board with a 3 wire configuration. 
The four position (4P) cable bought from digikey site contains four wires and has two male QWIIC connectors on either side - the length of the wire will need to be cut in half.

---

The reason for a 3 wire configuration over simply just having two has to do with the added resistance in the wires themselves. 


<img src="https://user-images.githubusercontent.com/108306069/186334230-cf53a1a7-a5ce-4c4d-8199-8c371e8bb186.png" width="50%" />



In a three or four wire configuration, the extra third and fourth wires detect the added resistance in the main (1st and 2nd) wires so that we are able to later account for it. 
However, a four wire configuration is very complicated to put together. 
Therefore, a 3 wire config is used. 

With a 3 wire, we assume that the added resistance in the first wire is the same as what is detected in the third wire.

More information on these configurations can be found [<u><big>***here***</u></big>](https://www.omega.com/en-us/resources/rtd-2-3-4-wire-connections)

---

As seen in the below photos, the blue wire from the 4P cable was folded back, the three left were stripped and tinned.

Three wire braided cable can be used to make the 4P cable longer. For the nEXO group, 25 inch wire was needed, but the 4P wires were only 6 inches. Measure and cut needed length as necessary.

### _**Note**_:

The colors of the three wire cable doesn't matter, but it would be better to find colors that match with the QWIIC (4P) cable (or any other cable used) to keep colors consistent and easy to follow for later on.

Recommended colors would be - black, red, and white cable. 
The 4P cable is colored black, red, blue, and yellow, but the blue wire was not used; red to red, black to black, and yellow to white.

 The 3 wire cable was also stripped and tinned, but before soldering them together, make sure heat shrink plastic tubes are put on the individual wires. 
 The heat shrink should be think enough to fit over the wire and still have some room to maneuver. 
 It should then be soldered to the 4P cable as seen in the images below.

 The other end of the three wire should not be soldered to anything yet.
 



<img src = "https://user-images.githubusercontent.com/108306069/185766617-954beb76-67e1-41be-bd0b-90935a3922cc.jpg" width="50%" height="55%" /><img src = "https://user-images.githubusercontent.com/108306069/185766623-c3d06b05-1737-4e91-85f3-d4f61504958a.jpg"  width="50%" height="55%" />


<img src = "https://user-images.githubusercontent.com/108306069/185766627-cb579d6f-ee85-4b9e-84e9-b5c3bbc7aa5e.jpg"  width="50%" height="55%" /><img src = "https://user-images.githubusercontent.com/108306069/185778949-317af6b9-57d7-4d23-b54a-ae9a424c5173.jpg" width="50%" height="55%" />


[Back to Top](#table-of-contents)

Move the heat shrink so that it covers the exposed wire and both cables that were soldered together. 
Heat the shrink plastics so that they are snug on the wires and do not individually move.
The wires can all three be moved in front of the heat gun at the same time, as long the heat shrink plastics are not touching each other.

Then, cut another piece of heat shrink and place it over the three wire cable (white, red, black) all the way until just before the the soldered joints - not entirely over the connected wires. 
This is to help keep the wires themselves protected and to keep them held together.
It is circled in the next photo:

<img src = "https://user-images.githubusercontent.com/108306069/185778777-e66a54ad-fd78-4270-ad75-b8b09ac564be.png" width="50%" height="55%" />

This also needs to be shrunk with the heat gun. Another wider tube of heat shrink needs to be cut. this time placed over the entirety of the wires - **_including_** the blue wire that was not used from the 4P QWIIC cable. The blue wire is included so that there are no exposed wires - to protect it and the system from shorts.

More heat shrink tubes can be added anywhere on the long strips of wires to keep the three cables together. I recommend putting a piece somwhere in the middle of the 3 wire and, on the opposite side, a little over an inch from the end.


<img src = "https://user-images.githubusercontent.com/108306069/185779342-11dd0550-268c-43da-8a5a-2952a9d8174b.png" width="50%" height="55%" />

Circled in blue are both the soldered ends of the 3 wire and 4P QWIIC connectors and the placement of the heat shrink. This is one of the final set ups for the Thermometry Sensor. The male connector will be placed in the female QUIIC connector on the PT100 boards.


### Finished:

<img src = "https://user-images.githubusercontent.com/108306069/184798467-91330268-8961-427e-8216-f5d0071aa060.jpg" width="55%" height="55%" />





[Back to Top](#table-of-contents)


# DB15 Layout

## [DB15 Wiring to RTD(Adafruit) boards](https://github.com/BlueComet4314/Test-Board-Instructions)



### To DB-15 (Images)

<img src = "https://user-images.githubusercontent.com/108306069/184798452-a2e35591-c14f-439d-8de4-ad9fd6077813.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/184798454-f7108c8d-c39e-456d-8c7f-5fc41f56aa8a.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/184798460-2a789be2-3efb-4a77-9485-1bf93ba478ae.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/184798463-87a4f5c2-265f-471e-b069-ab299ab38463.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/184798464-eb66bf25-b292-42ac-91a7-0bc6de4cb669.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/184798466-7e40b3fe-db35-4db4-b1f6-80fe5cb653d0.jpg" width="48%" height="48%" />

[Back to Top](#table-of-contents)


# Casing


[Back to Top](#table-of-contents)



# Test Board

Test boards for the Thermometry sensors boards were built in order to assay the functionality of the Thermometry boards as they were constructed.
These test boards (as shown in figure \ref{v2testboard}) use five resistors, with a resistance of 100 ohms (\Omega). The thermometry sensors - through the Teensy-4.1 - are able to convert this resistance to temperature.

Test Board wiring is the exact same as the wiring for the PT100/QWIIC cables found [here](#db15-layout)


## --> [DB15 Wiring to RTD(Adafruit) boards](https://github.com/BlueComet4314/Test-Board-Instructions) <--


### ***Version 1***

<img src = "https://user-images.githubusercontent.com/108306069/185823465-3eda0fea-e163-41c3-babf-fc7cd613bd82.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/185823466-614b1aed-64fd-41fd-8b8a-99fb3d206567.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/185823467-a0d639e8-b88d-4b7d-a39e-066bed02b51a.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/185823470-074942aa-4bb8-494e-9608-b56dc2b2b46e.jpg" width="48%" height="48%" />


### ***Version 2***

<img src = "https://user-images.githubusercontent.com/108306069/185823544-dbf12f31-0b2b-497d-a1b6-4b21faf4f0c4.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/185823545-3c58800f-b503-40a3-8a56-15bfd6b210d4.jpg" width="48%" height="48%" /> <img src = "https://user-images.githubusercontent.com/108306069/185823546-3e61f260-9e90-45b5-b063-fd9456583b7a.jpg" width="48%" height="48%" />

## ***Connected to Thermometry Sensor***

<img src = "https://user-images.githubusercontent.com/108306069/184806520-f2504c28-adb8-4823-b3b6-62ac52206db0.jpg" width="80%" height="60%" />


[Back to Top](#table-of-contents)

# Teensy Code

***Full Teensy Code and info can be found [***here***](https://github.com/BlueComet4314/Thermometry-Sensor-Instructions/tree/main/Teensy_code%20for%20Microcontroller) or in files at the top of the repository***

[Back to Top](#table-of-contents)

# Set-up Instructions

## With Test Board

Plug in the initial components before supplying the main board with power (just in case there are any shorts)

1. Ethernet Cable into ethernet port
2. Test Board into DB15 connector on Thermosensor
3. Main screen needs to be connected to middle port.
4. Thermocouples need to be screwed into the terminal block (the black fastener on the main board)
  
    -  ***Remember!!*** The Copper wire will be placed in the positive port (right hole) and the Constantan wire will be placed into the negative port (left hole).

<img src = "https://user-images.githubusercontent.com/108306069/186332681-432f33c2-13c9-40ab-8b6f-9d8d3e0f9920.png" width="90%" height="48%" />

After plugging in the components, supply power to the board, whether this is a usb cable inserted into the Teensy or a power adaptor into the barrel connector, it doesn't matter.
***However***, make sure that if you use a power adaptor that it does **not** excede <u>**6 Volts**</u>. This can cause damage to the Teensy or other parts of the Thermosensor.

[Back to Top](#table-of-contents)

## With PT100s


[Back to Top](#table-of-contents)

# Final images

## Test 1 -  Initial Room Temperature Testing of fully connected board

PT100s and Thermocouples were left in open air, taking in temperature of the room.

<img src = "https://user-images.githubusercontent.com/108306069/185823712-f5495cf6-93d2-46e9-9da5-2d9e74cd226b.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/185823714-35214d32-92bf-4d4e-984b-b51130b6bcea.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/185823716-3050e682-4cd1-4e99-8c79-3597b3178d24.jpg"
<img src = "https://user-images.githubusercontent.com/108306069/185823718-b0dd1cca-2b63-4da9-a3fa-107fa4b67e8a.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/185823719-392f6ebd-6363-4266-a552-77626c0d4df1.jpg" width="48%" height="48%" />


## Test 2 - Sensors inside Liquid Xenon Cell, attached to Thermosiphon

PT100s were attached to the Thermosiphon, as shown [here](#thermosiphon-set-up). The liquid xenon cell was placed under vacuum, Nitrogen gas was set to flow through the thermosiphon's lines, and temperature on the thermosiphon set to 170 degrees Kelvin (-103.15 Celsius/-153.67 Fahrenheit).

<img src = "https://user-images.githubusercontent.com/108306069/185825356-5d2cc1e7-d477-42bf-9022-25fc893d71dd.jpg" width="48%" height="48%" />

Initial cooldown, first readings of room temperature. 

<img src = "https://user-images.githubusercontent.com/108306069/185825363-5cc0f3f9-d289-4cfe-9fb4-7f02dc01f227.jpg" width="48%" height="48%" />

Thermosiphon has cooled to 170 K.

RTDs 1-4 are located at different positions on the thermosiphon as shown in image [one](#back-side-view) and [two](#front-side-view). 
RTDs 1 and 2 are near the top where it's the coldest, 3 and 4 are near the bottom where the heater on the Thermosiphon is located. 
RTD 1 is in between 2 and 3.

They will have slightly differing temperatures from each other, with the exception of 3 and 4.
 3 and 4 are located on the Aluminium block directly opposite from each other - they should have very similar readouts.


<img src = "https://user-images.githubusercontent.com/108306069/185825365-3c5fcb1b-3f0b-4b77-891b-3f608f982329.jpg" width="48%" height="48%" />

<img src = "https://user-images.githubusercontent.com/108306069/185825364-642cdf00-f81e-41bb-8ae0-5950d6acc406.jpg" width="48%" height="48%" />
<img src = "https://user-images.githubusercontent.com/108306069/185825366-b02850b4-23a7-428c-83cd-b87de0454b18.jpg" width="48%" height="48%" />


Graphing as the PT100 sensors (only 4 were used in this test) were cooled to 170 degrees Kelvin.

## Test 3 - Overnight test inside LXe Cell

<img src = "https://user-images.githubusercontent.com/108306069/185830484-3af2b7ea-9638-4f55-8051-bc7c66f6ce40.jpg" width="48%" height="48%" />

Initial check in the evening before being left overnight to fully cool.

<img src = "https://user-images.githubusercontent.com/108306069/185830486-328119ac-515b-4b29-8bd6-fe290bb93bcf.png" width="90%" height="48%" />

Graph of the complete cooldown of the RTD temperatures - stopping to rest at roughly 83 K to 85 K

Nitrogen gas was set to flow through the thermosiphon lines to cool the thermosiphon itself. The temperature of N2 is roughly 77 degrees Kelvin (-350 Fahrenheit/-196 Celsius). 

The graph in the second image shows the successful cooldown to Nitrogen Temperature. As shown in the top image, the RTDs (from nEXO) and LZs (from LUX-ZEPPLIN) show matching temperatures. Since we knew that LZ's PT100 sensors did work, to see nEXO's RTDs reading out near identical readings was promising!



## Updates -  "Room temperature" Check



<img src = "https://user-images.githubusercontent.com/108306069/185830624-e4af3d1b-0b02-4ab2-9c18-89e4760b1d4d.jpg" width="50%" height="48%" />

Quick check on thermometry sensors a few days after system's temperature was brought out of 77 K and let to rise back to room temperature.

Both Temperature Sensors that are being used now have their own protective cases.

## Updates - Second Room temperature check

After five days, the RTD sensors were once again check to make sure readings were accurate to the LZ sensors and that things were still running smoothly.


<img src = "https://user-images.githubusercontent.com/108306069/186332763-760c068b-a0f0-4bf3-9c33-e9a91aaf254f.jpg" width="50%" height="48%" />




[Back to Top](#table-of-contents)

# Flange

**This section is only if the Thermometry Sensors are being used for a cryogenic system with metal connector flanges. The metal flanges are essentially used in order to connect a DB15 cable to the PT100 wires while keeping the PT100s inside vacuum and the cable in open air as seen in the photos below.**

**If not used for a cryogenic system, this section can be skipped.**

PT100 cables were connected to an inner vacuum flange (feedthrough).

(image)

Gender changer for the DB15 was welded onto the flange which connects the RTDs from inside of the chamber to a cable outside of the chamber. The outer cable then connects to main thermometry board. 

At nEXO, there was a small issue with the feedthrough connector. 
The pins at the center were not direct feed throughs.
In other words, out of 15 pins; pin 15 on the vacuum side of the flange did not directly connect to pin 15 on the open air side.
The pin connections were flipped; pin 15 connected to pin 9, pin 1 connected to pin 8, etc.

Therefore, if you have soldered the DB15 connector correctly according to the schematic and you are unable to read temperature readouts when the feedthrough flange is connected, this may be your issue.

Fortunately, this is an easy fix. 
_Un_ fortunately, you will have to solder the DB15 wires backwards. 

The easiest way to do this, is to take another DB15 connector/cable and face the connecting side upwards and have it nearby:

<img src = "https://user-images.githubusercontent.com/108306069/187056149-524d78b9-e832-4bac-9254-4109bac13a32.png" width="50%" /><img src = "https://user-images.githubusercontent.com/108306069/187056152-076542b2-b58a-4527-9cb5-bf3ae0b16c8e.png" width="50%"/>

<img src = "https://user-images.githubusercontent.com/108306069/187056170-518ced56-0bce-42c4-8eab-676649266d0c.png" width="90%" />

The second DB15 connector/cable will be there as a guide to look at as you solder the wires. 
Instead of following the numbers on the connector you are soldering on, follow the numbers on the other DB15 connector.
It will be the same soldering methode, except backwards.

After this however, you will no longer be able to test the Thermometry boards without the feedthrough flange as the genderswapper.
The normal gender swapper doesn't have flipped pins (15 _is_ connected to 15, 8 to 8, etc.).

I suggest having an extra set of QWIIC cables connected to a DB15 that is soldered the normal way. 
That way if you need to test/assay something on the main thermo sensor board or PT100 board, you won't need the metal flange and extra cable to do so.



[Back to Top](#table-of-contents)

# Trouble Shooting



## Teensy

1. If you plug in the power source at some point and the green light on the Teensy blink on once briefly before dimming immediately to a faint green, this means that the Teensy may have been damaged/shorted.
You can easily check this if you have another Teensy on hand, the Teensys are designed to be able to be removed from the pins it is connected to just in case. 
You can pull the old Teensy off and replace it with a new one (once again uploading the Thermometry/Teensy code) and test it.

    - Another way to see if this is a Teensy issue, is if the screen itself doesn't display anything.
  It would only briefly light up once the power is supplied, then immediatly go black. 

2. If you have made multiple different thermometry sensors - or even if you have only made one - make sure that you have changed the MAC and I.P. address according to your own system/server, and that they are different from one another.





[Back to Top](#table-of-contents)

















