---
layout: page
title: Electronics Circuits
permalink: elec-circuits
---
## This path is work in progress!
The material that we provide in the following levels is by now means complete but it might help you to learn about the subject yourself, while we are working on providing content for you! 

Now that you are familiar with the basics of electronics and some standard components, we can think about how we can arrange them to create functional units that we can use to operate our rockets. 

## Level 1 - System Overview
### Lecture
Let's look at what a typical flight computer system might look like. 
Here we have the overview of a single microcontroller flight computer system. 
We have used systems like these four over five years, and only recently made the switch to multiple microcontroller design. 
![](/assets/images/Flowchart.jpeg)
As you can see, we can divide a flight computer into many sub-units that all have their own responsibilities. There are some sub-units that are always required and some that could be left out. 
#### Power Management
One that will be required is the power management unit, as all components and ICs need to be powered in order to function. The power management unit takes a input voltage and regulates it to the needed voltage levels - often 5V and 3.3V. Most ICs that we will use for our circuits require a specific voltage (most of the time 3.3V) in order to function.

The power management doesn't necessarily have to sit on the board that you develop, but it must happen somewhere. In stack, for example, the power management is done on the CORE board. The FUSION and the OUT board do not bear their own power management systems, but instead receive power through the connector with which they connect to the CORE board. 

#### Microcontroller
You can think of a microcontroller to be a mini computer. It is comprised in a single package integrated circuit and incorporates one or multiple CPU cores along with memory and programmable input/output peripherals. 

The input/output peripherals allow us to read out sensor data and to control components. Microcontrollers feature many pins around their package. Some of them are needed to power the microcontroller, some can be used to input an accurate timing signal, and some are GPIOs (general purpose input/output pins). 

We can assign the GPIO pins to be an input or an output pin. Some GPIOs have additional functionalities, like communication, to which we can assign them to. 

#### Sensors
Sensors are our sensory organs of our flight computer. With the help of them we can determine our rocket's orientation, its acceleration, velocity, and position, as well as its altitude. 

There are many more sensor we could add to our flight computer to determine properties such as:
- temperature 
- humidity
- voltage or current
- radiation 
- light and infrared wavelengths 
- gas compositions 

Our microcontroller communicates with the sensors via a bus protocol, which we will also learn about in a later level. 

#### Outputs
The flight computer's outputs are like the limbs the muscles of our body. With them we can intervene in our environment. For model rocketry, we can subdivide them into:
- pyro channels
- indicators
- and servo control

These outputs are controlled by the microcontroller and the instructions of when the microcontroller should control which outputs are set in the program we uploaded.
Most of the decisions will be based on the sensory readings. 

Pyro channels are needed to ignite model rocket engines and to trigger heating wires. With heating wires, we can, in turn, control various mechanisms, such as landing legs, air brakes, and the deployment of our parachute. 

Indicators, visually represent flight states or current errors to the user by the means of LEDs, speakers, or displays. 

And servo control is needed to steer our thrust vector control system (TVC) to actively stabilize our rocket. 

#### Telemetry 
Another way of communicating with the user, is by the means of telemetry. 
Telemetry is the transmission of data through the air. 
The transmission can occur in both ways. 

So, the rocket could send us live flight data, such as altitude and orientation. 
While, we could send the rocket commands to change the flight settings, to initiate the countdown, or to abort mid-flight. 

There are many ways of making such a communication possible, such as through Bluetooth, Wi-Fi, and radio communication. 

#### Summary
Every flight computer system can be divided into sub-units that must perform certain tasks. 

Input voltage must be regulated by the power management unit to supply all the other sub-units with power. 

The microcontroller is a mini computer that features input/output peripherals, which we can program to read out sensor data and to control our outputs. 

Sensors are our sensory organs with which the rocket knows its current state or with which it can record valuable scientific data, while outputs are similar to our muscles with which we can intervene in our environment. 

And finally, there's telemetry with which we can control our flight computer from afar and receive valuable information mid-flight.  