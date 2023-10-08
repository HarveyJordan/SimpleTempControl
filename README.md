# SimpleTempControl

Code and plans for a device capable of regulating the temperature in an enclosed container
## Problem Statement
A simple device is required that can read the temperature in an enclosed box and regulate it using an AC heating element. The acceptable teperature variations in the enclosure are relatively soft, on the order of 2-4 degrees celsius and as such a very simple control logic is acceptable. The upper and lower temperture bounds at which the heating element is turned on/off should be adjustable without the need to reflash code and some indication that the temperature is within the desired region must be given. The device should be splash proof and notbe overly large. The temperature probes should be placeable at least 50 cm away from the location of the device and a minimum of 2 temperature probes must be used. If more than 2 are used then the ability to enable/disable one or more probe must be provided. The device is intended for a user with limited electrical or software knowledge but with the ability to design for and use 3D printing. 

## Requirements 
### Mandatory
 - The device shall be equiped with 2-4 temperature probes with 0.5-1m leads (measured from the outside of the devices enclosure).
 - The device shall have a means by which the select which temperature probes to consider.
 - The temperature probes do not need to be removable with the use of hand tools.
 - The device shall be able to switch AC power on/off.
 - The AC heating element shall be able to be wired to the device with the use of basic hand tools and no prior electrical knowledge.
 - It shall be possible to adjust the upper and lower temperature thresholds using 2 potentiometers.
 - The temperature thresholds shall be adjustable in the range 20-40 degrees celcius.
 - The temperature thresholds shall be readable on a display while adjusting.
 - The current temperature inside the enclosure shall be displayed at all times
 - The device shall have an easily accessible power switch.
 - Disassebly of the device shall be possible with basic hand tools for the purpose modifying its enclosure.
 - The device shall have a enclosure that protects from liquid spills/splashes.
 ### Optional
 - The device could be equiped with a means of indicating errors or faults.

## General Plan
The concept is to use a readily avaliable micro controller with GPIO capabilities, such as the ESP32 or Arduino, as the brain of the device. The microcontroller will read have a number of temperture sensors which come on leads, such as one wire sensors, which will be used to measure the temperature. The temperature sensors will be numbered and a DIP switch (or similar) will be used to select which sensors to consider. A moving average between the sensors will be taken. A simple relay will be used to turn the heating element on/off and screw terminals or lever connectors will be used to wire the heating element. Either a mini LCD or 7 segment display will be used to show the temperature limits and the temperature will be adjustable with a pair of potentiometers. The entire system shall be housed in a simple enclosure and all cables passing in/out of the enclosure will either use gussets or simple pass through holes which match the size of the cables and then have clearance to electronics inside. The device will be powered by a standard 5V power cable such as a raspberry pi power cable or phone charger and there will be a power switch on the box containing the device.

For the optional requirements, an error LED will be provisioned which flashes in different patterns to indicate various errors. Examples of errors could be incorrect selection of temperature probes if the temperature difference between them is greater than 5 (TBC) degrees celsius, lack of power to the heating element if the relay has been turned on for some time and no significant temperature change has been noted. 
