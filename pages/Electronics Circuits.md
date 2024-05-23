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

## Level 2 - Voltaic Cell 
### Lecture
In the development process of a flight computer, a reliable and robust power supply is crucial for its success. The power supply must provide stable and sufficient power to all the components of the flight computer. We will learn how we can achieve this in the following levels.
In this level we will learn about the element that powers our flight computer - the battery or voltaic cell. 


<iframe width="560" height="315" src="https://www.youtube.com/embed/7b34XYgADlM?si=mGbRgA8745nqifg0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


A galvanic or voltaic cell uses a chemical reaction to create electricity. 
To do so, they use an oxidation reduction reaction.

#### Oxidation and Reduction 
To understand the voltaic cell we must first coin the terms oxidation and reduction. 
Oxidation is the process of given up electrons, while reduction is the process of receiving electrons. 

One element can only give up electrons, if another element takes those electrons up. Therefore, it's always an oxidation reduction reaction or redox reaction. 

The anode is the place of oxidation, while the cathode is the place of reduction. 

#### Noble Metals and Galvanic Series
Noble metals are found in nature in their pure state, such as silver, platinum, and gold. They are resistant to corrosion, which is basically a redox reaction, where the metal oxidizes (gives up electrons).

The nobler the metal the less likely galvanic corrosion occurs, and the less likely the element will give up electrons. How noble a metal is, is represented in the galvanic series. Magnesium for example is the least noble metal, and occurs naturally only in combination with other elements. It has such a low nobility that it even reacts with oxygen to burn, which is also a form of redox reaction. 

#### Zinc and Copper Voltaic Cell
If we look at the galvanic series, we can determine that copper is nobler than zinc. 
Therefore, a zinc nail would corrode in a copper ion solution. 

In a voltaic cell we separate the two metals into two half-elements. 
In one half-element we have a piece of zinc in a zinc sulfate solution.
In the other half-element we have a piece of copper in a copper sulfate solution. 
In a zinc sulfate solution there are both zinc ions and sulfate ions. The zinc ions are twice positively charged while the sulfate ions are twice negatively charged. The same is true for a copper sulfate solution. The charges cancel out and result in a neutral solution. 
Both zinc and copper ions are simply without two of their electrons, which means that they are twice positively charged ions. Ions can dissolve in water because of their polarity, which is why the  zinc and the copper ions are in their aqueous state. 

Both half-elements alone would not react in any way. However, if we connect them through a wire, the nobler copper ions that lack two electrons in the sulfate solution wants to pull electrons from the less noble zinc. One of the zinc elements gives up two electrons that move through the wire to the copper ions. Remember, moving electrons is what we call current. This means that we can use this electron flow to light up an LED by interposing an LED in the wire. 

Now the zinc element is twice positively charged, which means that it is a positive ion, which dissolves in water. On the other hand, the twice positively charged copper is attracted to the copper metal, where it takes up the two electrons and becomes a solid. Over time the, zinc electrode dissolves, while the copper electrode enlarges. 

However, an imbalance would build up in the zinc sulfate and copper sulfate solutions. The zinc sulfate solution gains more and more zinc ions, which makes the solution net positively charged. On the contrary, the copper sulfate solution loses copper ions, which makes the solution net negatively charged. If enough charge is built up, the reaction could no longer occur and the current would stop flowing again. To counteract this saturation, we connect the two half-elements by a membrane that only allows sulfate ions to pass through. If now an imbalance is present, the sulfate ions move from the copper sulfate to the zinc sulfate. Through that, the zinc sulfate gains negative charges, which makes it neutral again, while the copper sulfate also lose negative charges, which makes it neutral as well. The substrate that allows this balance to occur is called the electrolyte. In our case the zinc sulfate and copper sulfate are the electrolyte of this cell. 

In our case the zinc is the anode, as it is the location of oxidation. It gives up electrons.
The copper is the cathode, as it is the location of reduction, and it takes up electrons. 

The electric potential energy difference (voltage) such a cell creates, depends on the the difference in nobility of the two elements, which is represented by standard potential given in the galvanic series. It is measured by using a the concerned metal paired with a hydrogen electrode. 

Zinc would give up electrons when paired with hydrogen, and, therefore, has a standard potential of -0.76V, while a copper would receive electrons from hydrogen and has a standard potential of +0.35V. The total voltage a voltaic cell creates is the difference between the two standard potentials. So, in our case a voltage of around 1.11V.

#### Discharged and Recharging
This process can happen until there are not enough zinc elements or copper ions left. The voltage of the cell will decrease the more elements converted, and at some point the reaction will stop. This is when the voltaic cell is fully discharged. 

For rechargeable batteries, a voltage that is higher than the battery's own voltage is applied from the outside to the two poles of the battery. In the case of the zinc/copper battery this is not efficient, as the zinc might dissolve unevenly However, if we were to take the example of this material combination. Recharging would mean that the cooper is pressured to give up electrons, and that zinc is pressured to receive the electrons. Through that, the previous reaction could be undone. 

#### Summary
Every battery follows the principle of the voltaic cell. 
Inside such a cell there are two metals of different nobilities. 
The less noble metal gives up electrons, while the nobler metal receives the electrons - this process is called a redox reaction. The less noble metal is the place of oxidation - the anode, while the nobler metal is the place of reduction - the cathode. 

An easy to understand example is that of zinc and copper. 
Zinc is in the zinc sulfate solution and copper in a copper sulfate solution. The two half cells are connected by a membrane. By connecting the two elements through a wire, the zinc elements give up two of their electrons, which makes the zinc twice positively charged and dissolved in water. The electrons move to the twice positively charged copper elements. These copper elements become solid and attach to the copper electrode. The charge difference in the solution is counteracted by a sulfate movement from the copper sulfate to the zinc sulfate. 

How much voltage a cell can create, depends on the standard potential which is given in the galvanic series. A zinc/copper cell creates around 1.11V. This voltage will reduce gradually until no electron movement is left. This is what we call a discharged battery.

A zinc/copper cell is usually not rechargeable. However, for rechargeable batteries, we connect a higher voltage to the two poles of the battery that pressure the materials to undo the previous reaction. 
## Level 2 - Battery Selection
### Lecture
#### Battery Types
So, now that we know the basic functioning of a voltaic cells we can discuss a few different battery types that are suitable for model rocketry: 

##### Lithium-Ion (Li-ion)
Lithium Ion batteries use a liquid electrolyte that facilitates the movement of lithium ions between the anode and the cathode. Remember: the electrolyte in our zinc copper cell was the sulfate solution that neutralized the charges on both sides. 

The cathode in the Li-ion is typically lithium cobalt oxide, while the anode is often graphite. 
- Li-ion have a nominal cell voltage of around 3.6V, which is the voltage at which the battery shall be stored
- A fully charged voltage of 4.2V, above which the battery suffers severe damage.
- And fully discharged voltage of 2.5-3V below which the battery again suffers permanent damage. 

Li-ion batteries were used for a long time already, and are present in many consumer devices today, such as laptops, mobile phones, and cordless screwdriver.

It comes with the advantage of having a very high energy density, which means that it is able to store a lot energy in little volume and at a low weights. The low weight factor makes it a perfect option for model rocketry. Further, they are able to output very high currents.

On the contrary Li-ion come most of the time in a cylindrical form factor, which may be inconvenient to use in model rockets. Further, they are expensive, and can be dangerous. They must be handled with care, as short circuit or a too high charging process may lead to them taking fire. 

##### Lithium Polymer (LiPo)
Lithium polymer batteries are very similar to the lithium ion batteries. However, they use a solid polymer electrolyte instead of a liquid electrolyte. The electrons consist of the same materials, lithium cobalt oxide and graphite. 

This results in the same nominal, fully charged, and fully discharged voltages of 3.6V, 4.2V, and 3V. 
They also come with the same benefit of having a high energy density, although Li-ion battery's energy density is slightly higher. The advantage of the LiPo battery is that it comes in many form factors, which make them convenient to implement in model rockets. Further, they are able to output very high currents just like Li-Ion batteries, which is why they are often used in drones or RC cars. The battery also comes with the same disadvantages, as being quite dangerous to use and expensive. 

##### Nickel-Metal Hydride (NiMH)
Nickel-Metal Hydride batteries use a potassium hydroxide electrolyte solution, a hydrogen-absorbing alloy for the anode and nickel oxyhydroxide for the cathode. 

They have:
- a nominal voltage of: 1.2V
- a fully charged voltage of: 1.4V
- a fully discharged voltage of: 1V
 
These batteries come at the advantage of being more robust and less likely to suffer catastrophic failures like LiPo or Li-ion. They can tolerate overcharging with greater extent and are slightly less expensive. 

However, they have a lower energy density, meaning they are heavier and bulkier for the same amount of stored energy. There current output is mostly not as high as those of the lithium alternatives, but high enough to power the devices that we use in model rockets. 

In model rocketry they are good to use when robustness and safety are the highest priority. For people that haven't yet used batteries often, they are recommendable to be use. 

##### Type Selection
All three types of batteries are good to use in model rocketry, as all three of them have a relatively high energy density and good current output. 

Li-Ion are the best regarding energy density but come at the disadvantage of their cylindrical form factor. LiPo batteries are a slightly worse in energy density, but are available in all different forms. They are the battery type that we have used for all of our flight computers up to this point. However, both of them are dangerous to handle. We, for example, once forgot to deactivate the charger, which caused the LiPo battery to inflate almost to the point of explosion. We were very lucky at that point that no severe damage was caused. 

A safer alternative would be the NiMH, which is mor robust, can handle overcharges better, and is even cheaper. It comes at the disadvantage of lower, but still good energy density. NiMH are recommendable for all that aren't yet experienced with batteries. 

#### Capacity
A major characteristic of a battery is its energy rating. It gives us an information about how much energy can be stored in the battery and is given in Ampere times hours. 

A battery with a rated energy of 1 Ah has enough energy stored to provide 1 A of current for 1 h. If we discharge only 0.5A, a battery of only 0.5Ah could also supply our flight computer for one hour. 

$C=I*t$ ... Capacity in A*h

However, we should keep in mind that this is only a theoretical value. It gives us the absolute maximum energy that can be stored. In reality, for example, we should never discharge more than 80% of the capacity of a Li-Ion, LiPo, or NiMH, as a deep discharge, creates permanent damage that can lead to safety concerns on the lithium types, or to long-term performance drops on all types. 

#### Number of Cells
LiPo and Li-Ion batteries have a nominal cell voltage of 3.7V while NiMH batteries have a nominal voltage of 1.2V. 

Most flight computers will need a higher voltage, to be able to control servos and pyro channels effectively. The cells we previously described can also be put in parallel and series. If we put cells in parallel, their capacities add up, while the voltage remains the same. If we put the cells in series, the voltage of the cells adds up, while the capacity remains the same. 

Batteries often feature multiple cells inside to increase the capacity and voltage. How much the voltage of a battery is, is given by the cell number. 
A three-celled LiPo battery, for example, consist of three LiPo cells put in series. The whole battery pack has, therefore, a nominal voltage of 11.1V, a fully discharged voltage of 9V, and a fully charged voltage of 12.6V. By adjusting the number of cells or by changing battery types, we can acquire many different voltage ranges. 

#### C-Rating
Another important characteristic of the used battery is its C Rating. It is the rating of current the battery can be charged or discharged at. A rating of 1C would imply that a battery with a rated energy of 1Ah could be charged and discharged with 1A of current. The same C rating with a rated energy of 0.5Ah could only be charged and discharged at 0.5A of current. In conclusion this means that the charge/discharge current can be calculated through the C rating and the rated energy of the battery, using the following formula:

$𝐼=𝐶_𝑟∗𝐸_𝑟$

𝐼 … Current of charge or discharge A
𝐶𝑟 … C Rating 1/h
𝐸𝑟 … Rated Energy Ah

The C-rating is another factor that we can selected when buying a battery. 

#### Connector
The last aspect of the batteries are the connector with which we can connect them to our board. All battery connectors are polar, which ensures that they are connected in the right polarity and adds reverse polarity protection. 

The three most common battery connectors are the:
- T-Plug
- EC3
- and the XT60, or XT30 plugs

The T-Plug is the most compact of the three. It can withstand a lot of current, although the other two plug types can withstand even more. 

The EC3 and XT plugs have a bigger form factor, which leads to a more secure attachment and a higher current handling capability. The XT plugs are available in different sizes, while the larger XT60 is used most often, and come even in a horizontal configuration. 

Most importantly, there are female and male connectors of all three plug types, while the battery most often features the female connector. So, when designing our board, we have to use male connectors of the correct type to fit our battery. 

#### Summary
When selecting the right battery, we must first decide on which battery type we want to use. 
There are three types that are best suited for model rocketry:
Li-Ion, Li-Po, and NiMH. 
Li-Ion and Li-Po have a nominal voltage of around 3.6V, have high energy density, high current discharge capabilities, but are dangerous if not used correctly. 
NiMH on the other hand have a voltage of around 1.2V, have a moderate energy density, and moderate current output capabilities, and are more robust, which makes them easier to use. 

The capacity of a battery states how much energy it can store and is given in Ampere times hours. In reality we can only use around 80% of the capacity, as we would otherwise deep-discharge the battery. 

The next factor when selecting the battery, is the cell number. A cell number of two means that two cells are put in series, which doubles the voltage and maintains the capacity. So, by selecting the cell number, we can select the voltage range at which our battery should operate. 

Then, there is the C-rating which states how much charge discharge current a battery can handle at a certain capacity. 

And finally, there are different battery connectors, such as the T-plug, EC3, and the XT plugs. Batteries most often feature the female plug, while we have to incorporate the male plug on our boards. 

## Level 2 - Voltage Regulation 
#### Linear Voltage Regulator
#### Switching Regulator
### Charging 


## Level 3 - Microcontroller Implementation
### Breakout vs on-PCB design
### ESP32
### STM32


## Level 4 - Sensors
### Breakout vs on-PCB design
### How to read a datasheet
### Gyroscope and Accelerometer
### Barometer
### Voltmeter


## Level 5 - Outputs

### RGB LED
### Buzzer
### Pyro Channels
### PWM for servo control



