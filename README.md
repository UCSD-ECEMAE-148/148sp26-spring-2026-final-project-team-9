# <div align="center">DonkeyCar Upgrade</div>
![UCSDLogo](images/UCSDLogo.png)

### <div align="center"> ECE 148 Final Project </div>
<div align="center"> <img src="./images/Car Image.jpeg"> </div>

#### <div align="center"> Team 9 Spring 2026 </div>
<div align="center"> <img src="./images/Team Image.jpeg"> </div>

## Table of Contents
1. [Team Members](#team-members)
2. [Abstract](#abstract)
3. [Accomplishments](#accomplishments)
    - [What We Promised](#what-we-promised)
    - [Stretch Goals](#stretch-goals)
4. [Challenges](#challenges)
5. [Final Project Documentation](#final-project-documentation)
6. [Acknowledgements](#acknowledgements)
7. [Contacts](#contacts)

## Team Members
- Abdulaziz Khader - Computer Engineering - Class of 2026
- Filip Kurial - Aerospace Engineering - Class of 2028
- Guoxi Wu - Mechanical Engineering - Class of 2026

## Abstract
The goal of this project is to create a new fusion module between the Adafruit BNO08x IMU and the SparkFun NEO-F10N GPS, with the aim to create a more accessible set of parts for the DonkeyCar community. 

## Accomplishments
### What We Promised
- We managed to create a module for the BNO08x IMU and the NEO-F10n GPS, and the fusion generates locational data at 20Hz - limited by the speed of the main loop in DonkeyCar. 
- We tested the accuracy of this fusion on DonkeyCar's path_follow project, where the car follows a path determined by the GPS markers on a loop around campus.

Link to video of the car driving with the GPS/IMU fusion is found [here](https://drive.google.com/file/d/1c5hkkq--zWc0ZCswK_5Hx8fO6Ez4p7kt/view?resourcekey).

### Stretch Goals
- One stretch goal is to make the IMU and GPS integration modular so that you can use the BNO08x IMU with any kind of GPS, not just the NEO-F10N GPS. (Accomplished)
- Additionally, another supsequent goal is to measure the performance of the new IMU/GPS fusion against another GPS that supports RTK corrections to determine if upgrading the GPS would make a difference. 


## Challenges
Our biggest hurdle was with getting the IMU to work together with the GPS, as they would often overcorrect on positions or compete for trust on the true location of the car. Additionally, the IMU had some drift associated with it, giving us a forward value when the car is stationary. Tuning the fusion to account for both issues was the biggest hurdle we had to overcome, but we managed to complete it for a consistent fusion between the two modules.

## Final Project Documentation
### CAD Models
- [Camera Mount](./models/CameraMountV2.stl)
- [DC-DC Converter Case](./models/DCDCConverterCase.stl)
- [GPS Body Case](./models/GPSCaseBody.stl)
- [GPS Antenna Case](./models/GPSCaseCapv7.stl)
- [Serve PCB Case](./models/ServoPCBCase.stl)
- [VESC Case](./models/VESCBoxV2.stl)
- [Top half of RPi Case - thanks to Thingiverse](https://www.thingiverse.com/thing:7025215)
- [Bottom half of RPi Case](./models/PiBottom.stl)

### Electrical 
We added the IMU to the Raspberry Pi as an I2C connection, and here is the rest of the wiring of the car:

![Wiring Schematic](./images/Wiring%20Schematic.png)

### Code
All our code changes are shown in this GitHub [Pull Request](https://github.com/autorope/donkeycar/pull/1237).

To summarize: we added our BNO08x IMU as a separate class to not interfere with the current setup of DonkeyCar, and added a fusion component for fusing the GPS and IMU together. We then added an if-statement to check for those components in the setup of DonkeyCar and added a config option to toggle the fusion.

## Usage
To run this fusion, follow the steps in the donkeycar repo to clone it with the path_follow template, then change the ``myconfig.py`` file to turn on the fusion.

## Acknowledgements
*Huge thanks to Professor Silberman for making this a class we can have fun with! And thanks to Winston and Jose for helping us debug all the issues with the GPS. You are incredibe and amazing people!*


## Contacts
- Abdulaziz Khader - akhader@ucsd.edu 
- Filip Kurial - fkurial@ucsd.edu
- Guoxi Wu - guw007@ucsd.edu
