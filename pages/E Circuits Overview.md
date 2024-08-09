---
layout: page
title: Electronics Circuits
permalink: elec-circuits
---
## This path is work in progress!
The material that we provide in the following levels is by now means complete but it might help you to learn about the subject yourself, while we are working on providing content for you! 

Now that you are familiar with the basics of electronics and some standard components, we can think about how we can arrange them to create functional units that we can use to operate our rockets. 

## Level 1 - System Overview
<iframe width="560" height="315" src="https://www.youtube.com/embed/e55LFtrIxVw?si=-vC67JVFEke3OihL" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Let's look at what a typical flight computer system might look like. Below is an overview of a single microcontroller flight computer system. We have used systems like these for over five years and have only recently switched to a multiple microcontroller design.
![](/assets/images/Flowchart.jpeg)
As you can see, we can divide a flight computer into many sub-units, each with its responsibilities. Some sub-units are always required, while others can be optional. In the following chapters of this electronics course, we will focus on each aspect of a flight computer one by one.
For now, let's get a brief overview of all the subsections that make up a flight computer design.

#### Power Management
An on-all-board required sub-section is the power management unit, as all components and ICs need power to function. Essentially, the power management unit handles everything that is involved in delivering the right amount of voltage and current to your electronic components. 

In the chapter about power management, you will explore several key topics:
- **Voltaic Cell:** First, we’ll cover fundamental concepts such as oxidation and reduction, noble metals, and the galvanic series to explain the simplest form of a battery - the zinc/copper voltaic cell. Additionally, we’ll discuss discharge and recharge processes to provide a comprehensive understanding of how these cells function.
- **Battery Selection:** Building on that foundation, you’ll learn about different battery types, including Li-Ion, LiPo, and NiMH. We’ll also address important factors for battery selection, such as capacity, cell number, C-rating, and connectors.
- **Voltage Regulator:** Moving forward, we’ll examine various types of regulators, including shunt regulators, linear regulators, and switching regulators. Understanding these will help you select the correct regulator type and implement it accordingly. 
- **Regulator Circuit Design:** Finally, we will look at the implementation of the LM2596, a specific switching regulator.
#### Microcontroller
We can think of a microcontroller as a mini-computer. It is a single-package integrated circuit with one or more CPU cores with memory and programmable input/output peripherals.

The input/output peripherals allow us to read sensor data and control outputs. Microcontrollers feature many pins around their package. Some pins power the microcontroller, some provide accurate timing signals, and others are GPIOs (general-purpose input/output pins). 

In the chapter about microcontrollers, we will delve into the following key topics:
- **Pin Types:** To begin, we’ll cover different pin types, including GPIO pins, analog input, analog output, and PWM pins. We’ll also discuss pull-up and pull-down resistors, which play a role in signal stability.
- **Clock Generator:** Moving forward, we’ll explore the clock generator. You’ll learn about clock speed, interrupts, and sleep modes, which are essential for managing the microcontroller’s performance and power consumption.
- **Bus Protocols:** Next, we’ll provide an overview of bus protocols such as I2C, SPI, and UART. Understanding these protocols will help you interface the microcontroller with other components and devices.
- **Memory Sources:** Additionally, we’ll examine different types of memory, including Flash, EEPROM, and RAM. We’ll also discuss how microcontrollers are interfaced for programming.

Finally, we will explore three levels of microcontroller implementation:
- **Beginner Level:** We’ll start with the implementation of a complete microcontroller, the Teensy 4.1, onto our flight computer.
- **Intermediate Level:** Next, we’ll look at the incorporation of a microcontroller module, the ESP32.
- **Advanced Level:** Lastly, we will examine the industry-standard STM32, offering insights into how to implement bare-bone microcontrollers.
#### Sensors
Sensors are the sensory organs of our flight computer. They can determine our rocket's orientation, acceleration, velocity, position, and altitude. 

There are many more sensors we could add to our flight computer to determine properties such as:
- temperature 
- humidity
- voltage or current
- radiation 
- light and infrared wavelengths 
- gas compositions 

In the chapter about sensors, we will explore:
- First, the **Gyroscope**, including its functional principle, how it determines orientation, key parameters for selection, and the importance of calibration.
- Next, we will move on to the **Accelerometer**. Similar to the gyroscope, we will cover its operational principles and key considerations for use.
- Following that, we will examine the implementation of the **BMI088** into our flight computer, which combines both a gyroscope and accelerometer into a single package. 
- Then, we will delve into **Barometers**, specifically studying the BMP388 and focusing on concepts like oversampling and the IIR filter.
- Afterward, we will explore the **Voltmeter** and its application in our flight computer.
- Finally, we will consider **Additional Sensors**. This lecture includes other helpful sensors such as the magnetometer, GNSS receiver, and more.

#### Outputs
The flight computer's outputs are like the limbs or muscles of our body. With them, we can intervene in our environment. For model rocketry, we can subdivide them into:
- Flight data storage
- Indicators
- Pyro Channels
- And, Actuators

These outputs are controlled by the microcontroller. The instructions of when the microcontroller should control which outputs are set in the program we uploaded. Most of the decisions will be based on the sensory readings. 

In the chapter on outputs, we will explore: 
First, **Flight Data Storage.** After performing model rocket flights, we want to be able to analyze them to identify potential problems or assess the rocket's performance. To do so, we must access the flight's sensor data and the microcontroller's decisions. Currently, all flight data is lost immediately, so we must store our flight data using SD cards or flash memory chips. 

Next, we will move on to **Indicators.** These visually represent flight states or current errors to the user through LEDs, speakers, or displays.

Following that, we will delve into **Pyro Channels.** Pyro channels are needed to ignite model rocket engines and trigger heating wires. With heating wires, we can control various mechanisms, such as landing legs, air brakes, and the deployment of our parachute. 

Finally, we will consider **Actuators**, specifically the servo motor needed to steer our thrust vector control system (TVC).

#### Telemetry 
Another way of communicating with the user is by means of telemetry. 
Telemetry is the transmission of data through the air. 
The transmission can occur in both ways. 

So, the rocket could send us live flight data, such as altitude and orientation. While we could send the rocket commands to change the flight settings, initiate the countdown, or abort mid-flight. 

There are many ways of making such communication possible, such as through Bluetooth, Wi-Fi, and radio communication. 

#### Summary
We can divide every flight computer system into sub-units that must perform certain tasks. 

The flight computer must regulate the input voltage in the power management unit to supply all the other sub-units with power. 

The microcontroller is a mini-computer featuring input/output peripherals, which we can program to communicate with sensors and control outputs. 

Sensors are our sensory organs with which the rocket knows its current state or with which it can record valuable scientific data. Outputs are similar to our muscles, with which we can intervene in our environment. 

And finally, telemetry enables us to control our flight computer from afar and receive valuable information mid-flight.  

The next section of this course is about to begin, so buckle up and get ready to design the circuits for our flight computer. It’s essential to have a clear grasp of the fundamentals we’ve covered so far, as these concepts will underpin the more advanced topics we will explore. If there are any areas where you need more clarity, now is the time to review them. Understanding these basics thoroughly will be crucial as we move forward.


### Activity 1: Unit Dissection
As you just learned, we can split every flight computer into many sub-units.
Your task is to do the same with the Buffalo Rev. E flight computer. 
The different sections are marked in different colors, and your match the different colors to the corresponding sub-section name. 

Additionally, major components of each section will be provided with names. So, you can look them up in the web if you don't know what the section could be about. 

**Solution:**

### Activity 2
Which subsection/subsections could we leave out to implement in our flight computer for it to still be able to record flight data? 

**Solution:**
Telemetry