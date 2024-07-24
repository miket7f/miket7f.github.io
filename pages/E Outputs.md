---
layout: page
title: Flight
permalink: flight
---
## This path is work in progress!
The material that we provide in the following levels is by now means complete but it might help you to learn about the subject yourself, while we are working on providing content for you! 

## Level 1 - Flight Data Storage
<iframe width="560" height="315" src="https://www.youtube.com/embed/tjG84FDy4Ak?si=PKYHxn0xzuraWT9S" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Now, we have implemented the microcontroller and its sensors. Our flight computer is now able to interpret its environment, but it cannot yet take any corrective action. The flight computer might notice that it is unstable by 30° in the yaw axis. However, there is no way of changing those circumstances yet. Here, the flight computer's outputs come into play. 

We will learn about the most vital output types for model rocketry and can subdivide them into:
- flight data storage
- indicators
- pyro channels
- and actuators

Indicators visually represent flight states or current errors to the user using LEDs, speakers, or displays. 

Pyro channels are needed to ignite model rocket engines and to trigger heating wires. With heating wires, we can, in turn, control various mechanisms, such as landing legs, air brakes, and the deployment of our parachute. 

And finally, an actuator is needed to steer our thrust vector control system (TVC) to stabilize our rocket actively. 

After performing model rocket flights, we want to be able to analyze them to identify potential problems or to assess the rocket's performance. To do so, we must be able to access the flight's sensor data and microcontroller's decisions. However, as of right now, all the flight data is lost immediately. Therefore, we must store our flight data through SD cards or flash memory chips. 

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

For our use cases, almost any storage capacity can seal the deal, as we store data lines that don't require much storage. Most of our launches don't record more than MBs of data. Still, we recommend using an SDHC card, as it uses FAT32, and since smaller-sized SD cards are often more scarce. 

When selecting an SD card, it's important to consider the reading and writing speeds, typically measured in megabytes per second (MB/s). These speeds determine how quickly we can read or write data from the SD card.

There are several speed rating systems for SD cards, which include:
- Speed Class
- UHS Speed Class (Ultra High Speed)
- Video Speed Class
- Application Performance Class
- UHS Bus Interface

However, almost any speed rating will do the job for us. The exact speed classes are most important for videography and photography.
#### Implementation
We can add an SD card connector to our PCB to which we can insert an SD card. There are two ways in which those connectors hold the SD card in place. There are spring-loaded connectors, which feature a spring mechanism to secure the SD card. This mechanism facilitates easy removal. Further, there are pluggable connectors, which offer a simple, friction-based connection for easy insertion and removal of the SD card without additional locking mechanisms.

When connecting the SD card, we use SPI. 
The SD card needs to be powered by 3.3V with an added decoupling capacitor of 100nF. 
We connect the 
- SCK to CLK
- MISO to DAT0
- MOSI to CMD (Command Line)
- and the chip select to the CD or DAT3 pin. 
Through those simple connections, the microcontroller can interface with the SD card seamlessly.

#### Flash Chip
Another way of storing flight data is by using a flash memory chip. Often, it is advisable to implement both an SD card and a Flash simultaneously to add redundancy. 

Even though an SD card is a type of flash memory, there are still distinct differences between the two implementations. 

SD cards are removable, while flash memory chips are soldered directly onto the PCB. 
- This makes flash chips less susceptible to vibrations, which is crucial for stable data storage during rocket launches. 
- Further, flash memory chips have a neater form factor compared to SD card slots, potentially saving space on the PCB. 
- Retrieving data from an SD card is straightforward. We can detach it and assess the data on a PC. 
- Accessing data stored on a flash memory chip requires the microcontroller or another PCB to read out the information, which can be more complex.

The implementation of a flash memory chip is very similar to the implementation of an SD card slot. Most of the time, we will also interface the flash with the SPI protocol. Notably, there are also flash memory chips that we could interface with an even faster protocol like QSPI. 
Like SD cards, flash memory chips mostly require a 3.3V power supply with a decoupling capacitor (e.g., 100nF) for stable operation.

#### Summary
So, for us to be able to make post-flight analysis, we have to implement some data storage.

The two most viable options are an SD card slot or a flash memory chip. 

An SD card is, in essence, a flash memory with a specific form factor. There are micro SD cards, mini SD cards, and SD cards. When selecting an SD card, we must watch out for several specifications. They are categorized based on their storage capacity into SDSC, SDHC, and SDXC cards. Depending on the class, they come with different file formats. The most supported format for microcontrollers and data logging libraries is the FAT32 system implemented on the SDHC cards. Therefore, it is advisable to choose such an SDHC card that ranges from 2 to 32GB. When it comes to reading and writing speed, there are different categorizations. However, most of them are sufficient for our use cases. 

On the other hand, we could use a flash memory chip. Those come with the advantage of being directly soldered to the PCB, which makes them less prone to vibrations, as there is no plugged connection. Further, it allows them to be neater, contributing to a smaller PCB footprint. On the contrary, reading them out can be more complex to do. A good design practice is to add a flash memory chip as a second source of flight data storage for redundancy. 

A final method we have not yet mentioned is to use the microcontroller's flash memory to store flight data. The ESP32-WROOM-32-N8, for example, already features an internal 8MB Flash memory, which we could use for flight data storage. We did implement this methodology on the Buffalo performance flight computer design.

## Level 2 - Indicator
<iframe width="560" height="315" src="https://www.youtube.com/embed/07J46OSvcYg?si=bETE_a_Bxa0dpghP" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Indicators are crucial components in flight computers, providing essential feedback through visual and acoustic signals. In this lecture, we will explore various types of indicators.

We will start by learning about LEDs, including the need for and calculation of a current-limiting resistor. We will also cover the RGB LED, a versatile form of LED that allows for the creation of various colors.

Next, we'll delve into driver ICs, focusing on both low-side and high-side drivers, which we will need in case our output exceeds the microcontroller's GPIO rated current. 

We will then examine buzzers, exploring the differences between active and passive types and their applications.

Finally, we will discuss speakers, highlighting how they produce a range of sounds and how audio amplifiers like the MAX98357 can enhance audio performance in flight computers.
#### LED
The first and easiest output to set up is an LED. LEDs are invaluable in flight computers for providing visual indications to the user. They can indicate that the board is powered on, illustrate current flight states, and serve other signaling purposes.

An LED (Light Emitting Diode) is a diode that emits light when current flows through it in the forward direction. When the applied voltage reaches the LED's forward voltage, the LED becomes conductive and lights up. The forward voltage is the specific voltage at which the LED begins to emit light in forward bias.

The forward voltage varies based on the LED's color:
- A red LED typically has a forward voltage of 1.6-2V.
- A green LED generally requires 1.9-4.0V.
- A blue LED usually needs 2.5-3.7V.

These values are typical, but LEDs come in various forms with different specifications. Therefore, always check the datasheet for the specific LED you are using to ensure proper operation.

Similar to other diodes, an LED is not conductive in reverse bias. 

Now, what would happen if we connected one of those LEDs to our 3.3V source in forward bias? Let's assume we have a red LED with a forward voltage of 2V. The LED becomes conductive and wants a voltage drop of 2V across it. However, as we applied 3.3V, the remaining 1.3V must be dropped somewhere in the circuit according to Kirchhoff's voltage law. As there is no other component, the excess voltage must be dropped across its internal resistance ESR, which is very low. This low resistance would lead to a very high current, would overheat the diode, and lead to its destruction. 

$I = \dfrac{V_{excess}}{R_{LED}}$

To make the schematic work in the long term, we have to limit this current. This is done by a current-limiting resistor. Every LED also gives a maximum rated current, often between 5 to 20mA. Many LEDs operate across this current range. Generally, the higher the current, the brighter the LED's light. So, we know that the voltage across the resistor must be 1.3V, and by selecting a current that falls in the allowed current range of the LED, we can directly calculate the resistor.

$R_{lim} = \dfrac{V_{excess}}{I_{LED}}$

If we want to control a LEDs with our microcontroller, we can hook its anode to one of its GPIO pins. If we toggle the GPIO, a voltage of 3.3V is applied to the LED, and the LED lights up. 

https://www.circuitbread.com/ee-faq/the-forward-voltages-of-different-leds#:~:text=What%20you%20should%20find%20is,current%20required%20when%20using%20them.


#### RGB LED 
An even more useful type of LED for model rocket applications is the RGB LED. RGB stands for red, green, and blue, a widely used color scheme. By varying the proportions of these three colors, you can create virtually any color except black. For example, combining all three at the same brightness produces white, while red and green together produce yellow. You can use online color wheels to find the exact ratios needed to create specific colors.

An RGB LED houses all three LEDs (red, green, and blue) in a single package. The implementation is similar to using a single LED but repeated three times—once for each color. Since each color has a different voltage drop, you must calculate the current limiting resistor separately for each one.

#### Low-side Driver
When driving the LEDs with the microcontroller we have to be aware of the maximum current ratings of the microcontroller's GPIO pins. 
The ESP32 can provide up to 40mA per single pin, which is more than enough to directly drive an LED. The STM32F7 allows for up to 25mA per single pin, which is also sufficient to provide LEDs with power.

However, the Teensy 4.1 only allows for 10mA per pin. In this case, we would have either to reduce the brightness and the current of the LED, or we have to figure out another way of powering the LED without damaging the microcontroller. An easy way would be to interpose a BJT transistor with which we then turn on the LED. 

There are also specialized components designed to control high currents with low-current control signals, known as driver ICs. A very famous example is the ULN2003A, a transistor array that allows control of high currents with low-current control signals. It consists of 7 outputs that can be controlled individually.

Driver ICs are divided into two categories: low-side and high-side drivers. A low-side driver interrupts the circuit between the load and ground (GND), while a high-side driver interposes between the power source and the load. The low-side driver is easier to control with a microcontroller because the gate of the transistor is referenced to the ground signal. The ULN2003A is an example of a low-side driver IC.

An advantage of a low-side driver is that different components can be connected to different source voltages. Now, let's look at how to implement the ULN2003A in your project:

When implementing the ULN2003A, you need to connect the common ground. The control signals are on one side of the IC, and the loads with their source voltages are on the other side. It is important to consider that the BJT transistors inside the driver have a voltage drop of 0.9V at 100mA, which must be taken into account when calculating the current-limiting resistor. The ULN2003A can source 500mA per channel and a total of 2.5A for the entire IC. If you need to control a device requiring more than 500mA, you can simply unite two channels to double the allowed current flow.

When switching inductive loads, it is essential to connect the COM port of the IC. When the Darlington transistor switches off, the inductive load attempts to maintain current flow, which can cause a voltage spike. The freewheeling diode, connected between the load and the COM pin, allows this current to continue flowing in a loop, preventing the voltage spike from damaging the transistor or other components in the circuit.
#### Buzzer
While LEDs provide visual confirmation, a buzzer provides acoustic information. There are different types of buzzers, but one common type is the electromagnetic buzzer, which works based on the principle of electromagnetic induction. It consists of a coil (the electromagnet), a diaphragm with a permanent magnet, and a housing.

When the electromagnet is energized, it creates a magnetic field that attracts or repels the diaphragm, causing it to move. This movement of the diaphragm creates a sound wave that we can hear. To create this movement, an electrical signal (usually an alternating current or a pulsating direct current) is applied to the coil. The faster the diaphragm moves, the higher the pitch of the sound produced.

There are two types of buzzers available: active and passive (or externally driven) buzzers. The active buzzer incorporates an IC inside its enclosure that generates an alternating electric signal, causing the diaphragm to move at its resonance frequency. An active buzzer needs only to be connected to a steady DC voltage (e.g., 3.3V) to start sounding. Since the drive circuit is internal, the pitch of the sound cannot be controlled.

Passive buzzers, on the other hand, require external control and do not contain an internal IC. By varying the alternating frequency, we can control the pitch of the sound they produce. Externally driven buzzers are controlled by pulsing DC current, commonly using Pulse Width Modulation (PWM), which we will discuss later when we cover servo control.

When implementing a buzzer, there are a few considerations to keep in mind.
Firstly, we do not need a current-limiting resistor because buzzers are typically designed to operate within a specific voltage range and draw a fixed amount of current when powered within that range.

Secondly, when selecting a buzzer, it is important to choose one with a decibel rating that is appropriate for your application. For instance, a higher decibel rating is needed if the buzzer needs to be heard in a noisy environment or from a greater distance.

Finally, we must consider its current draw because if the buzzer draws more current than the microcontroller can supply directly, you may need to use a driver circuit.

#### Speaker
Speakers are similar to passive buzzers in their construction, consisting of a diaphragm, a voice coil, and a magnet. When an alternating current passes through the voice coil, it generates a magnetic field that interacts with the magnet, causing the diaphragm to move and produce sound waves.

Speakers are capable of producing a wider range of sounds compared to buzzers. They can reproduce complex audio signals, such as voice or music, making them useful for sophisticated acoustic indications in flight computers.

However, speakers require a driving circuit to produce sound at sufficient volume. This is where amplifiers come into play. An amplifier boosts weak audio signals from digital sources or microcontrollers to levels that can effectively drive speakers. Without an amplifier, these audio signals might be too weak to produce sound at a sufficient volume.

##### Audio Amplifier
An amplifier that is often used is the MAX98357. The MAX98357 is a digital input, Class D audio amplifier designed to drive speakers directly. It converts digital audio signals into high-quality sound and operates using the I2S (Inter-IC Sound) protocol. This amplifier also allows for the selection of mono or stereo sound output.

Amplifiers are categorized into different classes based on their circuit topology and how they handle the input signal. Class D amplifiers, like the MAX98357, are known for their high efficiency because they operate the output transistors as switches, rapidly turning them on and off. This switching mechanism reduces heat generation and improves power efficiency, making Class D amplifiers ideal for battery-powered and heat-sensitive applications.

#### Mono vs Stereo
Audio systems can be configured in various ways to suit different needs. Two common configurations are mono and stereo.

In a **mono** audio setup, the same audio signal is sent to all speakers. This means that regardless of how many speakers are used, they all reproduce the same audio signal. Mono audio is simple and effective for applications where spatial audio effects are not necessary, such as basic alert sounds.

In contrast, **stereo** audio uses two channels: left and right. Each channel carries a different audio signal, which creates a sense of directionality and space. This setup plays slightly different sounds through each speaker, mimicking how we naturally perceive sounds from various directions. Stereo audio is ideal for music playback, video soundtracks, and any application where a richer and more immersive audio experience is desired.

#### Summary
Indicators such as LEDs, buzzers, and speakers are essential components in flight computer design, providing visual and acoustic feedback to the user. Let's summarize the key points for each type of indicator:

Light-emitting diodes or LEDs emit light and become conductive when the applied voltage reaches the LED's forward voltage. The forward voltage is the specific voltage at which the LED begins to emit light in forward bias and varies by color. 

If we aren't driving the LED at its forward voltage, we must interpose a current-limiting resistor that dissipates the excess voltage. We can calculate this resistor based on the voltage excess and its ideal current draw.

RGB LEDs combine red, green, and blue LEDs in one package, allowing the creation of various colors by adjusting the brightness of each LED. 

We can drive LEDs by connecting them to the GPIO pins of our microcontrollers. However, if the LED's current draw exceeds the allowed current of the GPIO pins, we have to use low-side drivers like the ULN2003A to prevent the GPIO pins from damage. These drivers interpose a transistor, which allows control of the LEDs while requiring little to no current. 

Buzzers produce sound through diaphragm movement induced by an electromagnet. Active buzzers contain an internal driving circuit and only need a steady DC voltage, while passive buzzers require an external signal, often controlled by PWM, which allows us to create various tones. Selection criteria include the decibel rating for loudness and current draw to determine if a low-side driver is needed.

Speakers are similar to passive buzzers but capable of producing a wider range of sounds, including complex audio signals. To use them it is advisable to add audio amplifiers, such as the MAX98357 to the circuit. They convert I2S audio signals to drive speakers. On that exact model, we can also select between mono and stereo audio.

By understanding and correctly implementing these indicators, a flight computer can provide clear and effective feedback, enhancing the user experience and ensuring proper operation during various flight states.

## Level 3 - Pyro Channels
<iframe width="560" height="315" src="https://www.youtube.com/embed/jJ9oiYAq7mc?si=yDr6gFXS-Yvrh11C" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
One of the most important outputs on our flight computers are the pyro channels. Those are needed to control pyrotechnic devices such as heating wires and electric igniters. 

Many mechanical systems that we use on our rockets are deployed by heating wires. The deployment via heating wires benefits from forming less complex, lighter, more reliable, and smaller deployment systems. Additionally, the rocket's engines must be able to use electric igniters. These can also be controlled with this system.

When controlling heating wires and electric igniters, the biggest problem that comes into play is that they are causing very high current flows that can be as high as several amps. Therefore, they cannot be controlled via a standard microcontroller output pin. Additionally, in case of an overload, the microcontroller should be protected from severe damage.

We need to create a specific driving circuit called a pyro channel. 
In this lecture, you will learn everything you need to design your pyro channel that suits your project's needs. 

First, we will discuss the typical current draws of heating wires and electric ignitors. 
Then, I will show you how to create the most basic form of such a pyro channel. 
Following that, we will elaborate on additional safety features, such as fuses, optocouplers, and low-side drivers. Finally, we will talk about indicator LEDs and continuity detection for our pyro channels. 

#### Electric Igniter
An electric igniter consists of a wire or wire loop embedded in a pyrotechnic material. When an electric current passes through the wire, it heats up due to electrical resistance. This heat raises the temperature of the surrounding pyrotechnic material until it reaches the ignition point and ignites.

Electric igniters typically require a current of several amperes, often in the range of 1.5 to 2.0 amps, to function properly. The voltage needed to ignite them depends on several factors, including the resistance of the ignitors, the number of ignitors used, and whether they are connected in series or parallel.

The resistance of electric igniters can vary significantly, typically ranging from 1 ohm to 10 ohms. This variation in resistance impacts the required voltage and current for ignition. For example, ignitors with lower resistance will draw more current for a given voltage, while those with higher resistance require higher voltage to achieve the same current draw.

When configuring multiple igniters, the arrangement (series or parallel) affects the total resistance and current draw. In a series configuration, the total resistance is the sum of the individual resistances, which means the current draw is lower, but the required voltage is higher. In a parallel configuration, the total resistance decreases, requiring more current but lower voltage to achieve ignition.

Let's assume we have an electric igniter with a resistance of 5 ohms and an ignition current of 1.5 amps. To determine the voltage needed to achieve this current, we use Ohm's Law:

$V=I*R$

Where V is the voltage, I is the current, and R is the resistance.
Plugging in the values:
$V=1.5A*5Ω=7.5 V$

So, a voltage of 7.5 volts is needed to pass 1.5 amps of current through the igniter.
If we use a voltage higher than 7.5 volts, the igniter will still ignite. However, if we use a voltage lower than 7.5 volts, the igniter may not heat up sufficiently to reach its ignition temperature, and thus it might fail to ignite.

When using two of these igniters in parallel, the total resistance of the combination is halved compared to the resistance of a single igniter. With the same 7.5 volts applied, the total current drawn by the parallel configuration will double. For example, if each igniter requires 1.5 amps, then two igniters in parallel will draw a total current of 3 amps. Adding more igniters in parallel will reduce the overall resistance and increase the total current proportionally.

In contrast, if you place two igniters in series, the combined resistance will be the sum of the individual resistances, which in this case would be 10 ohms. At the same voltage of 7.5 volts, this series configuration will result in 0.75A. 

Since this is less than the 1.5 amps required for each igniter to ignite, both igniters might not reach their ignition temperature and could fail to ignite. To ensure both igniters in series will ignite, you need to double the voltage to 15 volts.

In most applications, especially in pyrotechnics, where simultaneous ignition of multiple devices is required, parallel configurations are preferred. This setup allows for the simultaneous triggering of multiple igniters while keeping the voltage requirement constant. The total current increases with additional parallel igniters. 

For our designs, multi-electric igniter ignition was essential, as we had to use engine clusters. However, if your project does not require simultaneous multi-ignition, you might not need to deal with such complexities.

#### Heating Wire
Heating wires are similar to electric igniters in their operation. They consist of resistance wires with a specific resistance per meter. The resistance of the wire is influenced by its thickness: thinner wires have higher resistance, while thicker wires have lower resistance, as described by the following formula:

$R=\rho \frac{L}{A}​$

Where R is the resistance, ρ is the resistivity of the wire material, L is the length of the wire, and A is the cross-sectional area of the wire.

When a voltage is applied to the heating wire, a current flows through it. The power the wire dissipates as heat in the wire is given by:

$P= I^2 R$

If it generates too much, the wire may become damaged or break. We can control the time the wire is powered or adjust the voltage using Pulse Width Modulation (PWM) to manage heat generation. Additionally, by varying the length and thickness of the wire, we can influence its resistance and, consequently, the amount of heat generated.

Heating wires are commonly made from nichrome, a nickel-chromium alloy known for its high electrical resistance and ability to withstand high temperatures. These wires are used in various applications where controlled heating is required. For example, nichrome heating wires can be used to burn through cable ties or rubber bands, effectively cutting them and allowing for the deployment of mechanisms.

We acknowledge that using heating wires for mechanism deployment is an experimental approach. However, this method is valuable for its simplicity and effectiveness in model rocketry. By utilizing nichrome heating wires, you can achieve precise control over mechanisms such as the release of recovery systems or the separation of stages while also minimizing weight and complexity. 

Let's assume we have a Nichrome heating wire with a resistance of 15 Ω/m. We power this wire using a 3-cell LiPo battery (12.6V). If we use a wire length of 0.1 m, the wire’s resistance will be 1.5 Ω. This results in a current draw of 8.4 A. The power dissipated by the wire can be calculated using the formula $P=I^2*R$, which gives us 105.84 W. This power is too high for the wire to handle safely. Therefore, we must manage the power dissipation by adjusting the on-time or reducing the voltage with PWM to prevent damaging the wire due to excessive heat.

#### Basic Pyro Channel
Now that we have identified the devices we want to control, the next step is to figure out how to manage them effectively. In the case of the Buffalo L rocket, which utilizes an engine cluster with four to five engines, simultaneous ignition requires a substantial current supply. We need to supply a total current of up to 5 x 1.5A = 7.5A in a parallel configuration. 

Additionally, the heating wire we calculated earlier requires around 10 A for a brief period (a few milliseconds) to achieve the desired effect.

Therefore, we should assume that our pyro channel must be capable of switching on and off a device with the highest current draw, which - in this case - is the heating wire requiring 10A.

Furthermore, we must ensure that the power source can simultaneously deliver the required current for multiple pyro channels. For example, if we plan to activate two heating wires at once, the battery must be capable of supplying 2 × 10A = 20A.

Most often, the pyro channels are powered directly from the battery because regulated power supplies cannot handle such high currents. Additionally, minor voltage drops resulting from battery discharge are generally not critical to the application's functionality.

It is important to watch out for the C-rating of the battery to ensure that the battery can handle these high currents.

To manage these high currents, power MOSFETs that can handle the maximum current requirements are employed. In the setup, the battery's positive terminal is connected to one pin of a terminal block, and the other pin of the terminal block is connected to the drain of an N-channel MOSFET. The source of the MOSFET is connected to the ground (GND). 

To activate a pyro channel, the microcontroller sets the output pin high, which applies a voltage to the gate of the MOSFET. This creates a voltage difference between the gate and source, turning the MOSFET on and allowing current to flow. The gate-source voltage (Vgs) must exceed the minimum threshold required to entirely turn on the MOSFET (typically Vgs = 3V). 

Finally, it's critical to consider the current ratings of both the MOSFET and the terminal block. The chosen MOSFET can handle a continuous drain-source current of up to 50A and a drain-source voltage of 30V. It also has a power dissipation rating of 60W, ensuring it can safely dissipate up to 60 watts of power without overheating or failing.

For additional safety, a pull-down resistor should be added to the gate of the MOSFET and connected to the ground. This ensures that the MOSFET remains off and does not turn on accidentally due to floating or noise signals. A lower resistance value is preferable to minimize the risk of accidental switching; a typical value for this pull-down resistor might be 2kΩ.

Additionally, a current-limiting resistor should be placed in series with the gate of the MOSFET. This resistor protects the microcontroller from potential damage caused by the current spike resulting from the MOSFET's internal capacitance during switching.

We created the most basic form of a pyro channel. However, we can enhance the safety and practicality of the channel with the following additions:
For improved safety, we could add an optocoupler, a fuse, or a low-side driver.
For improved practicality, we could utilize indicator LEDs or continuity detection. 
Let's start by discussing additional safety features.
#### Optocoupler
An optocoupler is a component that transfers electrical signals between two isolated circuits using light. It typically consists of an LED and a photodetector, a transistor with a light-dependent base, housed in a single package. When an electrical signal energizes the LED, it emits light that is detected by the transistor's base which makes the transistor conductive.

In the pyro channel application, we place the optocoupler between the microcontroller and the MOSFET gate. The microcontroller activates the LED inside the optocoupler, which then triggers the photodetector. As the transistor switches the gate of the MOSFET, it allows the MOSFET to switch the high current from the battery to the igniter or heating wire.

The primary benefit of using an optocoupler is the electrical isolation it provides. This isolation separates the low-voltage control circuitry (the microcontroller) from the high-current switching side (the MOSFET and the power circuit). This setup protects the microcontroller from potential damage that could occur if the MOSFET fails or if there's an overcurrent situation.
#### Fuses
Fuses are safety devices designed to protect electrical circuits from overcurrent conditions. They contain a metal element that melts and breaks the circuit when the current exceeds a specified rating. This prevents excessive current from damaging components or causing overheating.

In a pyro channel, we can use fuses to protect our circuit from overcurrent situations. For instance, if a component like the MOSFET or wiring is subjected to a higher current than it can handle, the fuse will blow, disconnecting the circuit and preventing damage. Choosing a fuse with a rating slightly above the operating current but below the maximum tolerance of components ensures protection while allowing normal operation. 

For instance, if the heating wire is too short, leading to an excessive current that could exceed the MOSFET's maximum rating, the fuse will blow and disconnect the circuit, thereby protecting the MOSFET from damage. After such an event, we would have to replace the fuse to restore the circuit to operational status.
#### High Side Drivers
For additional protection of the microcontroller, an driver IC can be used and interposed between the microcontroller and the MOSFETs. To control N-channel MOSFETS we have to use a high side driver, as low-side drivers would have to be added between the MOSFET's source and GND. Consequently, a low side driver would have to bear the entire current load. Now back to the high side driver design. Switching the MOSFET on requires charging the MOSFET's internal capacitance, and if the current spike is too high, it could potentially damage the microcontroller. Thus, the higher switching capabilities of a driver could provide further protection for the microcontroller. However, keep in mind that this is not required if you are using an optocoupler, as it offers a different method for achieving protection and isolation.

To further improve the practicality of the pyro channel, we can incorporate additional features such as indicator LEDs and continuity detection.
#### Indicator
For the user to be aware of pyro channel activation, we can add an LED in parallel to the MOSFET. We could connect an LED in parallel to the MOSFET and the MOSFET's current limiting resistor. Additionally, we have to add a current limiting resistor for the LED. When the channel is activated, the LED lights up, signaling that the current is flowing and the channel is engaged. This feature helps to quickly verify whether the pyro channel is functioning correctly without needing to test the output directly.

However, an lighting LED doesn't imply that current is flowing through the MOSFET. It simply means that the microcontroller's output is on.
#### Continuity Detection 
This leads us to our next circuit: continuity detection.
It ensures that our heating wires and electric ignitors are connected and in good condition. We can implement a simple LED-based method to achieve this.

First, we add an LED to the second terminal block connected to the MOSFET. We then connect the LED to a current-limiting resistor and ground (GND) through a button. When we press the button, the LED lights up to indicate that the circuit is complete and that the pyrotechnic device is securely connected. If the LED does not light up, it suggests a problem with the connection or the device itself. We need to choose the current-limiting resistor carefully to prevent accidental ignition of the pyrotechnic device.

If the resistor is too small, the current that flows through the pyrotechnic device and the LED might be too high, causing the pyrotechnic device to be triggered. 
#### Connectors
Finally, let's talk about how we can connect our pyrotechnic devices to our PCB.
The heating wires and electric igniters are connected to the flight computer using terminal blocks, which provide a secure and reliable interface for electrical connections. The two most common ones we used are the screw terminal block and the pluggable systems terminal block. 

The **screw terminal block** uses screws to clamp down on the wires, creating a firm and stable connection. 

The **pluggable terminal block** features a plug-and-socket design. The socket is soldered to the PCB, while the plug is a separate component to which the wires are attached using screws. This design facilitates easy removal and replacement of heating wires or electric igniters.

Alternatively, wires can be directly soldered to the PCB, which provides a rigid connection but lacks the flexibility and ease of maintenance offered by terminal blocks.

#### Summary
In this lecture on pyro channels for flight computers, we explored the critical aspects of designing circuits to control pyrotechnic devices, including heating wires and electric igniters. These devices are essential for rocket deployment systems, with heating wires used for mechanisms like stage separation or recovery system deployment and electric igniters required for engine ignition.

 Electric igniters, which ignite by heating a wire embedded in pyrotechnic material, typically need a current of 1.5 to 2.0 amps. Their resistance ranges from 1 to 10 ohms, affecting the voltage and current requirements based on their configuration. Igniters can be connected in parallel or series, with parallel configurations being preferred for simultaneous ignition due to their lower voltage requirements.

Heating wires operate similarly, converting electrical power into heat through their resistance. The amount of heat generated depends on the wire's resistance, which is influenced by its thickness and length. Nichrome is a common material for heating wires due to its high resistance and heat tolerance. 

The basic design involves a power MOSFET that handles the high currents, with the microcontroller controlling the MOSFET's gate. Ensuring the MOSFET’s specifications (e.g., 50A continuous current) exceed the channel’s needs is crucial. Resistors play important roles; pull-down resistors on the MOSFET gate prevent accidental activation while current-limiting resistors protect the microcontroller from current spikes from the charging process of the MOSFET's gate.

For safety enhancements, we could add optocouplers to provide electrical isolation between the low-voltage control circuitry and the high-current circuit, fuses to protect the circuit from overcurrent situations, or low-side drivers instead of optocouplers as another means of protection the microcontroller against current spikes.

Other practical improvements include adding indicator LEDs for visual confirmation of channel activation and implementing continuity detection using an LED to verify the proper connection and functionality of the pyrotechnic device. This setup helps ensure that connections are intact before activation.

Connectors for these systems typically include screw terminal blocks, which provide a stable connection by clamping wires with screws, and pluggable terminal blocks, which offer a removable plug-and-socket design for ease of maintenance and replacement. Direct soldering of wires to the PCB is another option, providing a rigid but less flexible connection.

## Level 4 - Actuators
<iframe width="560" height="315" src="https://www.youtube.com/embed/aI1_r9nGbFY?si=xur6DId0YU9WiDF9" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
In this lecture on actuators, we will focus on servos for thrust vector control (TVC). While there are various types of actuators, including different motors, our primary focus will be on servos due to their critical role in TVC systems.

We will first discuss what a servo is and then refresh your knowledge of PWM and how it helps you to control a servo. 

#### Servo 
A servo motor is an electric motor equipped with a potentiometer, a type of variable resistor that is attached to the servo horn. A potentiometer changes its resistance as it rotates. The servo's potentiometer provides feedback of the Servo horn position to its controller, allowing precise adjustments to the motor's position. This setup enables the servo to accurately control its horn's position, typically within a range of -90 to +90 degrees. 

#### PWM
To control a servo, we have to recall the concept of PWM (pulse width modulation). As we mentioned previously, most microcontrollers can only create digital outputs and often do not feature a DAC. They switch the outputs on and off continuously to get a voltage that falls between the maximum 3.3V and 0V. The voltage that is achieved depends on the duty cycle of the signal, which is the ratio of the active time over the total time. We must filter this signal to create a smooth voltage by adding a capacitor to the circuit. 

When controlling a servo, we use the same principle but spare the capacitor. Servos are connected with three wires: the power line (requiring 4 to 6V), the ground line (GND), and the signal line. The signal line receives a PWM signal, which determines the angle the servo should target. The PWM signal has a period of 20ms, where an active period of 1.5ms represents the center position (0°), 2ms represents +90°, and 1ms represents -90°. Intermediate pulse widths correspond to intermediate angles. For example, a pulse width of 1.75ms translates to +45 degrees, while 1.25ms equates to -45 degrees. By varying the pulse width, the servo adjusts its angle accordingly.

Their ability to provide accurate feedback and adjust to specific angles with high repeatability makes them ideal for controlling the thrust vector direction in rockets. The feedback mechanisms they integrate ensure that the output shaft stays at the desired position, which is crucial for maintaining stable orientation. Additionally, servos are compact, often lightweight, and easily integrated into model rockets.

> Oscilloscope for PWM analysis 

#### Summary
Now, to summarize the entire chapter. 
To be able to analyze flights, we have to integrate some kind of flight data storage. To do so, we can either choose a flash memory chip, or an SD card, which is a flash memory with a specific form factor. It is important to choose an SD card with the right capacity, most often an SDHC card will do the job. Further, we have to choose the SD Card with the right file format. Here, an SD card of the type FAT32 is advisable, as it cooperates smoothly with many libraries. Both flash memories and SD cards can be interfaced by SPI. 

LEDs are diodes that emit light when in forward bias. They have a forward voltage that should drop across them and a rated current. To limit the current, when a voltage larger than the forward voltage is applied, a current-limiting resistor is used. RGB LEDs use three LEDs of the colors red, green, and blue to create any color except black.

For microcontrollers with insufficient GPIO output current, a driver IC can be used. The driver IC is a transistor array that allows control of high currents with the GPIO pins of the microcontroller. A low-side driver is easiest to use as the gate voltages are referenced to the ground, and different source voltages can be on the load side. The transistor is interposed between the load and GND, compared to the high-side driver that is interposed between the source and the load.

Buzzers work with an electromagnet that moves a diaphragm. The oscillation of the diaphragm creates sound waves that we can hear. We differentiate between active buzzers, which internally feature an IC that creates the oscillating signal, and passive buzzers, which require an external signal, such as PWM, to produce sound. The external signal allows us to alter the pitch. Speakers can also be used to produce sound and often require amplifiers to ensure the audio signal is strong enough to drive the speakers effectively.

Pyro channels are needed to trigger heating wires and electric ignitors. They interpose an N-channel MOSFET between the battery source and GND. The heating wires and electric ignitors are connected to a screw terminal that has the battery voltage connected to one pin and the drain of the MOSFET to the other pin. The MOSFET is controlled by a voltage that the microcontroller applies to the gate. It also features a pull-down resistor between the gate and the source to prevent accidental power and adds a current-limiting resistor to the gate to protect the microcontroller. Additional features could include optocouplers for electrical isolation, high-side drivers for GPIO pin protection, fuses for overcurrent protection, continuity detection to ensure proper heating wire or electric ignitor connections, and LEDs to indicate the status of the pyro channel.

Servos are electric motors that feature a potentiometer for closed-loop angle control and often only have a range of motion of ±90°. To control them, a PWM signal with a duration of 20 ms is supplied. The active region tells the servo which angle it shall target. If it's 1 ms, it should steer to -90°; if it's 1.5 ms, it should reach 0°; and if it is 2 ms, it should target +90°. However, this behavior can vary depending on the specific servo model, and there are exceptions to these standard pulse widths and ranges.