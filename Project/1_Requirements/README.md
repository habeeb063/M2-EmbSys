# Abstract 

* Automation is an important technology in today's environment.
*  An automation system is a collection of sensors, controllers, and actuators that work together to complete a task with little or no human intervention.
*  In this project the idea of home automation is demonstrated with the energy meter, which calculates the bill amount and send it to user via mail, if threshold value is reached.
*  The user can control the appliances with the blink application anywhere around the world.


# Design of the System:

* The Home automation-based design energy meter consist of the fallowing components.

 ## Hardware Design:

 **Atmega328p Microcontroller:**

  * ATmega328 is an 8-bit, 28-Pin AVR Microcontroller, manufactured by Microchip, follows RISC Architecture and has a flash-type program memory of 32KB.
  * It has an EEPROM memory of 1KB and its SRAM memory is 2KB.
  * It has 8 Pins for ADC operations, which all combine to form PortA (PA0 – PA7).
  * It also has 3 built-in Timers, two of them are 8 Bit timers while the third one is 16-Bit Time
  * It operates ranging from 3.3V to 5.5V but normally we use 5V as a standard.
  * Its excellent features include cost-efficiency, low power dissipation, programming lock for security purposes, real timer counter with separate oscillator.


 **ESP8266 Module:**

  * The ESP8266 Wi-Fi Module is a self-contained SOC (System on chip).
  * It has integrated TCP/IP protocol stack that can give any microcontroller access to your Wi-Fi network.
  * It has GPIO pins allow Analog and Digital IO, plus PWM, SPI, I2C, etc.,
  * Each module comes pre-programmed with an AT command set firmware.

 **Ultra-Sonic Sensor:**

  * It is an electronic device that measures the distance of a target object by emitting ultrasonic sound waves, and converts the reflected sound into an electrical signal.
  * Ultrasonic waves travel faster than the speed of audible sound (i.e., the sound that humans can hear).
  * Ultrasonic sensors have two main components: the transmitter (which emits the sound using piezoelectric crystals) and the receiver (which encounters the sound after it has travelled to and from the target).
  * The formula for calculation is D = ½ T x C (where D is the distance, T is the time taken between the emission of the sound by the transmitter to its contact with the receiver, and C is the speed of sound 343 meters/second).

 **LDR Sensor:**

  * An LDR is a component that has a (variable) resistance that changes with the light intensity that falls upon it. 
  * A Light Dependent Resistor (LDR) is also called a photoresistor or photoconductor.
  * It is basically a photocell that works on the principle of photoconductivity. 
  * The passive component is basically a resistor whose resistance value decreases when the intensity of light decreases. 

 **Current Sensor Module(ACS712):**

  * ACS712 is a current sensor that can operate on both AC and DC.
  * This sensor operates at 5V and produces an analog voltage output proportional to the measured current.
  * The sensors use the Hall Effect to convert current inputs into voltage outputs.
  * In the Hall effect, electrons from an electric current flow through a magnetic field plate. The field then causes the electrons to "push" to one side of the plate and produce a voltage difference between the two sides. The difference in voltage from the side of the plate is the output of the sensor.

  **Keypad(4x3):**

  * Keypad is used as an input device to read the key pressed by the user and to process it.
  * A 4x3 keypad consists of 4 rows and 3 columns. Switches are placed between the rows and columns.
  * A key press establishes a connection between the corresponding row and column, between which the switch is placed.
  * To detect a pressed key, the microcontroller grounds all rows by providing 0 to the output latch, and then it reads the columns.
  * After pressing key, it makes contact of row with column, If one of the column bits has a zero, this means that a key press has occurred.

  **LCD (16x2):**

  * An LCD (Liquid Crystal Display) screen is an electronic display module and has a wide range of applications.
  * It can display 16 characters per line and there are 2 such lines.
  * Each character is displayed in 5x7 pixel matrix.
  * The 16 x 2 intelligent alphanumeric dot matrix display is capable of displaying 224 different characters and symbols.

 **Door Lock (Servo motor):**

  * A servo motor is a rotary actuator that allows for precise control of angular position.
  * Servo motor consists of DC motor with error sensing negative feedback mechanism. This allows precise control over angular velocity and position of motor.
  * It is a closed loop system where it uses negative feedback to control motion and final position of the shaft.
  * It has rotation angle that varies from 0° to 180°.

 **Electrical Appliances:**

  * An Electric Appliance is a device or apparatus that uses to perform a function in our personal life, other than industrial, with the help of electrical energy. It makes our life easier, bring comfort, and saves time.

 ## Software Design:

 **Blink Application:**

 * It’s an application used monitor and control the IoT devices from anywhere part of the world.
 * It can live stream in HD quality to anywhere.

 **Adafruit:**

 * The Arduino IDE is an open-source software, which is used to write and upload code.
 * The software is used to generate the hexa-file and dump it into microcontroller.

 **Arduino IDE:**

 * The Arduino IDE is an open-source software, which is used to write and upload code.
 * The software is used to generate the hexa-file and dump it into microcontroller. 

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
|`    `HL01|` `The user can unlock the door by using password. | Implemented |
|`    `HL02|` `The user can change the password of the door.| Implemented |
|`    `HL03|` `If the user is around the room the door automatically gets open. | Yet to be Implemented |
|`    `HL04|` `The Blink App is used to control the appliances wirelessly.| Yet to be Implemented |
|`    `HL05|` `Electricity Bill is calculated based on units consumed.| Yet to be Implemented |
|`    `HL06|` `The user can monitor its energy consumption and the bill amount in ‘io.adafruit’ website.| Yet to be Implemented |
|`    `HL07|` `The user gets automatic update of electric bill via mail if threshold value is reached.| Yet to be Implemented |

## LOW Level Requirements:


|`      `**ID**|`                 `**Description**|`            `**Status**|
| :- | :- | :- |
|LL01\_HL01|` `The user has to press the password in 4x3 keypad.| Implemented |
|LL02\_HL02|` `The user has to press ‘#’ to reset the password.|Implemented |
|LL03\_HL02|` `The user has to enter the current password to reset the password.|Implemented |
|LL04\_HL03|` `If the user is around 200cm of the ultra-sonic sensor, the door gets open.|Yet to be Implemented |
|LL05\_Hl04|` `The Blink app can be configured for different rooms to operate the different appliances.|Yet to be Implemented |
|LL06\_Hl06|` `The adafruit website has two different gauge one to monitor energy consumption and other to monitor bill.|Yet to be Implemented |
|LL07\_Hl07|` `The email can be send using IFTTT (if this then that) feature of ‘io.adafruit’ website  which generates the email if threshold value is reached.| Yet to be Implemented |




