# [Original Github - bungernut/nEXO_Thermometry](https://github.com/bungernut/nEXO_Thermometry)

# nEXO_Microcontroller_Temp
Using Teensy 4.1 and Arduino Mega to collect temperatures using PT100's and thermocouples

This program requires several libraries to be compiled. 
All but the WDT is installable via the Arduino library manager. 
Since the project is built on a Teensy4.1 it also naturally also reduires Teensyduino.
- [ ] Adafruit BME280
- [ ] Adafruit MAX31865
- [ ] Adafruit MAX31856
- [ ] WDT_T4 (https://github.com/tonton81/WDT_T4)

Current TODO:
- Fix NativeEthernet locking issue
- Prevent LCD burn in (partially done)
- Issue with assigning IP to multiple devices, should have put a couple dip switches to assign mac or IP

Future feature adds:
- Utilize ILI9341 touch feature for interactive display

Schematic of PCB
![Thermometry_SCH](https://user-images.githubusercontent.com/3258779/155235979-8a6f9ab8-8063-4b4c-9ad0-8a209429a6cb.png)

PCBnew
![Thermometry_PCB](https://user-images.githubusercontent.com/3258779/155236105-86f3ebac-597b-4e5d-be76-18cac1bc43cf.png)


PCB Version 1.2  
https://oshpark.com/shared_projects/bG9Ms06A (untested)


### - Parts
| LOC | Part | Digikey PN |
| -- | -- | -- |
| J1 |  DB15 | LD15S33E4GV00LF-ND |
| J2 | Barrel 2x5.5mm | CP-002A-ND |
|Teensy Conn| 24POS RCPT| SAM1093-24-ND|
|Teensy Conn| 6POS 2mm RCPT| DUPIIN - 2141-2X03G00SB |
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

