# Please Work ROBOTC
A quick guide on ROBOTC for ENGR-10 labs at SJSU.

## Table of Contents
- [Downloading ROBOTC](#downloading-robotc)
- [Configuing ROBOTC for the First Time](#configuring-robotc-for-the-first-time)

## Downloading ROBOTC


## Configuring ROBOTC for the first time
### Change Platform Type to Vex 2.0 Cortex

ROBOTC default Platform Type is Vex IQ, but it should be Vex 2.0 Cortex.

Change it in `Robot > Platform Type > Vex Robotics > Vex 2.0 Cortex`.
<img src="https://github.com/user-attachments/assets/3d529a47-8d94-40d2-9cea-f56b53d2fbe6">


### Set Natural Language PLTW

Natural Language is ROBOTC's method of introducing additional functions for the user which may commonly be used and coded in a different matter. Youseffi calls for the use of Natural Language PLTW as Natural Language 2.0 _removes base functions_ important to gotobeacon.c.

Set it in `Robot > Platform Type > Natural Language PLTW`
<img src="https://github.com/user-attachments/assets/f627f365-55df-4bd1-b12e-556fb9a8b112">


###

## Troubleshooting
>[!IMPORTANT]
>If you encounter any issue that is not listed in the troubleshooting section, contact me at ethan.thanh@sjsu.edu so I can hopefully find a solution other than get a new XYZ part.


To effectively figure out what is wrong with the robot, we must use debugging windows. To access these windows,

1. Download code to robot.
2. Go to `Robot > Debugger Windows` and make sure the following are selected from the menu: `Global/Local Variables, Motors, Sensors`

>[!NOTE]
>Debugging windows will only display values when the robot is plugged in.

The following sections are symptoms with their respective resolutions.

### Debug window indicates change in motor/sensor/variable value, but no change is observed



### ROBOT LED irradically flashes between red and green



### Controller VEXnet and GAME LEDs are flashing orange
ROBOTC defaults to dual USB/VEXnet functionality. This causes the controller not to run code unless connected to USB.

Change the communication mode to `Robot > Vex Cortex Communication Mode > USB Only`

<img src="https://github.com/user-attachments/assets/c59b8bc1-d92a-4b81-9c54-412057a2705f">

