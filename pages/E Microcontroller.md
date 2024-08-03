---
layout: page
title: Flight
permalink: flight
---
## This path is work in progress!
The material that we provide in the following levels is by now means complete but it might help you to learn about the subject yourself, while we are working on providing content for you! 

## Level 1 - Pin Types
<iframe width="560" height="315" src="https://www.youtube.com/embed/OMudnSCSlkE?si=Jsw0YBReucYpIBM8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
A microcontroller can be thought of as a mini computer. Unlike a traditional computer, a microcontroller integrates all the essential components into a single package, including the processing core, program memory, and input/output peripherals.

In the following levels, you will acquire knowledge of microcontroller basics. We will cover various topics, such as the different types of pins, the microcontroller clock, sleep modes, bus protocols, memory sources, and programming interfaces. At the end of this section, we will examine three specific microcontrollers and their implementations into a flight computer design. We will take a look at: the Teensy 4.1, a breakout board; the ESP32, a microcontroller module, and the STM32, a plain microcontroller.

In this first level, we will explore the input/output peripherals of a microcontroller, the so-called pins.

#### Power
For a microcontroller to function, it has to be provided with power. Most microcontrollers use a 3.3V input voltage, and feature several pins to which we will have to provide power to. 

#### GPIO Pins
The first term we have to coin is GPIO, which stands for "General Purpose Input Output" pins. Every microcontroller has some of these pins. A GPIO pin can either function as an input or an output pin. We use input pins to, for example, read out the state of a button. On the other hand, we use output pins to, for example, control LEDs or pyro channels.

A GPIO pin is a digital pin, meaning it can either be in a high or low state. The state of the GPIO pin refers to the voltage present at the pin. For microcontrollers powered with 3.3V, most microcontrollers would define a low state below a voltage of 1.2V, while they would define a high state above a voltage of 1.8V. In between those two values, the state of the pin couldn't be identified and is in some sort of gray zone. Every input pin has an upper threshold above which it would be permanently damaged. A standard upper threshold 3.3V microcontroller would be around 5V. 

So, if we were to set an output pin to high, we would measure a voltage of 3.3V, while if we set the pin to low, we would measure 0V. 

If a voltage greater than 1.8V is applied to an input pin, the microcontroller will interpret this as a high state and return a 1. If a voltage below 1.2V is applied, it will be interpreted as a low state, returning a 0.

#### Pull Ups / Pull Downs 
With a GPIO input pin, we could easily read out a button by attaching 3.3V to the button on one side and the input pin on the other. The microcontroller measures the voltage at the pin just as we do with the multimeter. If we press the button, the input pin reads 3.3V. However, if the button is not pressed, the pin is not connected to any voltage level, which means the voltage level is undefined. We call this condition a floating pin. 

Floating pins are tricky, as their high/low state isn't clearly defined. The slightest induction at the pin could change the voltage at the pin and create a false high state. This induction could, for instance, happen if someone accidentally touches the pin. We have to avoid floating pins as much as possible. To do so, we have to define the off-state of the button. Ideally, the pin should measure a voltage of 0V or GND while off. 
To do so, we connect the pin to GND via a resistor. We call this resistor a pull-down resistor, as it pulls down the voltage level of the input pin to GND. Now, the pin measures 0V when the switch isn't pressed.

But what happens when we press the button? Well, now the 3.3V is connected to GND via the pull-down resistor. We can think of the button as having a very small resistance. On the other hand, the pull-down resistor has typical values from a few hundred Ohms up to thousands of Ohms. If we now calculate the equivalent resistance, it is approximately the same as the pull-down resistor. And if we divide the voltage of 3.3V by the pull-down resistor, we get the flowing current. Multiplying the flowing current with the two resistors results in a voltage drop across the button of around 0V and across the pull-down resistor of around 3.3V. Therefore, the measured voltage at the pin is 3.3V. Through that, we have defined the pressed and unpressed state of the button effectively. 

We could create a similar logic by connecting the button to GND and using a pull-up resistor to connect the input pin to 3.3V. The pull-up resistor pulls up the voltage. If we now press the button, the input logic level would be low. The equivalent resistance is again approximately the same as the pull-up resistor, which results in a voltage drop of 3.3V across the pull-up and around zero across the button. Consequently, the input pin would measure a voltage of around 0V.  

#### Analog Input
Okay, so we can read out a button. But what if we wanted to determine the temperature in a room? 

For that, we could use a temperature-dependent resistor, which consists of a material that changes its resistance based on its temperature. First, we have to create a voltage divider that consists of one temperature-dependent resistor and one non-dependent resistor. Then, we connect the divider to 3.3V and 0V. Through that, we can measure a changing voltage based on the room temperature. 

However, the GPIO input only determines if the voltage corresponds to a high and low state. So, in our case, the input pin would be low at certain temperatures and high at others. If we wanted to know the exact temperature, we had to use another pin form - the analog input. 

An analog input measures the voltage in an analog way and then translates this analog information into digital information using an ADC (analog-to-digital converter). Analog signals have no discrete states and can take any value. They are not just 0 (Low) and 1 (High); instead, they can be anything in between. However, our microcontroller, being based on a digital architecture, cannot directly process an analog signal. To address this, we use the ADC to convert the analog signal into discrete states.

Consider an input voltage chart at the analog pin that shows a continuous temperature change. The ADC assigns a numeric value to each voltage level. The ADC also has a bit rating, which indicates the number of steps into which a 3.3V voltage scale is divided. An ADC with a 12-bit resolution divides a 3.3V scale into 2^12 steps (4096 steps). Therefore, the microcontroller would interpret a voltage of 3.3V as 4095 and a voltage of 0V as 0. If we look at the converted chart, we can see that it is no longer continuous but jumps from one value to another.

#### PWM
We can seamlessly turn on an LED with a microcontroller by putting a GPIO output to high. An LED is a diode that transmits light in forward bias. The higher the voltage across, the more light it will emit, which means that by varying the voltage, we could dim the LED. 
So, how would we do that with a microcontroller?

You could probably imagine that there is the inverse of an ADC - a DAC (digital to analog converter), and you are correct that there is. However, most of the time, microcontrollers don't use a DAC but instead use a principle that is called pulse-width modulation (PWM).

It works similarly to the switching regulator that we discussed before. The microcontroller turns on and off the output pin at a high frequency. Again, a capacitor is used to smoothen the square wave signal. By varying the ratio of the on and off times, we can create a voltage that is between high and low. For example, a one-to-one ratio would create a voltage of around 1.65V. The ratio between the active pulse time and the total time is called the duty cycle.

$D = \dfrac{PW}{T}$
PW ... active pulse time
T ... total pulse time 

A duty cycle of 100% would correspond to a voltage of 3.3V, a duty cycle of 0% would correspond to 0V, and a duty cycle of 50% would correspond to a voltage of 1.65V. 

#### Summary
So, in summary: 
A microcontroller is a mini-computer that integrates all necessary components, such as memory, a processor, and peripherals, into a single package, typically powered by 3.3V. It features GPIO (general-purpose input and output) pins. When set as input, they read the voltage to determine whether it corresponds to a digital high (>1.8V) or a digital low (<1.2V). When set as output, they can either be high (3.3V) or low (0V).

To avoid floating pins and ensure a defined voltage level when an input pin is not actively driven, pull-up and pull-down resistors are used. A pull-up resistor connects the input pin to a high voltage (3.3V), ensuring the pin reads high when the switch is open. Conversely, a pull-down resistor connects the input pin to ground (0V), ensuring the pin reads low when the switch is open.

To read a value between high and low, an analog input pin is used. This pin measures the voltage like a multimeter and translates the value into a numeric number via an ADC (analog-to-digital converter).

For outputting a voltage between high and low, pulse width modulation (PWM) is used. In PWM, the output pin is turned on and off repetitively. The ratio between the on-time and the total time is called the duty cycle. A capacitor can be used to smooth out the resulting voltage.

In addition to GPIO, microcontrollers also include pins dedicated to bus protocols such as UART, SPI, and I2C. These protocols enable communication with other devices and components. We will learn more about them in a later level. 

## Level 2 - Clock, Interrupts, and Sleep Modes
<iframe width="560" height="315" src="https://www.youtube.com/embed/GilS7-x-UNs?si=A5niDhqOWnQ4INPz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
In this level, we delve into crucial aspects of microcontroller functionality: clock generation for precise timing, interrupts for responsive operation, and sleep modes for efficient power management. These elements are pivotal in embedded system design, influencing timing accuracy, system responsiveness, and overall energy efficiency.

#### Clock Generator (Timer)
Remember the crystal oscillator? 
The crystal is how we can create a proper timing signal for microcontrollers. 
Proper timing is necessary to create, for example, a PWM signal. The oscillator creates a constant sine wave, which is translated into pulse signals for each cycle. For a PWM signal, a clock increments a number per cycle. The number of the clock is compared with a pre-defined number above which the output is high and below which the output is low. The clock counts further until it reaches its maximum number and then counts from zero again. By changing that pre-defined number, we can change the duty cycle of the PWM signal. 

However, this entire process only works if each cycle takes a fixed amount of time. If the cycle duration were to change, we would not be able to achieve an accurate PWM signal. Similarly, we need precise timing for bus protocols to communicate with other integrated circuits, and we can't time events (such as when to turn on a GPIO). 

Most microcontrollers feature an internal clock. However, those internal clocks are often inaccurate. Therefore, they allow for adding an external oscillator for higher precision.

#### Clock Speed
A direct result of the chosen oscillator is the clock speed. The clock speed is measured in Hertz and gives the number of operations per second. Usually, a microcontroller is equipped with CPU multipliers, which take the input of a crystal oscillator and multiply its signal by a factor to increase the number of operations per second. 

A higher clock speed results in a higher processing speed, as more operations can be conducted within a second. Most of today's microcontrollers have clock speeds of several MHz. However, the clock speed does only provide a rough idea of the microcontroller's performance. If we compared the clock speed of two microcontrollers with different architectures, it could be that the one with the lower clock speed has a better performance. 

Often, the same microcontroller can run at different clock speeds. A higher clock speed would require more power, produce more heat, and bear a better performance. A lower clock speed would be more power efficient but slower. 

We must select the crystal oscillator according to the microcontroller's specified clock speed. Using a crystal oscillator with a frequency significantly higher than the microcontroller's rated speed could lead to improper operation and must be avoided.

#### Interrupt and Sleep Modes
Okay, now let's learn about interrupts and sleep modes. 
Let's assume we create a device that can measure the present temperature by pressing a button. As of our current understanding, we would probably continuously read out the state of the button. If we press the button, the microcontroller will read the temperature through the ADC. 

Imagine we would make this device battery-powered and hang it on a wall as a thermostat. We probably only press the button once a day. However, the microcontroller would read out the state of the button several thousand times per second. Consequently, our microcontroller would require a lot of energy, and our device's power would probably only last a day. 

If we wanted to improve the power efficiency, the next two concepts come in handy - the interrupt and sleep states. 

We can put a microcontroller in sleep mode in which it only draws nA compared to mA. Often, there are regular sleep states and deep sleep modes. In those modes, most microcontroller functions are deactivated to save as much power as possible. 

To wake up the microcontroller, we can use an interrupt. Typically, a GPIO pin can be assigned to be an interrupt. If a logic level is present at the interrupt, the microcontroller stops whatever it is doing and conducts a so-called ISR (interrupt service routine). In our case, we would attach the button to the interrupt pin, and the interrupt service routine would be the wake-up signal of the microcontroller to read out the temperature sensor. 

The microcontroller would be in sleep mode until the button is pressed and triggers the interrupt. The interrupt wakes up the microcontroller, which reads out the temperature sensor. After that, the microcontroller would go back to sleep. 

Such a procedure would save tremendous power, and our device's power could suddenly last for months. 

#### Summary
The crystal oscillator is pivotal in creating accurate timing signals, essential for tasks like PWM generation and communication protocols. Microcontrollers typically feature internal clocks. However, those are inaccurate, which is why most microcontrollers allow the addition of external oscillators for improved precision.

Clock speed, determined by the oscillator and CPU multipliers, dictates the number of operations per second. While higher clock speeds enhance processing capabilities, they also increase power consumption and heat generation. Conversely, lower speeds conserve power but may reduce overall performance.

Interrupts allow microcontrollers to respond to external events by temporarily halting normal operations to execute interrupt-service routines (ISRs). This capability is crucial for tasks like waking the microcontroller from low-power sleep modes or sampling sensor data in real-time. Sleep modes can extend battery life in battery-powered devices by magnitudes.

## Level 3 - Bus Protocols
<iframe width="560" height="315" src="https://www.youtube.com/embed/QpK-G_KWNxs?si=zEYwAW8NTsZMjlqo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Microcontrollers facilitate communication with other devices such as sensors, microcontrollers, or laptops using bus systems and communication protocols. In this level, we will delve into three fundamental bus protocols: Inter-Integrated Circuit (I2C), Serial Peripheral Interface (SPI), and Universal Asynchronous Receiver Transmitter (UART).

#### I2C
The Inter-Integrated Circuit (I2C) bus is a widely used serial communication protocol for integrated circuits on the same PCB or between closely located devices. It's a simple serial bus protocol. Yet, it doesn't allow for long distances or ultra-high speeds. Still, it is sufficient for most applications, and many sensors come with this communication protocol built-in. 

Firstly, let's distinguish between serial and parallel bus protocols. In a serial protocol like I2C, data is transmitted one bit at a time, similar to products moving along a conveyor belt one by one. A parallel bus protocol would be the same but with multiple conveyor belts operating simultaneously. Therefore, a series bus system does not require many signal lines, while a parallel bus system does require many. At the same time, the parallel bus system is faster. 

I2C utilizes two essential lines: the Serial Data Line (SDA) and the Serial Clock Line (SCL) pulled up by resistors to prevent undefined states. The clock line is there to synchronize the timing of the different devices, as they might vary slightly per used crystal. 

There is always one master and one or more slaves. The master produces the serial clock line and initiates the communication. The slaves listen to the serial data line to determine whether or not they are addressed and receive the clock line to synchronize with the master. Every component has its 7-bit I2C address, through which the master can indicate with which slave it wants to communicate with. 

The master continuously produces the timing on the serial clock line. Its frequency determines the speed of the transmission, and there are different modes of operation. 100 kbits/s would correspond the standard I2C mode, while 400 kbit/s would correspond to the fast mode. There are even faster modes, but remember: the faster the frequency, the easier it is to smoothen the data curve. At high frequencies, even a small capacitor can smooth the curve, and if we have a smooth signal, no communication can occur. At fast enough frequencies, even the capacitance of the wire itself can be enough to disrupt the communication. 

The master starts communication by sending a start bit followed by the slave address it wishes to communicate with. Slaves monitor the bus and respond if addressed. Depending on the master's command (read or write), the communication proceeds accordingly: slaves transmit data if requested to read or listen if requested to write.

It's important to note that while I2C supports multiple devices on the bus, the bus's bandwidth is shared among all devices. Adding more devices can reduce the frequency of data exchanges with each device.

#### SPI
The second bus you will encounter often is the Serial Peripheral Interface (SPI) bus. This one is different from the I2C but is still a serial bus with a master and slaves. 

It consists of four essential lines:
- **SCK (Serial Clock)**, which is the same as the SCL line and provides the slaves with the timing
- **MOSI (Master Out Slave In)**, which is used by the master to send data to the slave.
- **MISO (Master In Slave Out)**, which allows the slave to send data to the master. 

One significant difference from I2C is the inclusion of the Chip Select (CS) line. Each slave device on the bus is connected to the master through its own CS line. Through that, the master is able to  select a specific slave device for communication without transmitting addresses. The master does so by pulling down a slave's CS line. 

Another distinctive feature of the SPI protocol is its full-duplex capability. Unlike I2C, where communication is half-duplex (one direction at a time), SPI allows simultaneous bidirectional communication between the master and the slave. The master sends data to the slave using the Master Out Slave In (MOSI) line, while simultaneously receiving data from the slave via the Master In Slave Out (MISO) line.

As a result of these enhancements, SPI is a more time-efficient protocol. It is also capable of operating at higher frequencies in the MHz spectrum. Unlike I2C, SPI requires four connections from the master to each slave: SCK, MOSI, MISO, and CS. Despite requiring more connections, SPI offers significantly faster information transmission and improved efficiency. While the high speed of SPI is often unnecessary for model rocket projects, there are situations where its capabilities can still be beneficial.

#### UART
Finally, you will briefly learn about UART (universal asynchronous receiver transmitter).
This protocol is the standard for communication between microcontrollers and PCs. We use this protocol to program the microcontroller and to transmit live information of the microcontroller to the PC. 

It only consists of two lines - RX (receive) and TX (transmit). 
The RX line of the first device goes into the TX pin of the second device, and vice-versa. 
Unlike I2C and SPI, UART is designed for communication between only two devices.

UART does not use a clock line to synchronize the data transmission. Instead, both devices must agree on a common speed known as the baud rate. Common baud rates include 9600, 115200, and others. Both devices must be configured to use the same baud rate for successful communication.

There is more detailed information available about UART, but this basic understanding will suffice for designing your own flight computer. 

#### Summary
Microcontrollers communicate with other devices through various protocols.

I2C (Inter-Integrated Circuit) uses two wires: SCL (serial clock line) and SDA (serial data line). It features a master and one or more slaves. The master addresses the slave it wants to communicate with and provides the clock signal. I2C is a relatively slow but easy-to-use protocol, often implemented in sensors.

SPI (Serial Peripheral Interface) requires four wires: SCK (serial clock), MOSI (master out slave in), MISO (master in slave out), and a separate CS (chip select) line for each slave device. SPI enables full-duplex communication, allowing both the master and slave to send and receive data simultaneously. The use of chip select pins allows the master to select which slave device to communicate with without transmitting addresses.

UART (Universal Asynchronous Receiver Transmitter) is another serial communication protocol used between two devices, typically a microcontroller and a PC. It utilizes two lines: RX (receive) and TX (transmit), and operates at a predefined baud rate. UART is straightforward but supports only point-to-point communication without a master-slave hierarchy.

## Level 4 - Memory Sources and Programming
<iframe width="560" height="315" src="https://www.youtube.com/embed/RH56VlN6feY?si=df9JFKt7_yLHSQHz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Microcontrollers rely on various memory sources for storing firmware, programs, data, and configuration settings. Understanding these memory types is essential for the microcontroller selection for our flight computer designs.

In this level, we explore the three most essential ones: Flash memory, RAM, and EEPROM.
- The flash memory is where the microcontroller's firmware and program are stored. 
- The RAM is used for temporal data storage and manipulation while the microcontroller is running. For example, to store variables and buffers.
- Finally, the EEPROM stores small amounts of information that last over many power cycles, such as configuration settings and calibration data.

Finally, we will explore the programming interface of microcontrollers known as the bootloader.
#### Flash
Flash memory is a non-volatile memory, which means that the information is retained even after power is turned off. Each flash memory chip consists of several blocks, which are further divided into pages. These pages consist of multiple floating-gate MOSFETs that can store either a zero or a one by trapping a charge between two isolaters in the so-called floating gate. 

Flash memory is an electrically erasable and programmable read-only memory (EEPROM). As its name suggests, we can erase stored data, program new data, and read data. However, programming data isn't possible for single bits; instead, we must erase and program entire pages.

Flash memories have a limited life cycle, meaning we cannot continuously erase and program data onto them indefinitely, as the floating-gate MOSFETs would degrade over time. This limited write/erase cycle is a crucial consideration for their use.

These characteristics define flash memory's use cases, such as storing firmware or software. These types of data do not require frequent erasing and programming, typically only a few hundred times at maximum over the device's lifetime.

#### EEPROM
Even though Flash memory is a type of EEPROM, it is common to treat Flash memories and EEPROMs as two distinct types of memory in microcontrollers as they come with different use cases. 

Similarly to the Flash memory, the EEPROM is non-volatile and doesn't lose information upon shut-down. The first difference is that each byte of the EEPROM is individually programmable and doesn't require the user to erase an entire page. The disadvantage of this individualistic access is a lower reading and writing speed and a smaller memory density. However, EEPROMs come with the advantage of enduring more erase/program cycles. 

Out of those characteristics, it makes sense that the EEPROM is used to store data that must remain on the device after power-down but will be changed often. Examples would be the storage of configuration settings, user preferences, and calibration data. 

#### RAM
The last type of memory that we will discuss is random access memory or RAM. Compared to the other two memory sources, it is volatile, meaning its data is lost after power down. RAM is called "random access" because any memory location can be accessed directly, regardless of its location in the memory hierarchy. Its smallest units are either capacitors (Dynamic RAM) or flip-flops (Static RAM). These components allow for even faster read/write speeds than floating-gate MOSFETs. 

Due to the fast read/write speeds and the fact that its data storage is only temporary, the RAM's use cases are to provide the central processing unit (CPU) with data that it needs to access quickly during program execution. 

#### Programming
Programming a microcontroller involves a bootloader, which is a small program pre-installed in the microcontroller's memory. When the microcontroller is powered on, it first runs the bootloader. During this limited time, the bootloader waits for communication from the PC. The PC can signal to the bootloader that it wants to upload new code, a process often done via UART. 

If the PC requests to upload code, the bootloader receives the new program data and writes it to the appropriate memory location in the microcontroller. The bootloader ensures that the new program is correctly received and stored. 

If no new code is uploaded during the bootloader period, the microcontroller proceeds to execute the previously stored program. This fallback mechanism means that if the bootloader does not receive a communication signal from the PC within the specified time window, it defaults to running the existing program in memory.

#### Summary
Microcontrollers rely on various memory sources crucial for storing firmware, programs, data, and configuration settings. 

The three primary types are:
- **Flash Memory**: Flash memory is non-volatile and used to store firmware and programs. It is organized into blocks and pages, each page containing floating-gate MOSFETs that can store binary data. Flash memory allows for data erasure and programming but operates with a limited write/erase cycle.
- **EEPROM**: EEPROM is also non-volatile and used to store configuration settings, user preferences, and calibration data. Unlike flash memory, EEPROM allows for individual byte programming without requiring full-page erasure. However, it has slower read/write speeds and lower memory density compared to flash memory.
- **RAM**: RAM is volatile memory used for temporary data storage and fast data manipulation during the microcontroller's operation. It supports random access to any memory location and uses capacitors (DRAM) or flip-flops (SRAM) for rapid read/write operations.

PCs upload code to the microcontroller via the UART protocol. During a limited time after power-up, the bootloader waits for communication from the PC. If prompted, the PC can upload new code to replace existing firmware or programs in the microcontroller's memory. If no new code is received, the microcontroller proceeds to execute the current program stored in memory.

### Examples
Input - Button + Pull-down 
Input - Temperature measurement + ADC
Output - LED + diming LED (oscilloscope)
Temperature Measuring Device with Button - with Interrupt 

## Level 5 - Specific Microcontrollers
<iframe width="560" height="315" src="https://www.youtube.com/embed/uWUyqHQ8FEk?si=MKklnrLhLdkzX307" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Now, with all the microcontroller basics out of the way, let's look at three specific microcontroller examples. But before we do so, let's talk about breakout boards, modules, and on-PCB design.
#### Breakout vs Embedded Microcontroller
We can implement a microcontroller into our flight computer in one of three ways. 

The first way would be to use a third-party breakout board. Breakout boards are ready-to-use microcontrollers where all the necessary components are already pre-installed. The breakout board most often features a voltage regulator that provides the exact 3.3V needed, has an integrated crystal oscillator that provides accurate timing for the microcontroller, and incorporates a chip (a USB to UART bridge) for proper communication between the PC and microcontroller. Further, it features a pin header for easy access to the microcontroller pins and has a pre-installed bootloader. This implementation is most straightforward, as we can use those breakout boards out of the box. An Arduino Uno, an ESP32 Dev Module, or a Teensy 4.1 are all examples of such breakout boards. The processors that they incorporate are from different companies. An Arduino Uno, for example, features an ATMEGA16 microcontroller. The disadvantage is the increased weight, as we have an additional PCB and pin rows. Further, it is not as reliable as the connection between the pins could be error-prone. However, it is very beginner-friendly, and if we came to damage the microcontroller, we could replace it more easily. 

The second way would be by using a so-called module. A famous example is the ESP32-Wroom module, which we will look at. This module can be directly implemented on our own PCB and spares us a few steps compared with a full microcontroller implementation. Such a module internally features a crystal for timing, has a pre-installed bootloader, has extra FLASH memory, and a Bluetooth antenna. In this case, we only have to be concerned with the USB to UART bridge for programming and the power management of the microcontroller. 

The final way would be onto the PCB-embedded microcontroller. In this case, we have to do all the implementation ourselves. We have to select a proper crystal, establish the USB to UART bridge, provide power management, and sometimes have to install the Bootloader. Additional functionalities, like Bluetooth and WIFI, must also be implemented by us, which requires antenna design and RF matching. We will look at this kind of implementation by using an STM32 microcontroller. This method allows us to adjust our design to our needs to the maximum degree and results in the most lightweight PCBs, as we can decide which features we want to incorporate and which we desire to exclude. 

#### Summary
To summarize:
There are breakout boards, microcontroller modules, and plain on-PCB microcontrollers. 
Breakout board microcontrollers are ready out of the box without the need for any further integration. They incorporate voltage regulation, crystal oscillators for proper timing, sometimes add memory such as Flash and RAM, and handle microcontrollers to PC communication. These microcontrollers are the most straightforward to implement but the least flexible. 
Examples: Arduino Uno, ESP32 Dev Module, Teensy.

Microcontroller modules are similar but require us to do the power management and create the connection between the microcontroller's UART protocol and the PC's USB protocol through a USB-to-UART bridge. Yet, these modules integrate memory sources, a crystal oscillator, and functionalities like Wi-Fi and Bluetooth.
These microcontrollers are still relatively easy to implement but come with the advantage of a more flexible integration, leading to a more lightweight design. 
Example: ESP32-Wroom module.

Finally, the plain on-PCB microcontrollers require us to do the entire implementation. From the power management, the crystal oscillator, the USB-to-UART bridge, the addition of memory sources, or even RF antenna design, we must do all aspects ourselves. However, they also allow for the most flexible implementations, as we can choose from numerous microcontroller chip lines and are free to omit any features we won't use.
Example: STM32 line of microcontrollers.

In summary, breakout boards are the easiest to use but least customizable; microcontroller modules offer a balance of ease and flexibility; and plain on-PCB microcontrollers provide the highest level of customization at the cost of increased complexity in implementation.

## Level 6 - Teensy 4.1
<iframe width="560" height="315" src="https://www.youtube.com/embed/2HjFBwXpSfw?si=YVjiuIaLtwlFIQ1j" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
We are going to examine one example of each type of microcontroller implementation over the following levels. For each type, we will look at their features and their implementation. By the end of this section, you will have an understanding of how to implement anything from a breakout board microcontroller to a microcontroller on the PCB.

We will start with the simplest method of all three: the breakout board, specifically the Teensy 4.1. 

Up to this point, we have illustrated all the concepts and circuits on the whiteboard. From now on, we will draw up some of the schematics in a printed circuit board design software. The software we will use is Easy EDA. However, there are many more you could use, such as KiCAD, Eagle, or Altium. After you have learned about circuits for flight computer design, we will teach you how to use a PCB design software to create and order your own printed circuit board at the end of the course. However, in the following levels, we will focus on the circuits rather than the software. 
#### Features
A famous breakout board line of microcontrollers is the Teensy line of microcontrollers from PJRC. They are known for their fast processing speeds and are compatible with the Arduino IDE, an easy-to-use microcontroller programming environment.

Let's specifically look at their Teensy 4.1, which is their newest microcontroller and a powerhouse for flight computers. 

The Teensy 4.1 incorporates a Cortex-M7 microcontroller, which runs at a clock speed of 600MHz. This clock speed is around 300 times that of the Apollo guidance computer. So, with this processing speed, you can achieve almost any goal in model rocketry. It ran our program over a thousand times per second and is the fastest of all microcontrollers we will discuss here. 

Regarding peripherals, it is an outstanding option. If we look at the pinout, we can see countless (55) GPIO pins, lots of PWM pins (32), and 18 analog input pins. Further, it incorporates several bus interfaces, such as 3 I2C, 3 SPI, and 8 UART bus systems. The Teensy 4.1 almost certainly has the pin you will need. 

Another notable feature of the Teensy 4.1 is its onboard SD card slot, which allows for convenient flight data storage. Interestingly, an SD card is just a form of Flash memory tailored to a specific physical format. 

If the SD card storage or the internal Flash or RAM of the Teensy 4.1 aren't enough, we can add up to two QSPI Flash memory chips or two 8MB PSRAM chips to the bottom of the board.

QSPI stands for quad serial peripheral interface and is an advanced form of SPI, which we discussed previously. It has four (quad) data lines, which enables way higher transfer speed, which allows for several times faster reading/writing speeds. 

PSRAM is a pseudo-static RAM. We can use an additional chip like this to outsource large variable arrays to this temporal storage for real-time data processing. This memory addition could be beneficial, for example, to process camera information. 

The Teensy 4.1 is an outstanding option if you are looking for a microcontroller with incredible processing speed, countless GPIO pins, and easy project integration. 

#### Implementation
Implementing a breakout board microcontroller in your project, such as the Teensy 4.1, is straightforward. The only thing you have to provide is the power supply. Often, like in the case of the Teensy 4.1, these boards even feature their voltage regulator. In the case of the Teensy 4.1 microcontroller, we could provide input voltage from 3.3 - 5V. So, by simply connecting VIN to 5V and GND ports to GND, the microcontroller is up and running. 

Now, the only task left to do is to connect our sensors and outputs to the appropriate pins of the microcontroller. Here, a pinout can be highly useful. The pinout indicates which pins we can use for which purposes. Let's look at the Teensy's pinout. Here, we can see that we can use pin 1 for PWM control or the transmitter for the UART protocol, indicated by TX1. We could use pin 12 as one of the SPI pins (the MISO pin) or again as a PWM pin. Further, we can use all pins as regular GPIO pins. 

#### Summary
So, in summary:
The Teensy 4.1 offers a supreme processing speed of 600MHz and can do almost any calculation. Further, it adds countless GPIO pins, PWM pins, and bus protocols. This microcontroller will almost certainly have the pin you need. The onboard SD card slot simplifies data logging.

Finally, the implementation is very straightforward and only requires us to provide the board with power and to connect our sensors and outputs to the appropriate pins of the microcontroller. To do so, we can look up the pinout most breakout board manufacturers will provide. 

## Level 7 - ESP32
<iframe width="560" height="315" src="https://www.youtube.com/embed/QLiEcxBSDEA?si=zvIlbmmwC9uyg71s" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture 
In this lecture, we will examine another way of microcontroller implementation - the microcontroller module. We will specifically take a look at the ESP32-Wroom module and its implementation. By doing so, we will learn about the USB to UART bridge. 
#### Features
An example of microcontroller modules is the ESP32-WROOM line of modules. Specifically, we will be looking at the ESP32-WROOM32E-N8. 

An ESP32-WROOM module incorporates a 40MHz crystal oscillator, a QSPI Flash memory chip, and RF matching circuits into a single module. They are known for their Bluetooth and WIFI capabilities, which they incorporate inside the enclosure, and are also programmable using the Arduino IDE. 

In the WROOM line of the ESP32 microcontroller, there are different build forms - indicated by the letter after the WROOM32. The main difference in build forms is that some modules already incorporate the antenna (E) while others include a UFL connector to which an antenna must be connected (UE). The -N8 at the end suggests how large the incorporated QSPI Flash memory is (in our case, it is 8MB). Further, there are module variants with the ending -N8R2, which suggests the same flash memory size and an additional PSRAM of 2MB. 

This ESP32 variant has two CPUs that can run at up to 240MHz. Additionally, it features a low-power co-processor that we can use for trivial tasks. 

The used microcontroller inside the module would feature 48 GPIO pins. However, the module only breaks out 25 of them. We can use all of those as PWM pins. Further, the module features 15 12-bit resolution ADC analog input pins, and they even feature two analog output channels to create analog voltages with the help of an 8-bit DAC. 

It has 3 UART, 3 SPI, 2 I2C, and 2 unique I2S buses. I2S is similar to I2C and stands for inter-integrated sound. Those bus systems are utterly valuable to control chips for stereo sound or microphone inputs. 

The ESP32 WROOM modules are perfect for projects that require easy connectivity, such as Bluetooth or WIFI. They are more challenging to implement than a breakout board microcontroller but still seamless to integrate. They feature a decent amount of GPIO pins and processing power and excel at projects with low power consumption. Their sleep currents can be less than 5uA. 

For those who want to spare themselves the trouble of implementing the module, you can also use an ESP32 Dev module, which features this ESP32-WROOM-32E module as a breakout board. 

#### USB to UART bridge
Now, it's time to implement such a microcontroller module.
The first question we have to answer is how a computer can communicate with our microcontroller. You are probably familiar with USB, and you might think of it as solely being the connector. However, USB stands for "Universal Serial Bus," which clarifies that USB is the communication protocol with which our laptops and PCs communicate with their devices, such as keyboards, mice, and much more. 

The USB bus additionally provides the devices with power and consists of a host (our PC) and multiple peripheral slaves (our devices). It can communicate at very high speeds, depending on the protocol. USB 3.1, for example, can reach transfer speeds of up to 10 Gbps (gigabits per second). Further, it is a very complex protocol, able to do multiple transfer modes and device enumeration. Their connectors are standardized. Common ones are USB-C, micro-USB, and USB type A. 

Now, let's recall the UART (universal asynchronous transmitter-receiver) protocol. As we discussed previously, it is one of the protocols with which our microcontroller communicates. Its speed is given by the Baud rate, where standard values are 9600-115200 (bits per second), magnitudes less than the speed of the USB protocol. The UART protocol is intended for communication between two devices only, without a master/slave system. 

Okay, a computer commonly communicates by USB, while a microcontroller communicates with the UART protocol. While both are serial protocols, we have seen that they differ significantly, which explains why we need a device that translates between USB and UART. 

For us to upload code from a PC to a microcontroller, we need a USB to UART bridge. Two famous ones are the CP2102 and the CH340. 

The CP2102 is the most expensive one. It emulates a USB device, which the PC immediately recognizes when we connect it. We do not have to install drivers to upload code through this bridge. Instead, it simply works out of the box. 

A CH340, on the other hand, is cheaper but needs a driver for the PC to recognize the device. 
#### Implementation 
With the basics of the USB-to-UART bridge out of the way, it is time to implement such a module.

First, we have to provide power to the VDD pins. This time, we have to provide a regulated voltage of 3.3V. Although, it could theoretically also range from 3V to 3.6V. 

We also have to provide the RESET and BOOT functionalities manually. The RESET pin is needed to restart the program while the microcontroller is still powered. If the RESET (Enable) pin is pulled high, the microcontroller is in normal operation, while if it is pulled low, the microcontroller is resetting. We connect this reset pin to 3.3V with a pull-up resistor and a button, which connects the EN pin to GND when needed. As buttons tend to bounce when pressed, which is an unintended oscillation of a button's electrical contacts, we also add a capacitor in parallel that filters these spikes that are inconvenient for the microcontroller. 

The ESP32 will enter the serial bootloader when the boot pin (GPIO0) is held low on reset. Remember, the bootloader is the part of the program the microcontroller can enter after start-up, which allows us to connect to the microcontroller to program it. Therefore, we also connect a button from the BOOT pin to the ground and add a capacitor to prevent the button from bouncing. If the button isn't pressed, the microcontroller will default to run the program, currently on the flash, and if it is, we have a small time window to program the device.

Further, we have to implement a USB to UART bridge, which we connect to the TXD0 and RXD0 pins of the microcontroller. 

Here, we used the CH340, which is more straightforward to implement than the CP2102. For both, we look up their datasheets, specifically their connection diagrams. We connect the UART pins of the microcontroller to one side of the IC while we connect the data pins of the USB port to other pins of the IC. We also have to provide the IC with regulated 3.3V power and some filtering capacitors, as indicated in the datasheet. We also connect the USB port to VUSB, as we can take the 5V of the USB line to power the board when connected.

There are two more pins: the RTS and DTR, which we connected to the USB-TO-UART bridge. These are essential to indicate to the microcontroller that we automatically want to reset and boot the microcontroller to upload code. The PC communicates to the USB-TO-UART bridge that we want to upload code now, and by a transistor circuit, these two signals trigger the RESET and the BOOT pins accordingly. The transistor schematic behind it takes too much time to understand in this lecture's context. Remember that this circuit exists and that you should implement it as soon as you want auto-programming functionality for your flight computer with just one click in your programming environment. 
#### Summary
In this lecture, we explored microcontroller modules, focusing on the ESP32-WROOM module, specifically the ESP32-WROOM32E-N8 variant. These modules are renowned for integrating a 40MHz crystal oscillator, QSPI Flash memory, and RF matching circuits into a single module. They excel in providing Bluetooth and WiFi connectivity and are programmable using the Arduino IDE.

The ESP32-WROOM32E-N8 features dual CPUs running at up to 240MHz along with a low-power co-processor. It offers 48 GPIO pins with 25 broken out to the module, extensive peripheral support including UART, SPI, I2C, and I2S buses, and analog capabilities such as 15 ADC pins and 2 DAC channels.

Implementing an ESP32 module requires providing regulated 3.3V power. Additionally, managing the reset and boot functionalities involves adding buttons to the RESET and BOOT pins and pull-up resistors. When the RESET pin receives a low signal, the microcontroller resets. Pressing the BOOT button after powering up puts the microcontroller into bootloader mode, allowing code uploads. Further, we add a capacitor to prevent the button-bouncing.

Furthermore, integrating a USB-to-UART bridge like the CH340 or CP2102 is essential for programming and communication with a PC. Finally, a transistor circuit allows for auto-uploading code from our programming environments without manually pressing the reset and boot buttons. 

## Level 8 - STM32
<iframe width="560" height="315" src="https://www.youtube.com/embed/hjtwoY0-eYs?si=bwWvjl2EVYiXZp4_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
We will take things further and implement a plain microcontroller chip at this level. This implementation is the final and most advanced form, and a slight error in your design can easily lead to the entire PCB being dysfunctional. 

The implementation of microcontroller chips varies greatly by the used chips. Two famous lines of the microcontroller are the ATMEGA and the STM32 lines. The ATMEGA microcontrollers are commonly implemented in Arduino boards, while the STM32 microcontrollers are heavily used in the industry. Here, we will describe the STM32 line of microcontrollers. 

We will look at their general features. Dive into the naming conventions of STM32 microcontrollers. Look at the implementation of a specific STM32 - the STM32F722RET6-
By doing so we will acquire information about their specific programming interface Serial Wire Debug (SWD). We will look at our first oscillator implementation, and finally, we will learn about the Cube IDE MX tool.
#### Features
The STM32 line of microcontrollers stands out due to its extensive range of options. There is almost certainly the perfect STM32 microcontroller for every project out there. There are Bluetooth and WIFI variants, variants with numerous GPIO pins, and low-power and high-speed versions. 

The amount of options makes the use of those microcontrollers highly scaleable. Further, they are known for their robustness, and we can rely on them in critical applications. 

#### Naming Convention
Let's look at a specific version of the STM32: 
STM32F722RET6
The naming might be confusing, but it follows the same scheme for all the STM32s. If we want to work with this microcontroller, we should familiarize ourselves with their naming conventions. 

- F7: indicates the used processor. All STM32s use Cortex-M processors. The F stands for the line of STM32. Where F is either a foundation or a high-performance variant, G would stand for a mainstream variant, L stands for a low-power version, and H stands for a high-performance variant. The seven stands for a Cortex-M7 processor, which is the highest performance core there is on Cortex processors. This one has a clock speed of 216MHz. 
- The next two digits indicate the microcontroller line. 
- The following R represents the number of pins this microcontroller breaks out. R corresponds to 64 or 66 pins. The microcontroller version with the fewest pins is F, with only 20 pins, and the one with the most is I, with 176 pins.
- The subsequent number or letter stands for the flash memory size. In our case, E stands for 512Kbytes. You may think 512Kybtes is very little memory compared to the 8MBytes the ESP32-WROOM-32E-N8 uses. However, we program the STM32 line with their tool, which allows us to save tremendous amounts of storage. In our case, the 512Kbytes were more than enough. 
- The next one stands for the package of the microcontroller. T stands for LQFP. The package is the form factor of the chip. There are variants where the pins are at the bottom of the chip and inaccessible, while there are versions with broken-out pins like LQFP. 
- Finally, there is the temperature range in which the chip is functional. 6 indicates a range of -40 to +85°C. 

DigiKey provides a page that outlines the meaning of all the numbers to look up. 
https://www.digikey.at/de/maker/tutorials/2020/understanding-stm32-naming-conventions?utm_adgroup=STMicroelectronics&utm_source=google&utm_medium=cpc&utm_campaign=Dynamic%20Search_EN_Supplier&utm_term=&productid=&utm_content=STMicroelectronics&utm_id=go_cmp-9415055229_adg-98040915040_ad-668047754589_dsa-459571002621_dev-c_ext-_prd-_sig-Cj0KCQjwpNuyBhCuARIsANJqL9NuQjvpgdRDj_jcrQFeAt_oQAfYkwKz_4l5YTTlH_azxBfwnVOBTP0aAnACEALw_wcB&gad_source=1&gclid=Cj0KCQjwpNuyBhCuARIsANJqL9NuQjvpgdRDj_jcrQFeAt_oQAfYkwKz_4l5YTTlH_azxBfwnVOBTP0aAnACEALw_wcB

#### Implementation
The implementation of an STM32-based microcontroller is more advanced than the two we have looked at before. 
To see how we can do it, let's devise the implementation of the STM32F722RET6 we discussed previously. 

The implementation will consist of 
- the power management
- the programming interface (serial wire debug)
- the configuration pins
- the oscillator design
- and the pin assignment using their MX tool

##### Power Management
On this IC, there are a few more pins that we have to provide with power. We can look up how exactly the power supply should look by viewing the hardware development guide that ST provides for all their STM microcontrollers. For this one, we have to look at the STM32F7 AN4661. 

First of all, there are the standard VDD pins for the digital logic of the IC. We provide those pins with a voltage of 3.3V and a capacitor of 100nF per pin each, which will vary by package. Additionally, we add a 4.7uF bulk capacitor for the VDD line. 

The voltage supply for the analog VDDA pins needs special treatment to improve the ADC's stability and accuracy. We create a circuit with the 3.3VDD on one side and add a 1uF capacitor. We add the 3.3VDDA line on the other side and a 1uF and 10nF capacitors. We connect the two circuits by a ferrite bead, which you probably haven't yet heard about. Ferrite beads are specialized inductors that are used primarily for filtering high-frequency noise in electronic circuits. In this case, we utilize the ferrite bead to electrically separate the voltages and to make the analog voltage cleaner.

The next voltage pin we must look at is the VCAP1 pin. The microcontroller needs this pin for the internal voltage regulator that creates an even stabler voltage for the internal components of the IC. On other STM32F7 versions, we can bypass this internal regulator. However, on this particular one, the regulator is always enabled. To ensure the proper functioning of the regulator, we have to provide the controller with a capacitor on the VCAP1 pin. It is crucial to select the capacitor's ESR (equivalent serial resistance) value to fall between 0.1 and 0.2 Ohms.
The internal voltage regulator creates a voltage of 1.2V, which we should be able to measure on the VCAP pin.

We don't use the final pin of the power supply VBAT. We would only need this pin in case we wanted to keep real-time clock measurements, such as time of day, day, month, etc. In this case, we would connect a button cell that continuously supplies the microcontroller with power. As we don't use this pin, we connect it to the standard 3.3VDD line. 

##### Serial Wire Debug (SWD)
To program an STM32, we do not have to provide the USB to the UART bridge ourselves. Instead, we use programming devices such as the ST-Link V2 to program any STM32. The programmer connects to the microcontroller by either JTAG or serial wire debug (SWD) and to the PC by USB. 

JTAG has a total of 20 pins, while SWD uses only four. As we want to minimize weight and PCB real-estate in-flight computer design, we will be using the SWD interface, which consists of the following four pins: 

- **SWDIO (Serial Wire Debug Data Input/Output):** This is the bidirectional data line used for communication between the debugger and the target microcontroller.
- **SWCLK (Serial Wire Debug Clock):** This is the clock line used to synchronize the data communication.
- 3.3V 
- and GND. 

SWD supports full debugging capabilities, including setting breakpoints, stepping through code, inspecting variables, and modifying memory. It also allows for programming the Flash memory of the microcontroller.

##### Configuration Pins
Similarly to the ESP32, we provide the STM32 with information on whether it shall reset or enter the bootloader upon power-up. 

The NRST pin corresponds to the reset pin in this scenario. The reset happens when we connect this pin to GND. To put the microcontroller in regular operation, we leave the reset pin floating or pull it up to 3.3V through a pull-up resistor. In fact, the IC pulls up the NRST pin internally. So, we don't have to add anything here. Often, a capacitor is added between the NRST pin and GND to add EMS (electromagnetic susceptibility) protection and avoid parasitic resets. When using the SWD interface, a program reset via the NRST pin is not actually necessary since SWD bypasses the bootloader and can reset and flash the MCU directly.

There's also a BOOT pin on the STM32. However, when we program the microcontroller via the SWD interface, the bootloader is bypassed. Still, if we want to flash the chip via USB through a USB-TO-UART bridge, we would have to pull BOOT0 high after a reset to enter the internal bootloader. To keep our options open, I recommend using a tactical switch on the BOOT0 pin, which pulls it high, with a pull-down resistor that pulls BOOT0 low. 

##### Oscillator Design 
Something we also didn't yet provide for the microcontroller is the clock source. The clock source for the STM32F7 must fall between 4-26MHz in order for the microcontroller to function. To establish a reliable oscillator circuit, we need to include two capacitors known as load capacitors. Load capacitors are capacitors connected to the terminals of a crystal oscillator. They form part of the resonance circuit that determines the oscillator frequency. The correct selection of load capacitors is essential for stable and accurate frequency operation.

Let's select a 12MHz crystal that falls between the stated frequency range in the datasheet. The crystal we selected states the external load capacitance it would like to see, which was given by 20pF. 

Now, there is a rough estimation formula with which we can determine the capacitances of the two capacitors in order for the circuit to work:

$C = 2*(C_{load} - C_{stray})$

The stray capacitance gives the unwanted capacitance of a circuit and depends on the PCB layout and the input capacitance of the oscillator pins.
For most designs, it roughly falls between:
$C_{stray} = 3 - 5pF$  

When assuming a stray capacitance of 5pF and inserting in the formula above, we get a value of 30pF for the capacitors that we shall implement. Now, we have to choose the next highest available capacitor size: 33pF.

Just like that, our oscillator design provides our microcontroller with periodic timing information on which it can base its bus protocols, PWM signals, and more. 

##### STM32 Cube IDE MX
To set up and program the STM32, we don't use the Arduino IDE but instead use their provided software - the STM32 Cube IDE. Within this tool, we can write our code, upload code to our microcontroller by connecting it through an ST-Link, and debug our code live. 

There is a CubeIDE MX tool inside the environment that allows us to set up the pins and the used clock during the development process. It graphically shows us which pin function we can assign to which pin, and makes as aware of any conflicts. 

So, as you have seen the STM32 line of microcontrollers is very different to the ones we discussed before. They are implemented uniquely, programed in a different environment, and allow debugging. There are variants for almost any application, and they are very robust.  

#### Summary
Now, you are familiar with all three implementation types. 
If you strive for the fastest processing speed, countless GPIO pins, bus functionalities, easy implementation, and an onboard SD card, a good starting point for your design would be the Teensy 4.1. 

For a more advanced PCB design, you can implement a microcontroller module. The ESP32-WROOM seamlessly incorporates connectivity, such as Bluetooth and WIFI, and excels in low-power situations. It is not as fast as the Teensy 4.1, but fast enough for most flight computer designs. Further, it is more difficult to implement than a breakout board, as you additionally need to implement a USB-to-UART bridge. Still, it is relatively easy to do. 

The last option, is to implement bare-bone microcontrollers. This option is for the advanced of you that want to familiarize themselves with microcontrollers used in the industry. The STM32 line offers and option for almost any application and provides fast processing speeds, countless GPIO pins, and many bus protocols. They are programmed in their own environment, upload code through their ST-Link programmers, and allow real-time debugging. To make them work, we have to design the oscillator circuit ourselves and have to incorporate the programming interface. 
