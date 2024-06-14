---
layout: page
title: Flight
permalink: flight
---
## This path is work in progress!
The material that we provide in the following levels is by now means complete but it might help you to learn about the subject yourself, while we are working on providing content for you! 

## Level 1 - Pin Types
### Lecture
As mentioned before, we can think of a microcontroller to be a mini computer. Compared to a real-computer, it comprises all the relevant parts in a single package, such as the processing cores, the program memory, and the input/output peripherals. 

#### Power
For a microcontroller to function, it has to be provided with power. Most microcontrollers use a 3.3V input voltage, and feature several pins to which we will have to provide power to. 

#### GPIO Pins
The first term we have to coin is GPIO, which stands for "General Purpose Input Output" pins. Every microcontroller has some of these pins. We can set them to either function as an input or an output pin. We use input pins to, for example, read out a temperature sensor or the state of a button. On the other hand, we use output pins to control motors, lights, speakers, and much more.

A GPIO pin is a digital pin, which means that it can either be in a high (1) or low (2) state. The state of the GPIO pin refers to the voltage that is present at the pin. For microcontrollers that are powered with 3.3V, most microcontrollers would define a low-state below a voltage of 1.2V, while they would define a high-state above a voltage of 1.8V. In-between those two values, the state of the pin couldn't be clearly identified, and is in some sort of gray zone. Every input pin has also an upper threshold, above which it would be permanently damaged. A standard upper threshold would be around 5V. 

#### Pull Ups / Pull Downs 
With a GPIO input pin, we could easily read out a button by attaching 3.3V to the button on one side and the input pin on the other side. The microcontroller measures the voltage at the pin, just as we do with the multimeter. If the button is pressed 3.3V are present. However, if it is not pressed the pin is not connected to any voltage level, which means the voltage level is undefined. We call this condition a floating pin. 

Floating pins are tricky, as their high/low state is not clearly defined. The slightest induction at the pin could change the voltage at the pin, and create a false high state. This could, for instance, happen if someone accidentally touches the pin. Therefore, we have to avoid pins is this state as much as possible. We have to define the off-state of the button, as low. Ideally the pin should measure a voltage of 0V or GND, while being off. 
To do so, we connect the pin to ground via a resistor. This is called a pull-down resistor, as it pulls down the voltage level of the input pin to ground. Now, the pin clearly measures 0V when turned on. 

But what happens when the pin is pressed? Well, now the 3.3V are connected to GND via the pull-down resistor. We can think of the button as having a very small resistance that is almost zero. The pull up resistor, on the other hand, has typical values from a few hundred Ohms all the way up to thousands Ohm. If we now calculate the equivalent resistance, it is approximately the same as the pull-down resistor. And if we divide the voltage of 3.3V by the pull-down resistor, we get the flowing current. Multiplying the flowing current with the two resistors results, in a voltage drop across the button of around 0V and across the pull-down resistor of around 3.3V. This means that the measured voltage at the pin is 3.3V. Through that, we have defined the pressed and unpressed state of the button effectively. 

We could create a similar logic by connecting the button to ground, and using a pull up resistor with which we would connect the input pin to 3.3V. The pull up resistor pulls up the voltage. If we now pressed the button the input logic level would be low. The equivalent resistance is again approximately the same as the pull up resistor, which results in a voltage drop of 3.3V across the pull-up and around zero across the button. Consequently, the input pin would measure a voltage of around 0V.  

#### Analog Input
Okay, so we are able to read out a button. But what if we wanted to determine the temperature in a room? 

For that we could use a temperature dependent resistor, which consists of a material that changes its resistance based on its temperature. First we have to create a voltage divider, that consists of one temperature dependent resistor, and one non dependent resistor. Then, we connect the divider to 3.3V and 0V. Through that, we can measure a changing voltage based on the temperature of the room. 

However, the GPIO input only determines if the voltage corresponds to a high and low states. So in our case the input pin would be low at certain temperatures, and high at other temperatures. If we wanted to know the exact temperature, we have to use another pin form - the analog input. 

This one uses an ADC (analog to digital converter), which measures the voltage at the pin. Analog signals have no discrete states and can take any values. They are not just Zero (Low) and 1 (High), but instead can be anything in-between. However, our microcontroller cannot do much with an analog signal as it based on a digital architecture. To make up for that, we have to use the ADC, which converts the analog signal to discrete states again. If we look at this input voltage chart at the analog pin, we can see that the temperature change is continuous. The ADC now assigns a numeric value to each voltage. An ADC comes also with a bit-rating, which tells us in how many steps a 3.3V voltage scale is divided. An ADC with a 12-bit resolution, would divide a 3.3V scale to a total of 2^12 steps (4096). So our microcontroller would interpret a voltage of 3.3V as 4095, and a a voltage of 0V as 0. If we now look at the converted chart, we can see that it isn't continuous anymore but jumps from one value to another. 

#### PWM
By putting a GPIO pin that is in the output state into a high state, we can easily turn on an LED. An LED is basically a diode that transmits light in the forward bias. The higher the voltage across it the more light will be emitted. This means that by varying the voltage, we could dim the LED. 
So, how would we do that we a microcontroller?

You could probably imagine that there is the inverse of a ADC - a DAC (digital to analog converter), and you are correct there is. However, most of the time microcontrollers do not use a DAC, but instead use a principle that is called pulse-width modulation (PWM).

It works similarly to our switching regulator that we discussed before. The microcontroller basically turns on and off the output pin at a high frequency. Again, a capacitor is used to smoothen, the square wave signal. And by varying the ratio of the on and off times, we can create a voltage that is between high and low. For example a one to one ratio would create a voltage of around 1.65V. The ratio between the active pulse time and the total time is called the duty cycle.

$D = \dfrac{PW}{T}$
PW ... active pulse time
T ... total pulse time 

A duty cycle of 100% would correspond to a voltage of 3.3V, while a duty cycle of 0% would correspond to 0V, and a duty cycle of 50% would correspond to a voltage of 1.65V. 


## Level 2 - Clock, Interrupts, and Sleep Modes

#### Clock Generator (Timer)
Remember the crystal oscillator? 
This is what creates the proper timing for most microcontrollers. 
The timing is necessary to create, for example, a proper PWM signal. The oscillator creates a constant sine wine that is translated into pulse signals for each cycle. For a PWM signal, a clock increments a number per cycle. The number of the clock is compared with a pre-defined number above which the output is high and below which the output is low. The clock counts further until it reaches its maximum number and then counts from zero again. By changing that pre-defined number, we can change the duty cycle of the PWM signal. 

However, this entire process only works, if each cycle takes a fixed amount of time. If the cycle duration were to change, we would not be able to achieve an accurate PWM signal. Similarly, we need a accurate timing for bus protocols with which we can communicate with other integrated circuits, and we couldn't time events (such as when to turn on a GPIO) properly. 

Most microcontrollers feature an internal clock. Further, they allow for adding an external oscillator for higher precision if needed. 

#### Clock Speed
A direct result of the chosen oscillator, is the clock speed. The clock speed is measured in Hertz, and gives the number of operations per second. Usually a microcontroller is equipped with a CPU multipliers which take the input of a crystal oscillator and multiples its signal by a certain factor to increase the number of operations per second. 

A high clock speed results in a high processing speed, as many operations can be held within one second. Most of today's microcontrollers have clock speeds of several MHz. However, the clock speed does only provide a rough idea of the performance of the microcontroller. If we compared the clock speed of two microcontrollers with different architectures, it could actually be that the one with the lower clock speed has a better performance. 

Often the same microcontroller can run at different clock speeds. A higher clock speed, would usually require more power, produce more heat, and bear a better performance. A lower clock speed, would be more power efficient, but slower. 

#### Interrupt and Sleep Modes
Let's assume we create a device with which we can measure the current temperature by pressing a button. We would probably read out the state of the button continuously. If it were pressed, we would read out the temperature through the ADC. 

Now, imagine we would make this device battery powered and hang it onto a wall as some form of thermostat. We probably only press the button once a day. However, the microcontroller would read out the state of the button several thousand times per second. This would take a lot of energy, and our device's power would probably only last a day or so. 

If we wanted to improve the power efficiency, the next two concepts can come in pretty handy - the interrupt and sleep states. 

We can put a microcontroller in a sleep modes, were it only draws nA compared to mA. Often, there are regular sleep states, and deep sleep modes. It sleep modes most of the microcontrollers functions are deactivated to save as much power as possible. 

To wake up the microcontroller we can use an interrupt. Typically a GPIO pin can be assigned to be an interrupt. If a certain logic level is present at the interrupt, the microcontroller stops whatever it is doing right now and conducts a so called ISR (interrupt service routine). In our case we would attach the button to the interrupt pin, and the interrupt service routine would be the reading of the temperature sensor and the wake up of the microcontroller. 

This means the microcontroller would be in deep-sleep until the button is pressed and triggers the interrupt. The interrupt wakes up the microcontroller, and reads out the temperature sensor. After that, the microcontroller would go back to sleep. 

Such a procedure would save tremendous power, and our device's power could suddenly last for months. 


## Level 3 - Bus Protocols
#### I2C
Microcontrollers communicate with another microcontroller, sensor, or laptop through bus systems and communication protocols. One of them is the inter-integrated circuit I2C bus. 
This bus system is used for integrated circuits to communicate with each other on the same PCB. 

Its a simple serial bus protocol that is easy to use, but doesn't allow for long distances or ultra high speeds. However, it is sufficient for most applications and many sensor come with this communication protocol built in. 

First, let's differentiate between a series bus protocol and a parallel bus protocol. In a series protocol, one information is transmitted at a time. You can think of it as the conveyer belt in a super marked. One product roles to the receiver at at time. A parallel bus protocol would be the same but with multiple conveyer belts operating at the same time. 
Therefore, a series bus system does not require many signal lines, while a parallel bus system does require many. At the same time, the parallel bus system is faster. 

I2C only consists of two wires: the SDA and the SCL line. 
SCL stands for serial clock line, while the SDA line stands for serial data line. 
Both lines are pulled up by a resistor to prevent the floating states described early. 

In this protocol there is always one master and one or more slaves. 
The master produces the serial clock line, and initiates the communication. 
The slaves listen to the serial data line, and receive the clock line.
The clock line is there to synchronize the timing of the different microcontrollers, as they might vary slightly per used crystals. 

Let's say we have a microcontroller to which two sensors are connected through I2C. Every component has its own 7bit I2C address. Now, let's look at what such a communication would look like.

The master continuously produces the timing on the serial clock line. Its frequency determines the speed of the transmission and there are different modes of operation. 100 kbits/s would correspond the standard I2C mode, while 400 kbit/s would correspond to the fast mode. There are even faster modes, but remember the faster the frequency the easier it is to smoothen the data curve. At very high frequency even a very small capacitor can do this, and if we have a smoothed signal no communication can occur. At fast enough frequencies even the capacitance of the wire itself can be enough to disrupt the communication. 

The master initiates the communication by sending a start bit and then writing the slave address with which it wants to communicate. All the slaves listen to the information the master provides. If they identify their own address they continue listing. Then the master sends another bit, which tells the slave if it wants to read or transmit information. If the master wants to read information, the slave then begins to transmit. On the other hand if the master indicated to transmit information, the slave will keep listening. 

This means that the master can only communicate with one sensor at the time. Because there are multiple addresses, we can add lots of sensors to the bus. 

#### SPI
The second bus that you will encounter often on microcontrollers is the serial peripheral interface (SPI) bus. This one is quite different from the I2C but is still a serial bus with a master and slaves. 

It consists of four wires: 
CS, SCK, MOSI, and MISO
CS stands for chip select 
SCK is the same as the SCL line and provides the slaves with the timing
MOSI stands for master out slave in
and MISO stands for master in slave out 

Every component is selected to the three lines SCK, MISO, and MOSI. Further, every sensor is connected to its own chip select pin. 

If the master wants to talk to a slave, it simply pulls down its CS line. Through that the master does not have to send addresses and the slaves do not have to listen for addresses. 
Another specialty of this protocol, is that the slave and the master can talk at the same time. The master provides information to the slave through the master out slave in line, while the slave provides the master with information through the master in slave out line. This is called fully-duplex mode which means that communication can held in both directions simultaneously.
All of these changes result in a more time efficient protocol. Additionally, its frequency can be in the several MHz spectrum.

All in all, the SPI bus requires four instead of just two connections from the master to the slave. However, this bus protocol is significantly more efficient and can transmit information way faster. 
For model rocket projects this speed is most often not required. However, it is sometimes still handy to use. 

#### UART
Finally, you will briefly learn about UART (universal asynchronous receiver transmitter).
This protocol is the standard for communication between microcontrollers and PCs. We use this protocol to program the microcontroller and to transmit live-information of the microcontroller to the PC. 

It also only consists of two lines - RX (receive) and TX (transmit). 
The RX line of the first device goes into the TX pin of the second device, and vice-versa. 
Unlike I2C and SPI, UART is designed for communication between only two devices.

UART does not use a clock line to synchronize the data transmission. Instead, both devices must agree on a common speed, known as the baud rate. Common baud rates include 9600, 115200, and others. Both devices must be configured to use the same baud rate for successful communication.

Obviously, there would be more information to add to describe UART, but for designing your own this rough understanding will be enough. 

## Level 4 - Memory Sources and Programming
Another aspect of microcontrollers are its memory sources. 
The three most essential ones are: Flash memory, RAM, and EEPROM.

Each of them usually serves a specific purpose. 
The flash memory is where the microcontroller firmware and program are stored. 
The EEPROM stores small amounts of information that last over many power cycles, such as configuration settings and calibration data.
Finally, the RAM memory is used for temporal data storage and manipulation while the microcontroller is running. For example to store variables and buffers. 
### Flash
Flash memory is a non-volatile memory, which means that the information is retained even after power is turned off. Each flash memory chip consists of several blocks, which are further divided into pages. These pages consist of multiple floating-gate MOSFETs that can store either a zero or a one. Flash memory is a type of electrically erasable and programmable read-only memory (EEPROM). As its name suggests, we can erase stored data, program new data, and read data. However, programming data is not possible for single bits; instead, we must erase and program entire blocks of the flash memory.

Flash memories have a limited life-cycle, meaning we cannot continuously erase and program data onto them indefinitely, as the floating-gate MOSFETs would degrade over time. This limited write/erase cycle is a crucial consideration for their use.

These characteristics define flash memory's use cases, such as storing firmware or software. These types of data do not require frequent erasing and programming, typically only a few hundred times at maximum over the device's lifetime.

### EEPROM
Even though the Flash memory is a type of EEPROM, it is common to treat Flash memories and EEPROMs as two distinct types of memory in microcontrollers as they both come with different use cases. 

Similarly to the Flash memory, the EEPROM is also non-volatile and doesn't loose information upon shut-down. The first difference is that each byte of the EEPROM is individually programmable and doesn't require the user to erase an entire block. The disadvantage of this individualistic access is a lower reading and writing speed, as well as a smaller memory density. However, EEPROMs come with the additional advantage of enduring more erase/program cycles. 

Out of those characteristics, it makes sense that the EEPROM is used to store data that must remain on the device after power-down but will be changed often. Examples for that would be the storage of configurations settings, user preferences, and calibration data. 

### RAM
The last type of memory that we will discuss is the random access memory or RAM. Compared to the other two memory sources it is volatile, which means that its data is lost after power down. RAM is called "random access" because any memory location can be accessed directly, regardless of its location in the memory hierarchy. Its smallest units are either capacitors (Dynamic RAM) or flip-flops (Static RAM). These components allow for even faster read/write speeds than floating-gate MOSFETs. 

Due to the very fast read/write speeds and the fact that its data storage is only temporary, the RAM's use cases are to provide the central processing unit (CPU) with data that it needs to quickly access while program execution. 

### Programming
Programming a microcontroller typically involves a bootloader, which is a small program pre-installed in the microcontroller's memory. When the microcontroller is powered on, it first runs the bootloader. During this limited time, the bootloader waits for communication from the PC. The PC can signal to the bootloader that it wants to upload new code, a process often done via UART. 

If the PC sends a request to upload code, the bootloader receives the new program data and writes it to the appropriate memory location in the microcontroller. The bootloader ensures that the new program is correctly received and stored. 

If no new code is uploaded during the bootloader period, the microcontroller proceeds to execute the previously stored program. This fallback mechanism means that if the bootloader does not receive a communication signal from the PC within the specified time window, it defaults to running the existing program in memory.

During a limited time after power-up, the bootloader waits for communication from the PC. If new code is uploaded, it replaces the existing program; otherwise, the microcontroller executes the current program in memory. This process allows for easy updates and reprogramming of the microcontroller.

### Summary
A microcontroller is a mini-computer that integrates all necessary components, such as memory, a processor, and peripherals, into a single package, typically powered by 3.3V. It features GPIO (general-purpose input and output) pins. When set as input, they read the voltage to determine whether it corresponds to a digital high (>1.8V) or a digital low (<1.2V). When set as output, they can either be high (3.3V) or low (0V).

To read a value between high and low, an analog input pin is used. This pin measures the voltage like a multimeter and translates the value into a numeric number via an ADC (analog-to-digital converter).

For outputting a voltage between high and low, pulse width modulation (PWM) is used. In PWM, the output pin is turned on and off repetitively. The ratio between the on-time and the total time is called the duty cycle. A capacitor can be used to smooth out the resulting voltage.

Every microcontroller has an internal or external clock that times all operations, such as PWM signals, timing, and communication protocols. The speed at which the oscillator runs, combined with the CPU multiplier, determines the microcontroller's clock speed, which gives a rough idea of its performance.

Input pins can also be used as interrupts. Interrupts disrupt the microcontroller's current program execution to run an interrupt service routine (ISR). They are useful for waking up a microcontroller from low-power sleep modes.

Microcontrollers communicate with other devices through various protocols. I2C (Inter-Integrated Circuit) uses two wires: SCL (serial clock line) and SDA (serial data line). It features a master and one or more slaves. The master addresses the slave it wants to communicate with and provides the clock signal. I2C is a relatively slow but easy-to-use protocol, often implemented in sensors.

SPI (Serial Peripheral Interface) requires four wires: SCK (serial clock), CS (chip select), MOSI (master out slave in), and MISO (master in slave out). SPI allows full-duplex communication, enabling both the master and the slave to communicate simultaneously without the need for address transmission.

UART (Universal Asynchronous Receiver Transmitter) is another communication protocol used for serial communication between two devices, typically a microcontroller and a PC. It uses two lines: RX (receive) and TX (transmit), and operates at a predefined baud rate. UART is straightforward but limited to point-to-point communication without a master-slave hierarchy.

PCs upload code to the microcontroller via the UART protocol. Upon power-up, the bootloader waits for a limited time for communication from the PC. The bootloader mechanism ensures that new code can be uploaded to the microcontroller efficiently and reliably. If new code is uploaded, it replaces the existing program; otherwise, the microcontroller runs the current program in memory.
### Examples
Input - Button + Pull-down 
Input - Temperature measurement + ADC
Output - LED + diming LED (oscilloscope)
Temperature Measuring Device with Button - with Interrupt 

## Level 5 - Specific Microcontrollers
### Lecture
Now, with all the microcontroller basics out of the way, let's look at three specific microcontroller examples. But before we do so, let's talk about breakout boards and on-PCB design.
#### Breakout vs Embedded Microcontroller
We can implement a microcontroller into our flight computer in one of three ways. 

The first way would be to use a third-party breakout board. Breakout boards are ready to use microcontrollers, where all the necessary components are already pre installed. The breakout board most often features a voltage regulator which provides the exact 3.3V needed, has an integrated crystal oscillator which provides the microcontroller with accurate timing, and incorporates a chip (a USB to UART bridge) for proper communication between the PC and microcontroller. Further, it features a pin header for easy access of the microcontroller pins and has the bootloader pre-installed. 
This implementation is easiest, as those breakout boards can be used out of the box. An Arduino Uno, an ESP32 Dev Module, or a Teensy, would all be examples of such breakout boards. The processor that they incorporate are from different companies. An Arduino Uno, for example, features an ATMEGA16 microcontroller. The disadvantage is the increased weight, as we have an additional PCB, and pin rows. Further, it is not as reliable as the connection between the pins could be error prone. However, it is very beginner friendly, and if we came to just damage the microcontroller it could be replaced more easily. 

The second way would be by using a so called module. A famous example is the ESP32-Wroom module, which we will look at. This module can be directly implemented on our own PCB and spares as a few steps compared with a full microcontroller implementation. Such a module internally features a crystal for timing, has a pre-installed bootloader, has extra FLASH memory, and a Bluetooth antenna. In this case we only have to be concerned with the USB to UART bridge, for programming, and the power management of the microcontroller. 

The final way would be an onto the PCB embedded microcontroller. In this case we have to do all the implementation ourselves. We have to select a proper crystal, have to establish the USB to UART bridge, provide proper power management, and sometimes have to install the Bootloader. Additional functionalities like Bluetooth and WIFI, must also be implemented by us, which requires antenna design and RF matching. We will look at this kind of implementation by using an STM32 microcontroller. This method allows us to adjust our design to our needs to the maximum degree, and results in the most lightweight PCBs, as we can decide which features we want to incorporate and which we want to exclude. 

## Level 6 - Teensy 4.1
A famous breakout board line of microcontrollers are the Teensys from PJRC. 
They are known for their fast processing speeds, and are compatibility with the Arduino IDE, an easy to use programming environment for microcontrollers.

Let's specifically look at their Teensy 4.1, which is their newest microcontroller and a powerhouse for flight computers. 

The Teensy 4.1 incorporates a Cortex-M7 microcontroller, which runs at a clock speed of 600MHz. With the processing power this microcontroller provides, you can achieve almost any goal in model rocketry. It run our program over a thousand times per second, and is the fastest of all microcontrollers we will discuss here. 
Regarding peripherals it is an outstanding option. If we look at the pinout, we can see that there are countless (55) GPIO pins, a lot of PWM pins (32), and 18 analog input pins. Further, there are several bus interfaces, such as 3 I2C, 3 SPI, and 8 UART. The Teensy 4.1 almost certainly has the pin you will need. 

What is also special, is that the Teensy 4.1 already implements an on-board SD card to which we can store flight data. An SD card is actually nothing more than a Flash memory with a specific form factor. 

If the SD card storage or the internal Flash or RAM of the Teensy 4.1 aren't enough, we can add up to two QSPI Flash memory chips or two 8MB PSRAM chips to the bottom of the board.

QSPI stands for quad serial peripheral interface, and is an advanced form of SPI, which we discussed previously. It has four (quad) data lines, which enables way higher transfer speed, which allows for several times faster reading/writing speeds. 

PSRAM. Is a pseudo-static RAM. We can use an additional chip like this to outsource large variable arrays to this temporal storage to be able to quickly process data in real-time applications. This could be beneficial, for example, to process camera information. 

The Teensy 4.1 is an outstanding option if you are looking for a microcontroller with outstanding processing speed, countless GPIO pins, and an easy project integration. 

##### Implementation
To implement a breakout board microcontroller in your project not much is required. The only thing you have to provide is the power supply. Often, like in the case of the Teensy 4.1, these boards even feature their own voltage regulator on board. In the case of the microcontroller we could provide input voltage from 3.3 - 5V. So, by simply connecting VIN to 5V and GND ports to GND, the microcontroller can be up and running. 

Now, the only task left to do, is to connect our sensors and outputs to the appropriate pins of the microcontroller. Here, a pin out can be highly useful, which indicates what can be used for which purposes. Let's look at it pinout, then we can see that we can use pin 1 for PWM control, as well as the transmitter for the UART protocol, indicated by TX1. Pin 12, could be used to as one of the SPI pins (the MISO pin) or again as a PWM pin. All pins in this pinout can be used as regular GPIO pins. 

## Level 7 - ESP32
An example of microcontroller modules are the ESP32-WROOM line of modules. Specifically, we will be looking at the ESP32-WROOM32E-N8. 

An ESP32-WROOM module incorporates a 40MHz crystal oscillator, an QSPI Flash memory chip, and RF matching circuits. They are known for their Bluetooth and WIFI capabilities, which they incorporate inside the enclosure, and are also programmable using the Arduino IDE. 

In the WROOM line of ESP32 microcontroller there are different build forms, which are indicated by the letter after the WROOM32. The main difference in build forms is that there are modules that already incorporate the antenna (E) and ones that incorporate a UFL connector to which a antenna must be connected (UE). The -N8 at the end suggests how large the incorporated QSPI Flash memory is, in our case 8MB. Further there are module variants that indicate -N8R2, which suggests the same flash memory size and an additional PSRAM of 2MB. 

This ESP32 variant has two CPUs that can both run at up to 240MHz. Additionally, it features a low-power co-processor that can be used for trivial tasks. 

The used microcontroller inside the module would feature 48 GPIO pins. However, only 25 are broken out to the module. All of them can be used as PWM pins.  It features 15 12-bit resolution ADC analog input pins and it even features 2 analog output channels to create real analog voltages with the help of a 8-bit DAC. 

It has 2 UART, 3 SPI, 1 I2C, and 3 special I2S buses. I2S is similar to I2C and stands for inter integrated sound. Those bus systems are very useful to control chips for stereo sound or microphone inputs. 

The ESP32 WROOM modules, are perfect for projects in which we require easy connectivity, such as Bluetooth or WIFI. They are a little bit more difficult to implement than a breakout board microcontroller, but still rather seamless to integrate. They feature a descent amount of GPIO pins and processing power, and excel at projects with low power consumption. Their sleep currents can be less than 5uA. 

To use ESP32 WROOM modules, we have to provide them with power, and we have to establish the connection between the microcontroller and our programming device. 

##### USB to UART bridge
Now we have ask how a computer communicate can communicate with our microcontroller. 
You are for sure familiar with USB, and you might think of it as solely being the connector. 
However, USB actually stands for "Universal Serial Bus", which clarifies that USB is also the communication protocol with which our laptops and PCs communicate with their devices, such as keyboards, mouses, and much more. 

The USB bus additionally provides the devices with power. It consists of a host (our PC) and multiple peripheral slaves (our devices). It can communicate at very high speeds, depending on the used protocol. USB 3.1, for example, can reach transfer speeds of up to 10 Gbps (gigabits per second). Further, it is very complex protocol, able to do multiple transfer modes, and device enumeration. Their connectors a standardized, and common ones are: USB-C, micro-USB, and USB type A. 

Now, let's recall the UART (universal asynchronous transmitter receiver) protocol.
As we discussed previously, it is one of the protocols with which our microcontroller communicates. It's speed is given by the Baud rate, where common values are 9600-115200 (bits per second), magnitudes less than the speed of the USB protocol. The UART protocol is only intended for communication between two devices, without a master/slave system. 

Okay, so a computer commonly communicates by USB, while a microcontroller communicates with the UART protocol. While both are serial protocols, we have seen that they differ in significant ways, which explains why we need a device that translates between USB and UART. 

For us to upload code from a PC to a microcontroller. We, therefore, need a USB to UART bridge. 
Two famous ones are the CP2102 and the CH340. 

The CP2102 is the more expensive one. It emulates a USB device, which is immediately recognized by the PC as soon as we connect to it. To upload code through this bridge, we do not have to install any drivers or what so ever, and it simply works out of the box. 

A CH340, on the other hand, is cheaper, but needs a driver in order for the PC to recognize the device. 

##### Implementation 
Implementing a microcontroller module like the ESP32 is a little trickier than implementing a breakout board. Yet, it is still relatively easy to do. 

We have to again provide power to the VDD pins. However, this time we have to provide a regulated voltage of 3.3V. 

We also have to provide the RESET and BOOT functionalities manually. The RESET pin is needed to be able to restart the program, while the microcontroller is stilled provided with power. If the RESET (Enable) pin is pulled high, the microcontroller is in normal operation, while if it is pulled low the microcontroller is resetting. We connect this reset pin to 3.3V by a pull-up resistor and to a button that can connect the EN pin to ground when needed. As buttons tend to bounce when pressed, which is an unintended oscillation of a button's electrical contacts. Consequently, we also add a capacitor in parallel that filters these spikes that are inconvenient for the microcontroller. 

The ESP32 will enter the serial bootloader when GPIO0 is held low on reset. Remember the bootloader is the part of the program the microcontroller can enter after start up, which allows us to connect to the microcontroller in order to program it. Therefore, we also connect a button the BOOT pin to ground, and add a capacitor to prevent button bouncing. If the button is not pressed the microcontroller will simply run the program that is currently on the flash, and if it is pressed we have a small time window in which we can program the device.

Further, we have to implement a USB to UART bridge, which we connect to the TXD0 and RXD0 pins of the microcontroller. 

Here, we used the CH340, which is a little bit more straightforward to implement than the CP2102. For both we have to first look at their datasheet, and their connection diagrams. We connect the UART pins of the microcontroller to one side of the IC, while we connect the data pins of the USB port to other pins of the IC. We also have to provide the IC with regulated 3.3V power, and some filtering capacitors as indicated in the datasheet. We also connect the USB port to VUSB, as we can take the 5V of the USB line to power the board when connected.

There are two more pins the RTS and DTR which we connected to the USB-TO-UART bridge. 
These are essential to indicate to the microcontroller that we automatically want to reset and boot the microcontroller to upload code. The PC basically communicates to the USB-TO-UART bridge that we want to upload code now, and by a special transistor circuit these two signals trigger the RESET and the BOOT pins accordingly. The transistor schematic behind it takes to much time to understand in this lecture's context. Just remember that this circuit exists and that you should implement it as soon as you want auto-programming functionality for your flight computer by just one click in your programming environment. 

## Level 8 - STM32
The final type of microcontroller implementation is that of plain microcontrollers. Two famous lines of microcontroller are the ATMEGA and the STM32 lines. The ATMEGA microcontrollers are commonly implemented in Arduino boards, while the STM32 microcontrollers are heavily used in the industry. Here we will describe the STM32 line of microcontrollers. 

There are hundreds of different STM32 chips available, which makes this line of microcontrollers special. There is almost certainly the perfect STM32 microcontroller for every project out there. There are Bluetooth and WIFI variants, variants with numerous GPIO pins, as well as low power and and high speed versions. 

The amount of options makes the use of those microcontrollers highly saleable. Further, they are known for their robustness, and can be used in critical applications. 

Let's look at a specific version of the STM32 the: 
STM32F722RET6
The naming might be rather confusing, but there a scheme behind the naming that is true for all the STM32s. If we want to work with these microcontroller it can be highly useful to become familiar with their naming conventions. 

- F7: indicates the used processor. All STM32s use Cortex-M processors. The F stands for the line of STM32. Where F is either a foundation or a high performance variant, G would stand for a mainstream variant, L stands for a low-power version, and H stands for a high performance variant. The 7 stands for a Cortex-M7 processor, which is the highest performance core there is on Cortex processors. This one has a clock speed of 216MHz. 
- The next two digits indicate the microcontroller line. 
- The following R stands for the number of pins this microcontroller breaks out. R corresponds to 64 or 66 pins. The one with the least pins is F with only 20 pins and the one with the most is I with 176 pins.
- The next number or letter: E stands for the flash memory size. In our case E stands for 512Kbytes. You may think that 512Kybtes is very little memory compared to the 8MBytes the ESP32 uses. However, we program the STM32 line with their own tool, which allows to save tremendous amounts of storage. In our case the 512Kbytes where more than enough. 
- The next one stands for the package of the microcontroller. T stands for LQFP. The package is basically the form factor of the chip. There are variants were the pins are at the bottom of the chip an inaccessible, while there are versions with broken out pins like LQFP. 
- And last there is the temperature range at which the chip is functional. 6 indicates a range of -40 to +85°C. 

The meaning behind all the numbers can be looked up at DigiKey: 
https://www.digikey.at/de/maker/tutorials/2020/understanding-stm32-naming-conventions?utm_adgroup=STMicroelectronics&utm_source=google&utm_medium=cpc&utm_campaign=Dynamic%20Search_EN_Supplier&utm_term=&productid=&utm_content=STMicroelectronics&utm_id=go_cmp-9415055229_adg-98040915040_ad-668047754589_dsa-459571002621_dev-c_ext-_prd-_sig-Cj0KCQjwpNuyBhCuARIsANJqL9NuQjvpgdRDj_jcrQFeAt_oQAfYkwKz_4l5YTTlH_azxBfwnVOBTP0aAnACEALw_wcB&gad_source=1&gclid=Cj0KCQjwpNuyBhCuARIsANJqL9NuQjvpgdRDj_jcrQFeAt_oQAfYkwKz_4l5YTTlH_azxBfwnVOBTP0aAnACEALw_wcB

The implementation of an STM32 based microcontroller is still a little bit more advanced then the two have looked at before. 
To see how its done, let's devise the implementation of the STM32F722RET6 we discussed previously. 

##### Power Management
On this IC there are a few more pins which we have to provide with power. We can look up how exactly the power supply should look like by viewing the hardware development guide that ST provides for all there STM microcontrollers. For this one we have to look at the STM32F7 AN4661. 

First of all there are the standard VDD pins for the digital logic of the IC. We have to provide those pins with a voltage of 3.3V and a capacitor of 100nF per pin each, which will vary by package. Additionally, we should add a 4.7uF bulk capacitor for the VDD voltage line. 

The voltage supply for the analog VDDA pins, needs special treatment to improve the ADC's stability and accuracy. To do so the 3.3VDD is implemented on one side with a 1uF capacitor and the 3.3VDDA voltage is implemented with a 1uF and a 10nF capacitors. The two circuits are connected by a ferrite bead, of which you probably didn't yet here about. Ferrite beads are specialized inductors used primarily for filtering high-frequency noise in electronic circuits. A ferrite bead is used in this case to electrically separate the two supply voltages, and to make the analog voltage cleaner.

The next voltage pin we must look at is the VCAP1 pin. This pin is needed for the internal voltage regulator that creates an even stabler voltage for the internal components of the IC. On other STM32F7 this internal regulator could be bypassed. However, on this particular one the regulator is always enabled. To ensure proper functioning of the regulator, we have to provide the controller with a capacitor on the VCAP1 pin. It is important to pay attention to the ESR (equivalent serial resistance) value of the capacitor in this case to only be between 0.1 and 0.2 Ohms!
The voltage regulator creates a voltage of 1.2V, which should be measurable on the VCAP pin.
To do the job, I selected two 0402 Samsung 4.7uF capacitors (CL05A475MP5NRNC) that show a proper ESR characteristic in their datasheet that I found on Mouser.

The final pin of the power supply VBAT is not used in our case. It would be in case we wanted to keep real-time clock measurements, such as time of day, day, or month, etc. In this case we would connect a cell button cell that continuously supplies the microcontroller with power. In our case it is not used. In this case, it is recommended to connect it to the standard 3.3VDD line. 

##### Serial Wire Debug (SWD)
To program an STM32, we do not have to provide the USB to UART bridge ourselves. Instead, there are programming devices, such as the ST-Link V2, which allow us to program any STM32. The programmer connects to the microcontroller by either JTAG or serial wire debug (SWD) and to the PC by USB. 

JTAG has a total of 20 pins, while SWD uses only four. As we want to minimize weight and PCB real-estate in flight computer design, we will be using the SWD interface which consists of the following four pins: 

- **SWDIO (Serial Wire Debug Data Input/Output):** This is the bidirectional data line used for communication between the debugger and the target microcontroller.
- **SWCLK (Serial Wire Debug Clock):** This is the clock line used to synchronize the data communication.
- 3.3V 
- and GND. 

SWD supports full debugging capabilities, including setting breakpoints, stepping through code, inspecting variables, and modifying memory. It also allows for programming the Flash memory of the microcontroller.

##### Configuration Pins
Similarly to the ESP32, we also have to provide the STM32 with information whether it shall reset, or whether it shall enter the bootloader upon power up. 

The NRST pin corresponds to the reset pin in this scenario. The reset happens when this pin is connected to GND. In normal operation it can either be left floating or pulled-up to 3.3V through a pull-up resistor. (Though, the pin is already pulled high internally). Often a capacitor is added between the NRST pin and GND to add EMS (electromagnetic susceptibility) protection and avoid parasitic resets. When using the SWD interface, a program reset via the NRST pin is not actually necessary, since SWD bypasses the bootloader and can reset and flash the MCU directly.

There's also a BOOT pin on the STM32. However, when programming via the SWD interface the bootloader can be bypassed and does not have to be accessed in this way. Yet, if I would want to flash the chip via USB through a USB-TO-UART bridge, I would have to pull BOOT0 high after a reset to enter the internal bootloader. Which internal bootloader (RAM vs system memory) is used depends on the state of BOOT1 on other MCUs, and is configured through software on the F7 series, as the BOOT1 pin is not implemented here. To keep our options open, I recommend to use a tactical switch on the BOOT0 pin that would pull it high with a pull-down resistor that normally pulls BOOT0 low. 

##### Oscillator Design 
Something we also didn't yet have to provide for the microcontroller is the clock source. The clock source for the STM32F7 must fall between 4-26MHz in order for the microcontroller to function. To make a proper oscillator, we also have to attach two capacitors, which are called load capacitors. Load capacitors are capacitors connected to the terminals of a crystal oscillator. They form part of the resonant circuit that determines the oscillator’s frequency. The correct selection of load capacitors is essential for stable and accurate frequency operation.

Let's select a 12MHz crystal which falls between the stated frequency range in the datasheet. The selected crystal also states the external load capacitance it would like to see, which in this case was given by 20pF. 

Now, there is a rough estimation formula with which we can determine the capacitances of the two capacitors in order for the circuit to work:

$C = 2*(C_{load} - C_{stray})$

The stray capacitance gives the unwanted capacitance of a circuit, and depends the PCB layout and the input capacitance of the oscillator pins.
For most designs it roughly falls between:
$C_{stray} = 3 - 5pF$  

When now assuming a stray capacitance of 5pF and by inserting in the formula above we get a value of 30pF for the capacitors that we shall implement. Now we have to chose the next highest available capacitor size which would be 33pF.

Just like that our oscillator design, provides our microcontroller with periodic timing information on which it can base its bus protocols, PWM signals and more. 
##### STM32 CubeIDE MX
To set up and program the STM32, we don't use the Arduino IDE, but instead use their provided software STM32 CubeIDE. Within this tool, we can write our code, upload the code to our microcontroller by connecting it through a ST-Link, and are able to debug our code live. 

There is a CubeIDE MX tool inside the environment that allows us to set up the pins and the used clock during the development process. It graphically shows us which pin function we can assign to which pin, and makes as aware of any conflicts. 

So, as you have seen the STM32 line of microcontrollers is very different to the ones we discussed before. They have to be implemented in a very different way, are programed in a different environment, and can be debugged. There is variants for almost any application and they are very robust.  

#### Summary
If you strive for the fastest processing speed, countless GPIO pins, bus functionalities, and easy implementation, as well as an onboard SD card, a good starting point for your design would be the Teensy 4.1. The option is a good start for any beginner and is definitely sufficient for a great flight computer design.

If you want to make a more advanced PCB design, you can implement a microcontroller module. The ESP32-WROOM seamlessly incorporates connectivity, such as Bluetooth and WIFI, and excels in low-power situations. It is not as fast as the Teensy 4.1, but fast enough for most flight computer designs. Further, it is more difficult to implement than a breakout board, as you additionally need to implement a USB-to-UART bridge. Still, it is relatively easy to do. 

The last option, is to implement bare-bone microcontrollers. This option is for the advanced of you that want to familiarize themselves to microcontrollers that are used in the industry. The STM32 line offers and option for almost any application, provides fast processing speeds, countless GPIO pins, and many bus protocols. They are programmed in their own environment, upload code through their own ST-Link programmers, and allow for real-time debugging. For making them work, we have to design the oscillator circuit ourselves and have to incorporate the programming interface. 

We will look at how we implement any of those three designs after we learned about the PCB design environment. 