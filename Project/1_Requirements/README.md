

# Requirements

## 4’W and 1’H:

 **What:** It is an automated appliances control and calculation of energy bill.

 **Where:** Can be used in home, school, Industries.

 **When:** It is a home automation system with energy bill calculator.

 **Why:** Most of the Modern houses needs automation to reduce time, effort, manual and errors.

 **How:** It is done using Atmega Microcontroller and ESP8266 module. 

 ## SWOT Analysis:

 **Strength:** Innovative, User friendly, Basic Structure.

 **Weakness:** Can be developed by anyone, Software used needs subscription for unlimited use.

 **Opportunities:** Extra features can be added to meet 
 the demand.
 
 **Threats:** Multiple projects are available on the same field. 


 ## HIGH Level Requirements:

|`      `**ID**|`                 `**Description**|`            `**Status**|
| :- | :- | :- |
|`    `HL01|` `The user shall unlock the door by using password. | Implemented |
|`    `HL02|` `The user shall see the password on the LCD display.| Implemented |
|`    `HL02|` `The user shall change the password of the door.| Implemented |
|`    `HL03|` `The LED shall Shows the status of Door Lock. | Implemented |
|`    `HL04|` `The Buzzer shall activates if the password is wrong on multi-attempt. | Implemented |
|`    `HL05|` `The Outdoor light shall be controlled by intensity of sunlight. | Implemented |


 ## HIGH Level Requirements for Future Scope:
 |`      `**ID**|`                 `**Description**|`            `**Status**|
| :- | :- | :- |
|`    `HL01|` `The Blink App is used to control the appliances wirelessly.| Implemented in Future Scope |
|`    `HL02|` `Electricity Bill is calculated based on units consumed.| Implemented in Future Scope |
|`    `HL03|` `The user shall monitor its energy consumption and the bill amount in ‘io.adafruit’ website.| Implemented in Future Scope |
|`    `HL04|` `The user should get automatic update of electric bill via mail if threshold value is reached.| Implemented in Future Scope  |

## LOW Level Requirements:


|`      `**ID**|`                 `**Description**|`            `**Status**|
| :- | :- | :- |
|LL01\_HL01|` `The user has to press the password in 4x3 keypad.| Implemented |
|LL02\_HL02|` `The user has to press ‘#’ to reset the password.|Implemented |
|LL03\_HL02|` `The user has to press ‘*’ to lock the door.|Implemented |
|LL04\_HL01|` `The user has to enter the current password to reset the password.|Implemented |
|LL05\_HL02|` `The user can see the password on the 16x2 LCD display.|Implemented |
|LL06\_HL03|` `The LED green indicated the door is open.|Implemented |
|LL07\_HL03|` `The LED red indicated the door is locked.|Implemented |
|LL08\_HL04|` `The Buzzer gets activated after 3 unsuccessful attempts.|Implemented |
|LL09\_HL04|` `The Outdoor Light is controlled by LDR sensor.|Implemented |


 ## LOW Level Requirements for Future Scope:
|`      `**ID**|`                 `**Description**|`            `**Status**|
| :- | :- | :- |
|LL01\_HL01|` `The Blink app can be configured for different rooms to operate the different appliances | Implemented in Future Scope |
|LL02\_HL03|` `The adafruit website has two different gauge one to monitor energy consumption and other to monitor bill | Implemented in Future Scope  |
|LL03\_HL04|` `The email should be send using IFTTT (if this then that) feature of ‘io.adafruit’ website  which generates the email if threshold value is reached |  Implemented in Future Scope  |




