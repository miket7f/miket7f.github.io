---
layout: page
title: Flight
permalink: flight
---
## This path is work in progress!
The material that we provide in the following levels is by now means complete but it might help you to learn about the subject yourself, while we are working on providing content for you! 

## Level 1 - Flight Data Storage
### Lecture
Now, we have implemented the microcontroller and its sensors. Basically, we have created a data logger. Our flight computer is now able to interpret its environment. However, it can not yet intervene. The flight computer might notice that it is unstable by 30° in the yaw axis. However, it has no way of changing those circumstances yet. Here, the flight computer's outputs come into play. 

We will learn about the most vital output types for model rocketry and can subdivide them into:
- flight data storage
- indicators
- pyro channels
- and servo control

Indicators visually represent flight states or current errors to the user using LEDs, speakers, or displays. 

Pyro channels are needed to ignite model rocket engines and to trigger heating wires. With heating wires, we can, in turn, control various mechanisms, such as landing legs, air brakes, and the deployment of our parachute. 

And servo control is needed to steer our thrust vector control system (TVC) to actively stabilize our rocket. 

After performing model rocket flights, we want to be able to analyze them to identify potential problems or to assess the rocket's performance. To do so, we must be able to access the flight's sensor data and microcontroller's decisions. However, as of right now, all the flight data is lost immediately. To counteract this, we have to store our flight data through SD cards or flash memory chips. 

We will look at the flight data storage implementation at this level. 
#### SD Card
As previously mentioned, an SD card is a Flash storage with a specific form factor. There are micro SD cards and regular SD cards. For most flight computers, we will use micro SD cards to spare PCB space. 

SD cards come with different specifications. Most important are their storage capacity, used file system, and speed class. 

The storage capacity of an SD card is given in Bytes. You might know that a byte is the same as 8-bit. A bit has two conditions — either zero or one, while a byte has 2^8 conditions — for example, a number from 0 to 255. 

Usually, SD cards come in the range of Gigabytes to Terabytes, which are enormous units. Their storage capacities are ranked in steps of two. So, there are 2GB, 4GB, 8GB, and so on versions. 

There are SD card categories based on their capacity:
- SDSC (Secure Digital Standard Capacity) for capacities of up to 2GB
- SDHC (Secure Digital High Capacity) for capacities from 4GB to 32GB
- and SDXC (Secure Digital Extended Capacity) for capacities of over 32GB

These SD cards use different file systems based on their category.
SDSC cards mostly use the FAT16 file system, while SDHC cards use FAT32, and SDXC cards use exFAT. The used file system is essential when selecting the appropriate SD card for your project. The FAT32 system, for example, is universally supported on many microcontrollers and data-logging libraries. The Arduino SDFat library, for example, works with the FAT32 file system. 

For our use cases, almost any storage capacity can seal the deal, as we store data lines that don't require much storage. Most of our launches don't record more than an MB of data. Still, we recommend using an SDHC card, as it uses FAT32, and since smaller-sized SD cards are often more scarce. 

When selecting an SD card, it's important to consider the reading and writing speeds, typically measured in megabytes per second (MB/s). These speeds determine how quickly we can read or write data from the SD card.

There are several speed rating systems for SD cards, which include:
- Speed Class
- UHS Speed Class (Ultra High Speed)
- Video Speed Class
- Application Performance Class
- UHS Bus Interface

However, almost any speed rating will do the job for us. The exact speed classes are most important for videography and photography.
#### Implementation
We can add an SD card connector to our PCB to implement an SD card storage. There are two ways in which those connectors hold the SD card in place. There are spring-loaded connectors, which feature a spring mechanism to secure the SD card. This mechanism facilitates easy removal. Further, there are pluggable connectors, which offer a simple, friction-based connection for easy insertion and removal of the SD card without additional locking mechanisms.

When connecting the SD card, we use SPI. 
The SD card needs to be powered by 3.3V with an added decoupling capacitor of 100nF. 
We connect the 
- SCK to CLK
- MISO to DAT0, 
- MOSI to CMD
- and the chip select to the CD or DAT3 pin. 
Through those simple connections, the microcontroller can interface with the SD card seamlessly.

#### Flash Chip
Another way of storing flight data is by using a flash memory chip. Often, it is advisable to implement both an SD card and a Flash simultaneously to add redundancy. 

Even though an SD card is a type of flash memory, there are still distinct differences between the two implementations. SD cards are removable, while flash memory chips are soldered directly onto the PCB. 

- This makes flash chips less susceptible to vibrations, which is crucial for stable data storage during rocket launches. 
- Further, flash memory chips have a neater form factor compared to SD card slots, potentially saving space on the PCB. 
- Retrieving data from an SD card is straightforward. We can detach it and assess the data on a PC. 
- Accessing data stored on a flash memory chip requires the microcontroller or another PCB to read out the information, which can be more complex.

The implementation of a flash memory chip is very similar to the implementation of an SD card slot. Most of the time, we will also interface the flash with the SPI protocol. Notably, there are also flash memory chips that we could interface with an even faster protocol like QSPI. 
Like SD cards, flash memory chips require a 3.3V power supply with a decoupling capacitor (e.g., 100nF) for stable operation.

#### Summary
So, for us to be able to make post-flight analysis, we have to implement some data storage.

The two most viable options are an SD card slot or a flash memory chip. 

An SD card is, in essence, a flash memory with a specific form factor. There are micro SD cards, mini SD cards, and SD cards. When selecting an SD card, we must watch out for several specifications. They are categorized based on their storage capacity into SDSC, SDHC, and SDXC cards. Depending on the class, they come with different file formats. The most supported format for microcontrollers and data logging libraries is the FAT32 system implemented on the SDHC cards. Therefore, it is advisable to choose such an SDHC card that ranges from 2 to 32GB. When it comes to reading and writing speed, there are different categorizations. However, most of them are sufficient for our use cases. 

On the other hand, we could use a flash memory chip. Those come with the advantage of being directly soldered to the PCB, which makes them less prone to vibrations, as there is no plugged connection. Further, it allows them to be neater, contributing to a smaller PCB footprint. On the contrary, reading them out can be more complex to do. A good design practice is to add a flash memory chip as a second source of flight data storage for redundancy. 

A final method we have not yet mentioned is to use the microcontroller's flash memory to store flight data. We did implement this methodology on the Buffalo performance flight computer design.

## Level 2 - Indicator
#### LED
The first and easiest output to set up is an LED. LEDs are invaluable in flight computers for providing visual indications to the user. They can show that the board is powered on, indicate current flight states, and serve various other signaling purposes.

An LED (Light Emitting Diode) is a diode that emits light when current flows through it in the forward direction. Similar to other diodes, an LED is not conductive in reverse bias. When the applied voltage reaches the LED's forward voltage, the LED becomes conductive and lights up. The forward voltage is the specific voltage at which the LED begins to emit light in forward bias.

The forward voltage varies based on the LED's color:
- A red LED typically has a forward voltage of 1.8-2.2V.
- A green LED generally requires 2-3V.
- A blue LED usually needs 3-3.5V.

These values are typical, but LEDs come in various forms with different specifications. Therefore, always check the datasheet for the specific LED you are using to ensure proper operation.

Now what would happen if we connected one of those LEDs to our 3.3V source in forward-bias?
Let's assume we have a red LED with a forward voltage of 2V. 
The LED becomes conductive wand wants to have a voltage drop of 2V across it. However, as we applied 3.3V, the remaining 1.3V must be dropped somewhere in the circuit according to the Kirchhoff's voltage law. As there is no other component, the excess voltage must be dropped across its internal resistance ESR, which is very low. This would lead to a very high current, overheating of the diode, and finally destruction of the diode. 

$I = \dfrac{V_{excess}}{R_{LED}}$

To make the schematic work on the long-term we have to limit this current. 
This is done my a current limiting resistor. 
Every LED also gives a maximum rated current that is often between 5 to 20mA. 
Many LEDs operate across the current range. Generally, the higher the current the brighter the LED. So, we know that the voltage across the resistor must be 1.3V and we want to have current of 10mA. With those two parameters we are able to directly calculate the resistor.

$R_{lim} = \dfrac{V_{excess}}{I_{LED}}$

If we want to control the LEDs with our microcontroller, we can hook their anode to one of its GPIO pins. If we toggle the GPIO, a voltage of 3.3V is applied to the LED and the LED lights up. 

##### RGB LED 
An LED type that is even more useful for model rocket applications, is the RGB LED. RGB stands for the colors red, green, and blue. It is a widely used color scheme, as every other color except black can be created with those three colors if their proportions are varied accordingly. If all three LEDs are at the same brightness, the color white is created. If red and green light up we get yellow. There are color wheels online that can show you the exact ratios to create any colors you want. 

An RGB LED houses those three LEDs in a single package. Its implementation is basically the same, as the implementation of a single LED, but the process repeated thrice. And as every color has a different voltage drop we have to calculate the current limiting resistor for all three separately. 

##### Low-side Driver
When driving the LEDs with the microcontroller we have to be aware of the maximum current ratings of the microcontroller's GPIO pins. 
The ESP32 can provide up to 40mA per single pin, which is more than enough to directly drive an LED. The STM32F7 allows for up to 25mA per single pin, which is also sufficient to provide LEDs with power.

However, the Teensy 4.1 only allows for 10mA per pin. In this case, we would have either to reduce the brightness and the current of the LED, or we have to figure out another way of powering the LED without damaging the microcontroller. An easy way would be to interpose a BJT transistor with which we then turn on the LED. 

But, there are also special components to do the job, so called driver ICs. 
A very famous one the ULN2003A, is basically a transistor array, which allows to control high currents with low-current control signals. It basically consists of 7 outputs that can be controlled individually. There are two kinds of driver ICs low-side and the high-side drivers.
A low-side driver interposes the circuit between the load and the GND, while a high-side driver interposes between the source and the load. The low side driver is easier to control, as the gate of the transistor is referenced to the GND signal. So, it is easier to interface from microcontrollers. 
The ULN2003A is also a low-side driver IC.

Another advantage of a low-side driver is that different components can be connected to different source voltages. When implementing the ULN2003A, we have to connect the common ground. The control signals on the one side and the loads with their source voltages on the other side. 
Further, we have to keep in mind that the BJT transistors inside the driver, have a voltage drop of 0.9V @100mA. We have to take this voltage drop into account when calculating the current limiting resistor! The ULN2003A is able to source 500mA per channel and a total of 2.5A for the entire IC. If we need to control a device with more than 500mA, we can simple unite two channels which doubles the allowed current flow. 

If we were to switch inductive loads, we have to connect the COM port of the IC. When the Darlington transistor switches off, the inductive load attempts to maintain current flow, which can cause a voltage spike. The freewheeling diode, connected between the load and the COM pin, allows this current to continue flowing in a loop, preventing the voltage spike from damaging the transistor or other components in the circuit. 

#### Buzzer
While the LED provide visual confirmation, a Buzzer provides acoustic information. 
There are different types of buzzers, but one common type is the electromagnetic buzzer, which 
works based on the principle of electromagnetic induction. 
It consist of a coil (the electromagnet), a diaphragm with a permanent magnet, and a housing. 

When the electromagnet is energized, it creates a magnetic field that attracts or repels the diaphragm, causing it to move. This movement of the diaphragm creates a soundwave that we can hear. To create this movement, an electrical signal (usually an alternating current or a pulsating direct current) is applied to the coil. The faster the speed of the movement the higher the note that is produced. 

There are two types of buzzer as components that can be bought. There active and passive (or externally driven) buzzers. The active buzzer already incorporates an IC inside its enclosure that creates an alternating electric signal that causes the membrane to move in its resonance frequency. Active buzzer must only be connected to a steady DC voltage of, for example, 3.3V and then the begin to sound. As those buzzers feature the drive circuit internally, their notes can not be controlled. 

Then there are passive buzzers. Those have to be controlled externally, and feature no internal IC. Through that we can vary the alternating frequency and, therefore, the note it produces. We control those externally driven buzzers by pulsing DC current. The pulsing method commonly used is PWM, which we will look at later in this Level when we discuss servo control. 

Regarding the implementation of the buzzer, we do not have to take many things into account. We do not need a current limiting resistor. When selecting, we have to look at its decibel rating, so we can chose a buzzer with a sufficient loudness, and we have to look at its current draw to determine whether or not we have to use a low-side driver. 
### Summary


## Level 3 - Pyro Channels
### Lecture
One of the most important outputs on our flight computers are the pyro channels. Those are needed to control pyrotechnic devices such as heating wires and electric igniters. Many mechanical systems that we use on our rockets are deployed by heating wires. The deployment via heating wires bears the benefit of forming less complex, lighter, more reliable, and smaller deployment systems. Additionally, the rocket's engines must be able to use electric igniters. These can also be controlled with this system.

When controlling heating wires and electric igniters, the biggest problem that comes into play is that they are causing very high current flows that can be as high as several amps. This means that they cannot be controlled via a standard microcontroller output pin. Additionally, in case of an overload, the microcontroller should be protected from severe damage.

##### Circuit
Therefore, we need to create a specific driving circuit. The circuit is directly powered by the LiPo battery, as the regulated power supplies cannot withstand these high currents, and because minimal voltage differences are not important to the functionality of the application. 

The heating wires and electric igniters are connected to the flight computer by a screw barrier terminal block. In the case of the Stack flight computer their are connected by pluggable terminal blocks, which come of the advantage of being easily accessible when installed in the rocket. 

The source of the battery is connected to one of the two pins of the terminal block, while the other pin is connected to the drain of a N-channel MOSFET. The source of the MOSFET is connected to GND. 
The gate of the MOSFET is pulled down to ground by a 2k resistor. This prevents the pyro channel from accidentally deploying pyro technic devices because of interferences.
Furthermore, these pyro channels feature status LEDs (Light Emitting Diodes) that indicate if they are turned on. 

To switch a pyro channel on, the microcontroller sets the output pin high which is connected to the gate of the MOSFET. This creates a voltage difference between the gate and source of the MOSFET, which eventually makes the MOSFET conductive so that current can flow. To ensure that the MOSFET turns on it is important that the voltage difference is larger than the minimal gate source voltage our MOSFET requires. (Vgs = 3V) Further it is important to add a current limiting resistor to the gate of the MOSFET, as the internal capacitance of the MOSFET leads to a current spike when turning it on. This current spike could damage the microcontroller and can be prevented by this resistor. 

The last thing to consider is the current ratings of the MOSFET and the barrier terminal block. Our MOSFET is able to withstand a continuous drain source current of 50A and a drain source voltage of 30V. Its power dissipation rating is 60W, which means that the MOSFET can safely dissipate up to 60 watts of power without overheating or experiencing failure. 
#### Summary


## Level 4 - PWM for Servo
### Lecture
To be able to control the servos that are located inside our thrust vector control system, we have to understand the concept of PWM (pulse width modulation). As we mentioned previously, most microcontrollers are only able to create digital outputs and often do not feature a DAC. Instead they switch the outputs on and off continuously to get a voltage that falls between the maximum 3.3V and 0V. The voltage that is achieved depends on the duty cycle of the signal, which is the ratio of the active time over the total time. To create a steady voltage this signal must than be filtered by adding a capacitor to the circuit. 

In a case of controlling a servo, we use the same principle, but spare the capacitor. 
A servo motor is a type of electric motor that incorporates a potentiometer. The potentiometer, also known as a variable resistor, consists of a rotary component that changes its resistance as it rotates. This rotation is directly linked to the position of the servo motor's output shaft. Through that the servo can accurately control its horn position. Consequently, most servos are limited to a range between -90 and +90 degrees in rotation. The potentiometer within the servo provides feedback to the servo controller, allowing it to adjust the motor's position to match the desired angle specified by the PWM signal. 

Servos have three wires. The power line that requires anything from 4 to 6V, the GND line, and the signal line. On the signal line, we provide the servos with information of what angle it shall target. This information is provided by a PWM signal with a duration of 20ms.
An active period of 1.5ms corresponds to the center position of the servo, so 0°.
An active period of 2ms corresponds to plus 90°, and an active period of 1ms corresponds to -90°. Anything in-between corresponds to the other angle values. Servos interpolate between these extremes based on the pulse width received. For example, a pulse width of 1.75ms corresponds to +45 degrees, while 1.25ms corresponds to -45 degrees. Through alternating the active period, we can indicate which angle the servo should take on. 

> Oscilloscope for PWM analysis 


#### Summary
LEDs are diodes that emit light in forward bias. They have a forward voltage that should drop across them and a rated current. To limit the current, when a voltage that is larger than the forward voltage is applied, a current limiting resistor is interposed. 
RGB LEDs use the three colors red, green, and blue to create any color and are often incorporated into a single package. 

For microcontrollers with too little GPIO output current, a driver IC can be used. The driver IC is basically a transistor array that allows to control high currents with low current microcontroller, while adding protection to the microcontroller. A low-side driver is easiest to use as the gate voltages are referenced to ground, and different source voltages can be on the load side. The transistor is basically interposed between the load and GND, compared to the high-side driver that is interposed between source and the load. 

Buzzers work by an electromagnet that moves a diaphragm. The oscillation of the diaphragm creates sound waves that we are able to hear. The oscillation is either created by an already incorporated IC than the buzzer is an active buzzer. Or we have to create this control signal by PWM, which additionally allows as to alter the pitch. 

Pyro channels are needed to trigger heating wires and electric ignitors. The basically interpose an N-channel MOSFET between the battery source and GND. The heating wires and electric ignitors are connected to a screw terminal that has the battery voltage connected to one pin and the drain of the MOSFET to the other pin. The MOSFET is controlled by a voltage that the microcontroller applies to the gate. It also features a pull-down resistor between gate and source, to prevent accidental power on, and adds a current limiting resistor to the gate to protect the microcontroller. We can add an LED to indicate when the pyro channel is turned. 

Servos are electric motors that feature a potentiometer for closed-loop angle control, and often only have a range of motion of +-90°. To control them a PWM signal with a duration of 20ms is supplied. The active region tells the servo which angle it shall target. If its 1ms it should steer to -90, if it's 1.5ms it should reach 0°, and if it is 2ms it should target +90°.

Finally, an SD card is flash storage that we can interface by SPI to store flight data. There are two types one that secures the SD card by a click (spring-loaded), and ones that secure the SD card by friction. 
