# Teensy Code - what it's for



The code in the teensy_tft file needs to be uploaded to the Teensy 4.1 microcontroller used on the Thermometry Sensor board

This code essentially takes in the resistance/temperature readings from the PT100 (RTD sensors), converts the resistance to temperature in Kelvin, then displays this information to the digital screen that is connected to the main board.
The code is written in C++.


<img src = "https://user-images.githubusercontent.com/108306069/186031393-ab272727-d524-465a-8bb0-4282cfe1d6a7.png" width=50% height=50% />
<img src="https://user-images.githubusercontent.com/108306069/186031592-809fb829-91d5-4f96-82c8-fb6fc05c4156.png" width=80% height=50% />


Programs used for uploading teensy code to the microcontroller can be found [here](https://www.pjrc.com/teensy/loader_mac.html).

This link will take you to the following page:

<img src ="https://user-images.githubusercontent.com/108306069/186031658-57f1bef5-96a6-42bf-a0ae-659622360989.png" width=90% height=50% />


Download the two Teensy Loader links (boxed in red) and install the packages - One is the Teensyduino application and a second loader just called Teensy:

<img src="https://user-images.githubusercontent.com/108306069/186031696-5f7bca8f-2793-48db-b046-78d3197082d3.png" width=50% height=50% />

"Teensy" is the left application, "Teensyduino" is the right.

The website will instruct you on how to download these apps.

### ***Note  #1*** 

The Teensy app (left side of above image) does not directly get downloaded into your applications folder.
I'd recommend dragging and placing it there so you don't have to go searching for it.



The teensy_tft file in this repository will be opened through the Teensyduino application. 
When uploading the teensy_tft file, make sure that you are uploading a ***.zip*** file and not a folder.
When the files here are downloaded from this repository, they will already be in a .zip format.
Upload the teensy code exactly how it is downloaded.

### ***Note #2***

You will also need to change the I.P. and MAC address in the code itself according to your own system/server. Currently, there are three separate I.P.s and MAC addresses commented out in lines $35 - 49$. In the nEXO system, we built three thermometry sensors, each needed its own I.P. and MAC address.

The IP address will be dependent on your local network.

<img src="https://user-images.githubusercontent.com/108306069/186333172-af2e3c01-8c9d-4f26-8e27-bac763e66ec8.png" width="60%" />
