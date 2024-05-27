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
## Level 3 - Battery Selection
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

## Level 4 - Voltage Regulation 
### Lecture 
Our power supply is primarily based on batteries. It's important to note that a battery's voltage varies across its charging state; for example, a LiPo battery's voltage ranges from 12.6V when fully charged to 11.1V when discharged. Additionally, many integrated circuits require a specific voltage, such as 3.3V, and other components, like servos, are uniformly controllable using 5V.

The job of a voltage regulator is to provide these exact voltages. Mostly, they convert an input voltage to a lower output voltage, and in some cases, they can even perform the inverse. We mainly categorize voltage regulators into linear regulators (LDOs) and switching regulators. However, there is an even simpler form known as the "Shunt Regulator."
#### Zener Diode 
To understand the simplest form of a voltage regulator, we must first recall the functional principle of a diode. A diode allows current to flow in one direction if a forward voltage, typically around 0.7V for a silicon diode, is applied. This forward voltage overcomes the depletion region. In the reverse direction, the diode normally blocks current flow, as the reverse voltage enlarges the depletion region of the diode.

However, we haven't yet discussed a special property of all diodes known as the breakdown voltage. While it's generally true that no current flows in reverse bias, this isn't entirely correct. Every diode can become conductive in its reverse direction if the applied reverse voltage exceeds a certain threshold, called the breakdown voltage. For standard diodes, the breakdown voltage is quite high, and reaching it causes immense currents to flow, which can permanently damage the diode.

There is, however, a special type of diode known as the Zener diode, which is designed to have a low and well-defined breakdown voltage, called the Zener voltage. When the Zener diode reaches this voltage in reverse bias, it becomes conductive without being permanently damaged. This unique property allows Zener diodes to be used effectively in voltage regulation applications.
#### Shunt Regulator 
We can use the Zener diode to create the simplest form of voltage regulators - the Shunt Regulator. To do so, we place a resistor in front of a Zener diode that is set in reverse-bias. On the left side, we have the input voltage. On the right side, we have a parallel load and the output voltage. The output voltage is determined by the Zener voltage.

Keep in mind that the Zener diode becomes conductive in reverse-bias if the applied voltage exceeds the Zener voltage. If only the Zener diode was present, an almost infinite current would flow. To prevent this from happening, we include a series resistor. The flowing current creates a voltage drop across the resistor, according to Ohm's law (𝑉=𝐼𝑅V=IR). The higher the current, the higher the voltage drop. If the current were too high, the voltage drop across the resistor would become excessive, and the voltage across the Zener diode would fall below the Zener voltage. Consequently, the flowing current reaches a balance with the voltage drop across the resistor, so the voltage across the Zener diode remains approximately at the Zener voltage. If the input voltage increases, the current flow increases, and the voltage drop across the series resistor increases as well. The Zener diode essentially clamps the output voltage to its Zener voltage.

The disadvantages of this regulator become apparent when examining the circuit:

- The resistor must be selected properly. It must be large enough to limit the current flow to prevent burning out the Zener diode, and it must be small enough to avoid causing too much voltage drop.
- If the output device draws high currents, the voltage drop across the resistor increases, which could result in too little voltage across the Zener diode, rendering it unable to clamp the voltage effectively.
- If no current is drawn by the load, current must still flow through the diode, making this type of regulator inefficient.

Consequently, the shunt regulator is best suited for applications with steady, small current flows. High currents could cause the regulator to provide insufficient voltage. In any case, this type of regulator is inefficient as it regulates the voltage by dissipating excess voltage as heat over the series resistor.

#### Linear Regulator
A more advanced form of a voltage regulator is the linear regulator. 
There are different forms of this regulator, however in its simplest form it regulates the voltage by controlling the resistance of a transistor based on the input voltage and the current draw. 

It its most basic form it consists of a NPN bipolar junction transistor (BJT). Its collector is connected to the input voltage and its emitter is collected the the output voltage. At the base we have Zener diode that is connected to the input side by a series resistor. This again creates a stable reference voltage at the base of the BJT. Additionally, the voltage drop from the base to the emitter is also always constant with around 0.7V. Therefore, the output voltage, is the Zener voltage minus the voltage drop across the base emitter. 

This voltage regulator design is beneficial, as the current does not have to flow over the series resistor but instead can flow through the transistor to the load. Through that it is more efficient, as we are not losing as much energy through heat. For the transistor to be able to limit the current flow, it has to operate in the active region, where the resistance across emitter collector varies with the current that is flowing through the base into the emitter. 

Linear regulators, require the input voltage to be higher than the output voltage. The input voltage has to at least higher than the output voltage by the dropout voltage. 
A special form of linear regulators, are the low dropout voltage regulators, so called LDOs. That compel by very low dropout voltages. 

A standard series of LDO's is the 78XX series. 
Such an LDO, integrate a circuit like this into single component. 
A component that houses many elements inside is called an integrated circuit. 

These kind of regulators take things a step further than the example that we discussed. 
- They incorporate thermal protection. 
- An internal voltage reference that is accurate over a large input voltage range and output current range. 
- They achieve very stable outputs. 
- And as mentioned earlier have a low drop out voltage. 

They can be bought in various forms, while the last two letters suggest the output voltage.
A 7805, for example, would create an output voltage of 5Vs. 
There, are also special forms that can create adjustable outputs, based on a resistor divider that is fed into the LDO. 

Linear regulators are commonly favored for their affordability, simplicity, and reliability, making them a popular choice for many applications. However, in scenarios requiring high currents and optimal efficiency, a superior alternative emerges: the switching regulator.

#### Switching Regulator
The switching regulator too steps down the voltage, but it also increases the current. Therefore, the output power is approximately equal to the input power. The converter achieves this internally by a circuit featuring a transistor, a capacitor, and an inductor. The transistor switches the input on and off repetitively. According to the current needed on the output of the converter the duration in which the transistor is turned on increases or decreases. A capacitor smoothens the voltage, while a inductor smoothens the current. As a result, the switch converter has a way higher power efficiency than a linear voltage regulator, often going above 90 percent.

Switching Regulators are divide into three sub-categories. 
The buck converters, the boost converters, and the buck-boost converters. 
A buck converter is a switching regulator take steps down the voltage and increases the current. So, it converts a high input voltage to a lower output voltage, as the one I described previously. 
The boost converter is exactly the opposite, it steps up the voltage while reducing the current. Through that a lower input voltage is converted to a higher output voltage. 
The final form is a buck-boost converter, which is an adjustable voltage regulator and able to do both. 

There are many switching regulators from numerous manufacturers. All of them come with different advantages and disadvantages. Let's look at just one of them. The buck-converter LM2596S-5.0. The “-5.0” represents the fixed voltage that the regulator outputs. 

##### Passive Components
As most switching regulator ICs, this one also includes all active components that are needed to create a buck converter. However, we have to provide the passive components on the outside, as they are too large to be incorporated into the IC. These components are: capacitors on the input and output, an inductor, and a diode. 

##### Switching Frequency
If we look at its datasheet we find something that is called the switching frequency. It determines the speed at which the voltage is switched on and off. For this one it is 150kHz which is faster than the 52kHz of the LM2576. The faster switching frequency, the smaller the passive components can be. Remember, that the inductor wants to maintain steady current while the capacitor wants to maintain steady voltage. Those change resistances are time dependent, which means that if the time is very fast even smaller components can achieve the smoothing. 

##### ESR
For the capacitor selection of a switching regulator, we have to look at the ESR (equivalent series resistance) of the capacitor. Ideally capacitors have no resistance, which would mean that an infinite current could flow when connecting a fully discharged capacitor to a voltage source. However, in reality every component has a series resistance, which we call the ESR.

If you recall the three main capacitor types, they feature very different typical resistance values: 
- MLCCs: <0.015Ω
- Aluminum Electrolytic Capacitors: 1 - 30Ω
- Tantalum Capacitors: 1 - 3Ω

##### RMS
Further there is the RMS (root mean square) current rating. The RMS current is the current flowing through the ESR (equal series resistance) of a capacitor causing a temperature rise of +10°C. It indicates the maximum continuous current that the capacitor can handle without exceeding its temperature limits. It's crucial for ensuring that the capacitor can withstand the current demands of the application without overheating. We should select capacitors with RMS current ratings that exceed the expected current levels to ensure reliability and longevity.


#### LM2596 Circuit Design
Now, back to the LM2596:
Let's set up a voltage regulation circuit that converts a LiPo battery voltage down to 5V. 
To do that we have to follow the “Application and Implementation” guide of the Texas Instruments LM2596 data sheet. 

We have the select the input capacitor, output capacitor, inductor, and diode accordingly. 

##### Input Capacitor
First, we have to determine a suitable input capacitor. The input capacitor provides the LM2596 with instantaneous current each time it is switched on. 
For its selection the RMS (root mean square) current rating, and the voltage rating are most significant. As we can read from the datasheet, the RMS rating should at least be ½ of the DC load current (3A), following a minimum RMS current of 1.5A. The input voltage for an aluminum electrolytic capacitor should be 1.5 times higher than the maximum supply voltage, in our case 12.6V. So, it should have a voltage rating of 18.9V. 

##### Output Capacitor
Secondly, it's crucial to evaluate the output capacitor in switching regulator circuits. The output capacitor serves two main purposes: filtering the output voltage and maintaining stability in the regulator loop. Its most critical design factor is its Equivalent Series Resistance (ESR). This parameter should ideally be kept as low as possible to minimize output ripple. However, it's important to strike a balance, ensuring that the ESR isn't too low, which could potentially destabilize the feedback loop.

In switching regulator circuits, where capacitors are commonly employed for filtering, the output ripple typically stems from the regulator's switching action, and is basically a slight periodic change in the output voltage. 

As a capacitor type we will select an electrolytic capacitor, as the assumed temperatures of this flight computer’s applications will be above -25°C. Below this temperature a tantalum
type capacitor would be preferable, as it is stated in the data sheet.

##### Inductor
Third, the inductor was selected. Following the guide in the TI data sheet, the
inductance needed is around 47μH. It also is stated that it is important to look
out for a proper core material of the inductor, as cheap core materials can cause
EMI (electromagnetic interference) in nearby PCB traces. Through a diagram in
the datasheet, the approximate inductor ripple current can be evaluated. This data
sheet is based on an input voltage range from 10 – 16V, and can, therefore, be
used in this case. The maximum inductor ripple current is equal to around
900mA at full load. And by using a formula included in the datasheet, the
maximum output voltage ripple can be calculated.

![](/assets/images/Pasted%20image%2020240526110222.png)

$Δ𝑈_{𝑂𝑈𝑇 }= Δ𝐼_{𝐼𝑁𝐷} ∗ 𝐸𝑆𝑅_{𝐶𝑜𝑢𝑡}$
$Δ𝑈_{𝑂𝑈𝑇}$ … Output ripple voltage [V]
$Δ𝐼_{𝐼𝑁𝐷}$ … Inductor ripple current [A]
$𝐸𝑆𝑅_{𝐶𝑜𝑢𝑡}$ … Equal serial resistance of the output capacitor [Ω]

This results in a voltage ripple of 0.9A* 0.094Ω = 84.6mV, which is acceptable.

##### Diode
The fourth component we have to lay out is the catch diode. This diode is needed to
provide the current with a way to flow back if the internal switch of the regulator
is turned off. This ensures that the energy stored in the inductor during the on phase of the regulator's switching cycle is safely discharged and utilized by the load. Essentially, the catch diode allows the circuit to maintain continuity of current flow and prevent any abrupt changes or disruptions in the power delivery process. This diode has to work extremely fast and should have a minimal voltage drop. The ideal type of this diode is, therefore, a Schottky diode. Schottky diodes are known for their low amount of voltage that must be applied in forward bias to make them conductive. The diode chosen must also withstand the maximum current of 3A.

##### On/Off Functionality
The flight computer features a designated on/off pin. Normally a switch would be interposed in one of the connections to the battery. This would mean that the switch itself must withstand a current as high as 3A, making the PCB heavier and more expensive. By using this on/off pin, only very little current is needed to turn/off and on the entire flight computer. Therefore, the currents the switch must withstand shrink massively. 

Additionally, a red LED is added to visualize the power state of the 5V line. This results in the final schematic for the 5V power regulation.

#### Summary
So there are many ways in which we can convert an input voltage, such as a LiPo battery voltage to a defined output voltage. 

The easiest way would be by using a Zener diode and a resistor, which we call a Shunt Regulator. Conversely, this type can only be used in continuous current applications with low currents, as the current always has to flow over the series resistor, which dissipates the excess voltage as heat. This process is extremely inefficient. 

Another way would be by using a linear regulator, which uses a transistor in its active region to restrict current flow. Here, larger currents can flow as the current doesn't have to flow over a series resistor. Further, variable current draws can also be conveniently managed with this type of regulator. However, the transistor itself provides some resistance, and due to that energy loss through heat, which also makes this type of regulator limited to a current supply of several amps and to moderate efficiencies.

Finally, there are switching regulators that while changing the voltage also change the current. Through that the net power the regulator delivers remains constant. This is achieved by turning on and off the input power supply, and then smoothing the signal with a capacitor and an inductor to provide a stable output voltage. There are three forms. The buck converters that step down voltage, the boost converters that step up voltage, and the buck-boost converters that can do both. 

When designing a switching regulator circuit, we have to provide the passive components as they do not fit into a integrated circuit. When selecting the capacitors we have to watch out for their ESR, their RMS ratings, and the voltages they can withstand. For the inductor and diode we have to consider their allowed currents. 

### Examples
Zener Diode
Shunt Regulator 
L7805
LM2596

## Level - Microcontroller Implementation
### Lecture
#### Microcontroller 1x1s 
As mentioned before, we can think of a microcontroller to be a mini computer. Compared to a real-computer, it comprises all the relevant parts in a single package, such as the processing cores, the program memory, and the input/output peripherals. 

##### Power
For a microcontroller to function, it has to be provided with power. Most microcontrollers use a 3.3V input voltage, and feature several pins to which we will have to provide power to. 

##### GPIO Pins
The first term we have to coin is GPIO, which stands for "General Purpose Input Output" pins. Every microcontroller has some of these pins. We can set them to either function as an input or an output pin. We use input pins to, for example, read out a temperature sensor or the state of a button. On the other hand, we use output pins to control motors, lights, speakers, and much more.

A GPIO pin is a digital pin, which means that it can either be in a high (1) or low (2) state. The state of the GPIO pin refers to the voltage that is present at the pin. For microcontrollers that are powered with 3.3V, most microcontrollers would define a low-state below a voltage of 1.2V, while they would define a high-state above a voltage of 1.8V. In-between those two values, the state of the pin couldn't be clearly identified, and is in some sort of gray zone. Every input pin has also an upper threshold, above which it would be permanently damaged. A standard upper threshold would be around 5V. 

##### Pull Ups / Pull Downs 
With a GPIO input pin, we could easily read out a button by attaching 3.3V to the button on one side and the input pin on the other side. The microcontroller measures the voltage at the pin, just as we do with the multimeter. If the button is pressed 3.3V are present. However, if it is not pressed the pin is not connected to any voltage level, which means the voltage level is undefined. We call this condition a floating pin. 

Floating pins are tricky, as their high/low state is not clearly defined. The slightest induction at the pin could change the voltage at the pin, and create a false high state. This could, for instance, happen if someone accidentally touches the pin. Therefore, we have to avoid pins is this state as much as possible. We have to define the off-state of the button, as low. Ideally the pin should measure a voltage of 0V or GND, while being off. 
To do so, we connect the pin to ground via a resistor. This is called a pull-down resistor, as it pulls down the voltage level of the input pin to ground. Now, the pin clearly measures 0V when turned on. 

But what happens when the pin is pressed? Well, now the 3.3V are connected to GND via the pull-down resistor. We can think of the button as having a very small resistance that is almost zero. The pull up resistor, on the other hand, has typical values from a few hundred Ohms all the way up to thousands Ohm. If we now calculate the equivalent resistance, it is approximately the same as the pull-down resistor. And if we divide the voltage of 3.3V by the pull-down resistor, we get the flowing current. Multiplying the flowing current with the two resistors results, in a voltage drop across the button of around 0V and across the pull-down resistor of around 3.3V. This means that the measured voltage at the pin is 3.3V. Through that, we have defined the pressed and unpressed state of the button effectively. 

We could create a similar logic by connecting the button to ground, and using a pull up resistor with which we would connect the input pin to 3.3V. The pull up resistor pulls up the voltage. If we now pressed the button the input logic level would be low. The equivalent resistance is again approximately the same as the pull up resistor, which results in a voltage drop of 3.3V across the pull-up and around zero across the button. Consequently, the input pin would measure a voltage of around 0V.  

##### Analog Input
Okay, so we are able to read out a button. But what if we wanted to determine the temperature in a room? 

For that we could use a temperature dependent resistor, which consists of a material that changes its resistance based on its temperature. By creating a voltage divider, that consists of one temperature dependent resistor, and one non dependent resistor, and connecting them to 3.3V, we can measure a changing voltage based on the temperature of the room. 

However, the a GPIO input only determines high and low states at it is a digital pin. 

##### Interrupt

##### PWM
##### I2C
##### SPI


##### Timers

##### Clock Frequency

##### Breakout vs on-PCB design
##### Programming


#### ESP32


#### STM32



## Level - Sensors
### Breakout vs on-PCB design
### How to read a datasheet
### Gyroscope and Accelerometer
### Barometer
### Voltmeter


## Level - Outputs

### RGB LED
### Buzzer
### Pyro Channels
### PWM for servo control
#### Example
Oscilloscope for PWM analysis 



