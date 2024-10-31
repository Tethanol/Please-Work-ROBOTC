# Please Work ROBOTC
A quick guide on ROBOTC for ENGR-10 labs at SJSU.

## Table of Contents
- [General Controller Knowledge](#general-controller-knowledge)
- [Configuing ROBOTC for the First Time](#configuring-robotc-for-the-first-time)
- [Troubleshooting](#troubleshooting)



## General Controller Knowledge

### Controller LEDs
We have 3 LEDs on the Vex Cortex Controller which have different meanings \(from top to bottom)

- **ROBOT:** Green = Battery on; Red = Battery off
- **VEXnet:** This should not be on for our robot project.
- **GAME:** Green = Robot is operational (Not always true)


### Power Cycling
Power cycling helps reset the controller's operation modes as well being a general troubleshooting tool. To power cycle, see the instructions below:

1. Turn off the controller and remove the USB.
2. After all controller LEDs are off you may plug in the USB and turn on the controller.



## Configuring ROBOTC for the first time

### Change Platform Type to Vex 2.0 Cortex
ROBOTC default Platform Type is Vex IQ, but it should be Vex 2.0 Cortex.

Change it in `Robot > Platform Type > Vex Robotics > Vex 2.0 Cortex`.
<img src="https://github.com/user-attachments/assets/3d529a47-8d94-40d2-9cea-f56b53d2fbe6">

### Update Controller Firmwares
>[!CAUTION]
>Failure to update the controller and CPU firmware may result in **fire or burning of the controller** when operating the motors. **Update before running code!**

>[!WARNING]
>The battery must be **plugged in** and **controller turned on**, or the CPU will stuck in a bootloader loop.

Most of these controller are running EasyC-era Cortex firmware, which is older than the ROBOTC Cortex firmware used for the program. Most controllers should pick up on the outdated firmware and prompt the user to update the controller.

To update the controller firmware, select `Firmware Download`.

<img width="622" alt="{E527AD8C-820C-40BF-A06E-092AB9A99ECA}" src="https://github.com/user-attachments/assets/5430f3e9-2754-4fa5-8753-afeb53caf023">

We must also update the Master CPU Firmware. **THE BATTERY MUST BE PLUGGED IN AND TURNED ON!**

To update this, go to `Robot > Download Firmware > Manually Update Firmware > Master CPU Firmware > Standard File`
<img width="811" alt="{DD1CD064-A63A-436E-9B3B-0623BE3078C6}" src="https://github.com/user-attachments/assets/2e92c14c-3d0b-4617-9b0e-db3744ee0a96">

<details><summary><b> What to do if CPU Master Firmware update fails</b></summary>

Your controller's CPU is stuck in a bootloader loop. The original laptop which attempted to download the code will not recognize the controller COM port until the CPU is fixed. To fix this you must:

1. Take the controller to a different laptop with ROBOTC.
2. Ensure VEX 2.0 Cortex is the platform type
3. Update the CPU Master Firmware again with the **battery on**.
4. VEXnet LED will now be on, so ensure the Communication Mode is set to USB only. [Power cycling](#power-cycling) may be needed to swap to USB Only mode.

</details>


### Change Communication Mode
ROBOTC defaults to dual USB/VEXnet functionality. This causes some errors with the robot not running when USB is not connected to the controller.

Change it to USB Only through `Robot > Vex Cortex Communication Mode > USB Only`
<img src="https://github.com/user-attachments/assets/c59b8bc1-d92a-4b81-9c54-412057a2705f">

>[!IMPORTANT]
>When you download the code for the first time, it may ask to power cycle your controller.

### Set Natural Language as PLTW
Natural Language is ROBOTC's method of introducing additional functions for the user which may commonly be used and coded in a different matter. Youseffi calls for the use of Natural Language PLTW as Natural Language 2.0 _removes base functions_ important to gotobeacon.c.

Set it in `Robot > Platform Type > Natural Language PLTW`
<img src="https://github.com/user-attachments/assets/f627f365-55df-4bd1-b12e-556fb9a8b112">



## Troubleshooting
>[!IMPORTANT]
>If you encounter any issue that is not listed in the troubleshooting section, or the solutions do not work, contact me at ethan.thanh@sjsu.edu so I can hopefully find a solution other than get a new XYZ part.


To effectively figure out what is wrong with the robot, we must use debugging windows. To access these windows,

1. Download code to robot.
2. Go to `Robot > Debugger Windows` and enable the following: `Global/Local Variables, Motors, Sensors`
   ![image](https://github.com/user-attachments/assets/5fce1f0c-d1e7-45d6-8992-34932972c8dd)


>[!NOTE]
>Debugging windows will only display values when the robot is plugged in.

The following sections are symptoms with their respective resolutions with successive steps if the previous solution didn't work.

### General Fix: Firmware and Power Cycling
This only applies when ROBOT and GAME LEDs are green. This will fix most issues with the robot code not executing on the motors/sensors.

>[!WARNING]
>Again, the battery must be **plugged in** and controller **turned on**.

1. [Update/Reinstall the firmwares on the controller](#update-controller-firmwares)
2. [Power cycle] the controller to set it back to USB Only mode.


### Debug window indicates change in variable/motors/sensor value, but no change is observed
Check the debug menu:
- If the values associated with the variable/motors do not change, check the code.
- If the values associated with the variable/motors do change, check the controller.

<details><summary><b> Code Debugging</b></summary>

1. Check ports are defined.
2. There may be issues with Natural Language PLTW, especially for the motor. Try not to use PLTW when setting motor values. Recommend `motor[portX] = Y;` where X is a defined motor port, and Y is a value between -127 and 127.

</details>

<details><summary><b> Controller Debugging</b></summary>
                                                
1. [Power cycle](#power-cycling) the controller.
2. Try different ports.
3. Change the controller.


</details>

### ROBOT LED not on when USB is plugged in
1. Change the USB cable.
2. Change the controller.


### ROBOT LED irradically flashes between red and green
Usually an issue with the battery/controller terminals.

1. Change the battery.
2. Change the controller.


### Controller VEXnet and GAME LEDs are flashing orange
ROBOTC defaults to dual USB/VEXnet functionality. This causes the controller not to run code unless connected to USB.

Change the communication mode to `Robot > Vex Cortex Communication Mode > USB Only`.

<img src="https://github.com/user-attachments/assets/c59b8bc1-d92a-4b81-9c54-412057a2705f">


### Controller not recognized by computer
1. Change the USB cable.
2. Change the laptop.
3. Change the controller.
