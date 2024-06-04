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

## Level 5 - Microcontroller Basics
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

#### Memory
Another aspect of microcontrollers are its memory sources. 
The three most essential ones are: Flash memory, RAM, and EEPROM.

Each of them usually serves a specific purpose. 
The flash memory is where the microcontroller firmware and program are stored. 
The EEPROM stores small amounts of information that last over many power cycles, such as configuration settings and calibration data.
Finally, the RAM memory is used for temporal data storage and manipulation while the microcontroller is running. For example to store variables and buffers. 
##### Flash
Flash memory is a non-volatile memory, which means that the information is retained even after power is turned off. Each flash memory chip consists of several blocks, which are further divided into pages. These pages consist of multiple floating-gate MOSFETs that can store either a zero or a one. Flash memory is a type of electrically erasable and programmable read-only memory (EEPROM). As its name suggests, we can erase stored data, program new data, and read data. However, programming data is not possible for single bits; instead, we must erase and program entire blocks of the flash memory.

Flash memories have a limited life-cycle, meaning we cannot continuously erase and program data onto them indefinitely, as the floating-gate MOSFETs would degrade over time. This limited write/erase cycle is a crucial consideration for their use.

These characteristics define flash memory's use cases, such as storing firmware or software. These types of data do not require frequent erasing and programming, typically only a few hundred times at maximum over the device's lifetime.

##### EEPROM
Even though the Flash memory is a type of EEPROM, it is common to treat Flash memories and EEPROMs as two distinct types of memory in microcontrollers as they both come with different use cases. 

Similarly to the Flash memory, the EEPROM is also non-volatile and doesn't loose information upon shut-down. The first difference is that each byte of the EEPROM is individually programmable and doesn't require the user to erase an entire block. The disadvantage of this individualistic access is a lower reading and writing speed, as well as a smaller memory density. However, EEPROMs come with the additional advantage of enduring more erase/program cycles. 

Out of those characteristics, it makes sense that the EEPROM is used to store data that must remain on the device after power-down but will be changed often. Examples for that would be the storage of configurations settings, user preferences, and calibration data. 

##### RAM
The last type of memory that we will discuss is the random access memory or RAM. Compared to the other two memory sources it is volatile, which means that its data is lost after power down. RAM is called "random access" because any memory location can be accessed directly, regardless of its location in the memory hierarchy. Its smallest units are either capacitors (Dynamic RAM) or flip-flops (Static RAM). These components allow for even faster read/write speeds than floating-gate MOSFETs. 

Due to the very fast read/write speeds and the fact that its data storage is only temporary, the RAM's use cases are to provide the central processing unit (CPU) with data that it needs to quickly access while program execution. 

#### Programming
Programming a microcontroller typically involves a bootloader, which is a small program pre-installed in the microcontroller's memory. When the microcontroller is powered on, it first runs the bootloader. During this limited time, the bootloader waits for communication from the PC. The PC can signal to the bootloader that it wants to upload new code, a process often done via UART. 

If the PC sends a request to upload code, the bootloader receives the new program data and writes it to the appropriate memory location in the microcontroller. The bootloader ensures that the new program is correctly received and stored. 

If no new code is uploaded during the bootloader period, the microcontroller proceeds to execute the previously stored program. This fallback mechanism means that if the bootloader does not receive a communication signal from the PC within the specified time window, it defaults to running the existing program in memory.

During a limited time after power-up, the bootloader waits for communication from the PC. If new code is uploaded, it replaces the existing program; otherwise, the microcontroller executes the current program in memory. This process allows for easy updates and reprogramming of the microcontroller.

#### Summary
A microcontroller is a mini-computer that integrates all necessary components, such as memory, a processor, and peripherals, into a single package, typically powered by 3.3V. It features GPIO (general-purpose input and output) pins. When set as input, they read the voltage to determine whether it corresponds to a digital high (>1.8V) or a digital low (<1.2V). When set as output, they can either be high (3.3V) or low (0V).

To read a value between high and low, an analog input pin is used. This pin measures the voltage like a multimeter and translates the value into a numeric number via an ADC (analog-to-digital converter).

For outputting a voltage between high and low, pulse width modulation (PWM) is used. In PWM, the output pin is turned on and off repetitively. The ratio between the on-time and the total time is called the duty cycle. A capacitor can be used to smooth out the resulting voltage.

Every microcontroller has an internal or external clock that times all operations, such as PWM signals, timing, and communication protocols. The speed at which the oscillator runs, combined with the CPU multiplier, determines the microcontroller's clock speed, which gives a rough idea of its performance.

Input pins can also be used as interrupts. Interrupts disrupt the microcontroller's current program execution to run an interrupt service routine (ISR). They are useful for waking up a microcontroller from low-power sleep modes.

Microcontrollers communicate with other devices through various protocols. I2C (Inter-Integrated Circuit) uses two wires: SCL (serial clock line) and SDA (serial data line). It features a master and one or more slaves. The master addresses the slave it wants to communicate with and provides the clock signal. I2C is a relatively slow but easy-to-use protocol, often implemented in sensors.

SPI (Serial Peripheral Interface) requires four wires: SCK (serial clock), CS (chip select), MOSI (master out slave in), and MISO (master in slave out). SPI allows full-duplex communication, enabling both the master and the slave to communicate simultaneously without the need for address transmission.

UART (Universal Asynchronous Receiver Transmitter) is another communication protocol used for serial communication between two devices, typically a microcontroller and a PC. It uses two lines: RX (receive) and TX (transmit), and operates at a predefined baud rate. UART is straightforward but limited to point-to-point communication without a master-slave hierarchy.

PCs upload code to the microcontroller via the UART protocol. Upon power-up, the bootloader waits for a limited time for communication from the PC. The bootloader mechanism ensures that new code can be uploaded to the microcontroller efficiently and reliably. If new code is uploaded, it replaces the existing program; otherwise, the microcontroller runs the current program in memory.
#### Examples
Input - Button + Pull-down 
Input - Temperature measurement + ADC
Output - LED + diming LED (oscilloscope)
Temperature Measuring Device with Button - with Interrupt 

## Level 6 - Specific Microcontrollers
### Lecture
Now, with all the microcontroller basics out of the way, let's look at three specific microcontroller examples. But before we do so, let's talk about breakout boards and on-PCB design.
#### Breakout vs Embedded Microcontroller
We can implement a microcontroller into our flight computer in one of three ways. 

The first way would be to use a third-party breakout board. Breakout boards are ready to use microcontrollers, where all the necessary components are already pre installed. The breakout board most often features a voltage regulator which provides the exact 3.3V needed, has an integrated crystal oscillator which provides the microcontroller with accurate timing, and incorporates a chip (a USB to UART bridge) for proper communication between the PC and microcontroller. Further, it features a pin header for easy access of the microcontroller pins and has the bootloader pre-installed. 
This implementation is easiest, as those breakout boards can be used out of the box. An Arduino Uno, an ESP32 Dev Module, or a Teensy, would all be examples of such breakout boards. The processor that they incorporate are from different companies. An Arduino Uno, for example, features an ATMEGA16 microcontroller. The disadvantage is the increased weight, as we have an additional PCB, and pin rows. Further, it is not as reliable as the connection between the pins could be error prone. However, it is very beginner friendly, and if we came to just damage the microcontroller it could be replaced more easily. 

The second way would be by using a so called module. A famous example is the ESP32-Wroom module, which we will look at. This module can be directly implemented on our own PCB and spares as a few steps compared with a full microcontroller implementation. Such a module internally features a crystal for timing, has a pre-installed bootloader, has extra FLASH memory, and a Bluetooth antenna. In this case we only have to be concerned with the USB to UART bridge, for programming, and the power management of the microcontroller. 

The final way would be an onto the PCB embedded microcontroller. In this case we have to do all the implementation ourselves. We have to select a proper crystal, have to establish the USB to UART bridge, provide proper power management, and sometimes have to install the Bootloader. Additional functionalities like Bluetooth and WIFI, must also be implemented by us, which requires antenna design and RF matching. We will look at this kind of implementation by using an STM32 microcontroller. This method allows us to adjust our design to our needs to the maximum degree, and results in the most lightweight PCBs, as we can decide which features we want to incorporate and which we want to exclude. 

#### Teensy 4.1
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

#### ESP32
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

#### STM32
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
## Level 7 - Sensors
### Lecture
Sensors are our sensory organs of our flight computer. With the help of them we can determine our rocket's orientation, its acceleration, velocity, and position, as well as its altitude. 
Based on the input of our sensors, our rocket can make informed decisions about steering the engines, deployment mechanisms, or aborting the flight. Further, they help us to analyze our rocket flights by storing their data. 

We will discuss the four most vital ones for model rocketry: 
the gyroscope, the accelerometer, the barometer, and the voltmeter. 
At the end we will briefly talk about other sensors that could be beneficial for your projects. 
#### Gyroscope
The first and most important sensor for advanced model rockets is the gyroscope. It is the main sensor with which we are able to determine the orientation of our vehicle. 

##### Function Principle
The gyroscope determines the angular rate based on the Coriolis effect. The Coriolis effect dictates that when a mass is set in motion within a rotating reference frame that a force arises perpendicular to both the mass's direction of motion and the rotation axis of the frame. This force, known as the Coriolis force, induces a distinct displacement or deflection in the moving mass. 

The gyroscope has an oscillating mass inside that moves along a predefined axis. Now if this component is rotated, we have a rotating frame of reference, which results in a displacement of the mass that is caused by the Coriolis force. This displacement changes the capacitance between two plates and this capacitance change is measured and then translated into a rotation change - the angular rate. 

##### Determining Orientation
For determining the rocket's orientation we need a total of three gyroscopes each along a different axis in the coordinate system. One that measures angular rate around the pitch, one 
around the yaw, and one around the roll axis. 

To now determine the orientation of the vehicle, we take this orientation change multiply it by the elapsed time and add it to the previous orientation value. We basically integrate the angular rate to get an absolute orientation. However this works only if we rotated the rocket about one axis. As we have three-dimensional orientations we have to use a 3D rotation representation, such as Euler angles, or Quaternions. These concepts are further discussed in the software path.

##### Parameters
Here we will focus more on the gyroscope itself. 
When looking at the datasheet, the following properties are mostly given. You should understand in order to be able to select the gyroscope that fits your project best. 

First, the operating range gives the maximum angular rate the gyroscope can measure. An operating range from +-2000°/s would mean that it can't record any faster rotations than that. 

A second property of the gyroscope, is its resolution given in bits. A 16-bit gyroscope would divide the entire angular rate range into 2^16 values. 

Resolution shall not be confused with accuracy. A higher resolution does not necessarily mean more accuracy. It simply means that we are given more digits to work with. But, whether or not the value is correct is only dependent on the accuracy. 

Accuracy ratings are mostly not given directly in a gyroscope datasheet, as they are dependent on multiple factors. Rather, the data sheet provides several parameters that indirectly represent the gyroscopes accuracy. 

One of the factors affecting the accuracy of a gyroscope is the temperature coefficient of offset (TCO), which describes how the measured angular rate changes with temperature. A TCO of ±0.015 °/s/K means that for each degree Kelvin (or Celsius) increase in temperature, the gyroscope's measured angular rate can become inaccurate by ±0.015 °/s. This means that as the temperature changes, the bias or zero-rate output of the gyroscope can drift, leading to inaccuracies in the angular rate measurement.

The second factor is the zero-rate offset, which describes the static error a gyroscope has when it is not rotating. Most gyroscopes come with an offset in angular rate from the factory. An offset of ±1°/s means that the gyroscope's reading can be off by 1°/s from the actual angular rate even when it is stationary. This offset is constant and can be calibrated out or compensated for when determining orientation.

This is a measure of the random noise in the gyroscope's output. The smaller the noise density, the smaller the angular rates we will be able to detect. A value of 0.014 °/s/√Hz means that the gyroscope has a noise level of 0.014 °/s for each square root of the bandwidth in Hertz. This low noise density allows for more precise detection of small angular rate changes, improving the overall accuracy of the measurements.

So, the gyroscope's accuracy is largely determined by the Zero-offset, the TCO, and the noise density. 

To read the data from a gyroscope using a microcontroller, gyroscopes often come with bus connections like SPI or I2C. Additionally, they frequently feature interrupt pins that indicate to the microcontroller when new data is ready. An interrupt for new readings of the angular rate is especially important because the microcontroller needs to integrate the new data as soon as possible.

Remember, the microcontroller calculates the change in orientation by multiplying the angular rate change by the elapsed time. If the elapsed time is not correct, the determined angle would become inaccurate over time. Therefore, timely data integration is crucial for maintaining accurate orientation tracking.

Another property of a gyroscope is its ODR output data rate. It often can be selected and gives the number of data sets that the sensor outputs per second in Hz. 

A major disadvantage of the orientation determined by the gyroscope is that it isn't a direct measurement but the integral of the angular rate. This means that a slight error in the angular rate results in an offset in the orientation. If the slight error in angular rate is single-sided, the orientation result drifts from the real orientation over time. 

##### Calibration
A zero-offset and the TCO alone would, therefore, cause the orientation readings to become inaccurate in no time. This is why gyroscopes are calibrated before use. Basically, the gyroscope is sitting still and the angular rates are measured and averaged. In ideal circumstances the angular rate should be zero if the gyroscope is static. The measured average is subtracted from the angular rate. If the test is conducted again, the gyroscope's angular rate reading in a static condition will be approximately zero. Unfortunately, it is not possible to completely eliminate drift. Depending on the gyroscope's characteristics, there is a certain limit to how far we can go with calibration. With good calibration, a good orientation accuracy of several minutes can be achieved reasonably. 

#### Accelerometer
Another way though for rockets not as important way to determine orientation is by the means of an accelerometer. It measures the total acceleration acting on the sensors internal mass.

##### Function Principle
Every mass has a moment of inertia. If a mass is moving its moment of inertia resists change in speed, similarly to how a capacitor resists change in voltage or an inductor resists change in current. If a mass is accelerated or decelerated, the mass experiences a force in the opposite direction - the inertia force. An accelerometer takes advantage of this principle. Within the component there is a mass that can freely move along one axis. In case of accelerations, its moment of inertia resists change and the inertia force displaces the mass from the center. Again, the displacement is measured by the capacitance, and then the displacement is converted to an acceleration. 

##### Determining Orientation
For determining the orientation of the vehicle, we have to use an 3-axis accelerometer. Now if the rocket sits at the launchpad, the only acceleration that is present is Earth's gravitational acceleration. If the rocket would be perfectly upright, the entire gravitational acceleration would be measurable in one axis only. However, if it is not we would get parts of the total gravitational acceleration in two axis of the sensor. Simply put, by knowing the ratios between those parts, we can determine the orientation of the rocket. 

The problem with accelerometer arises while powered ascent. The rocket engine provides thrust that is higher than the gravitational acceleration in order to accelerate the vehicle and to make it lift off. The gravitational acceleration always points downwards to Earth's center from the rocket's COG. The acceleration by the engine's thrust, on the other hand is in-line with rocket engine that sits inside the thrust vector control mount. Consequently, the resulting acceleration of the two becomes highly unpredictable, as it depends on the orientation of the vehicle, on the thrust of the engine, and the angle of the thrust vector control system. As the total orientation isn't pointing to the Earth's center anymore, we have no way of determining the orientation based on these measurements in flight. Further, even if we could the accelerations are also caused by vibrations that are also present during rocket flight. 

You may wonder why drones are able to used an accelerometer for determining orientation. But that is simple. When drones are hovering, they experience almost no acceleration, and when they are moving, their accelerations are still comparably low. This makes it easy for drones to use accelerometers. 


##### Parameters
Accelerometer's datasheets feature the exact same kinds of parameters 
There's the operating range, which is this time given in g. A rating of +-3g would mean that it could measure an acceleration of approximately 3 times of Earth's gravitational acceleration -around 3x9.81m/s^2. The resolution is also given in bits, and splits the operating range into values. 

The accuracy also heavily depends, on the zero-offset given in mg/K, the TCO given in mg/°/K, and the noise density in μg/√Hz.

Accelerometer are also interfaced by common protocol such as I2C and SPI, and too feature interrupt pins. Even their output data rates are comparable. 

#### BMI088 Implementation
Both ways of determining orientation come with their own sacrifice. 
Gyroscopes tend to drift over time due to their indirect nature, while accelerometers are prone to vibrations and are difficult to use while powered ascent. 

Drones are able to use accelerometers to determine orientation as they do not have those high accelerations that are present in rocket flight. However, they still use both types of sensors and fuse them in order to get the most accurate results. They use the accelerometer data to correct the gyroscope drift, while filtering out the noise from the accelerometers. The two sensors perfectly complement each other for drone applications. 

Therefore, gyroscopes and accelerometers are often sold within a single package. 
Now, let's look at such a sensor packet or IMU (inertial measurement unit) the BMI088 from Bosch. 

##### The Sensor
The BMI088 is a 6DOF sensor, which stands for six degrees of freedom. The term DOF refers to the number of measured axis. It features a tri-axial gyroscope, and a tri-axial accelerometer. 

Both have a digital resolution of 16-bit. The accelerometer is able to output data in steps of  0.09mg, while the gyroscope gives its readings in steps of 0.004°/s. 

For this sensor the operating ranges for both the accelerometer and the gyroscope can be selected. The accelerometer's setting range from +-3g all the way up to +-24g. For model rocketry, we will rather chose a lower g setting, as we do not expect that high accelerations. 
The gyroscope's setting range from +-125°/s to +-2000°/s. 

The zero-offset for the accelerometer is +-20mg, and for the gyroscope +-1°/s.
The TCO is +-20mg for the accelerometer, and +-0.015°/s/K for the gyroscope.
The noise density is 175 μg/√Hz for the accelerometer and 0.014 °/s/√Hz for the gyroscope. 
We can also adjust the output data rate of the BMI088 and select anything between 12.5Hz to 2kHz. 

The BMI088 allows for SPI and I2C interface and features a total of four interrupt pins. 

Its high resolution, low noise, wide operating range, and flexibility in output data rate make it capable of providing precise and reliable motion data for accurate control algorithms.
##### Datasheet
To implement the BMI088 into our flight computer we have to turn to its datasheet. Don't be overwhelmed by the amount of information provided in such as document. To integrate this sensor we do not have to understand the entire 62 pages. Often the maximum ratings, and the pin-out and configuration diagram are enough to be able to implement the sensors. 

If we turn to page 52, we can see which functions are taken on by which pins. Pin one, for example, is the second interrupt pin of the accelerometer. Pin 3, is one the supply voltage pins, and so on. On page 53, we see typical connection diagrams for their sensors. As you can see, we can either connect the BMI088 by SPI or I2C. I usually like to connect sensors by SPI, due to the faster communication speeds. 
##### Power Supply
To hook up the BMI088, we have to connect +3.3V to all VDD and the VDDIO pin. Further, we have to connect the GND and GNDIO to 0V or GND.
The PS pin (protocol select pin) is needed to indicate via which bus protocol our microcontroller wants to communicate with the sensor. By pulling it low, SPI is selected, and by pulling it high I2C is selected. 

As recommended in the datasheet the NC should also be connected to ground to omit floating pins. To provide stable input voltage for the IC, we should add two 100nF capacitors as close as possible to the VDD pins of the BMI088. 

For my designs, I like to add another two bigger 10uF capacitors, to counteract the ripple voltage of our power supply. 
##### SPI Connection
Because you understand the SPI protocol it is straight forward how to connect the interface:
- SCK to SCK, 
- MOSI to sensor data in (SDI)

Even though, both the accelerometer and the gyroscope sit in a combined housing, we could use both of them on their own. This is why there are even two distinct sensor data out pins (SDO1 and SDO2) on the sensor. As only one of them can communicate at at time it is perfectly reasonable to connect both of them to the same MISO. 

To tell the sensor whether the accelerometer or the gyroscope is currently addressed, we have two different chip select pins which we have to add. 
##### Interrupts
Regarding interrupts there are different modes in which this sensor can operate. 
Both the accelerometer and the gyroscope feature two interrupt pins each. 
For each, one can be selected to be a new data ready interrupt, which means that the sensor would indicate that new data can be read out by changing the voltage on this pin. 
This results in one interrupt for the accelerometer and one interrupt for the gyroscope. In this case, the accelerometer and gyroscope data would not be outputted at the same time, but on their own speeds and timings. 

However, there is a way of synchronizing the data of the gyroscope and the accelerometer. In that case one interrupt pin would be sufficient, which fires as soon as both the gyroscope and the accelerometer are ready to provide new data. 

Another operating mode, is the FIFO (first in first out) mode. In this mode the IMU stores the gyroscope and accelerometer values into a Buffer with timestamps, which allows the microcontroller to still receive time-correct data, while not disrupting the microcontroller continuously. In this case one of the interrupts each, could be configurated to indicate a full or almost full buffer. Further INT1 and INT3 could be used as inputs. When applying a high to these pins, the sensor would tag those specific data sets. 

We usually, just use the first method with two new-data interrupts, as we depend on the real-time data of the gyroscope. For us the main advantage of having access to four interrupt pins is that we can chose either one of the two for both sensors that suits are wiring best. 

#### Barometer
When launching a rocket, we also want to know the altitude that we reached. To do so, there are different ways, but most commonly the altitude of a model rocket flight is determined by a barometer. This is also the common way in which drones determine their height. 

A barometer measures the air pressure, as well as the air temperature.

As altitude increases, the atmospheric pressure decreases. This relationship is due to the weight of the air above a given point in the atmosphere. The higher you go in altitude, the less air there is above you, resulting in lower atmospheric pressure. This is why barometric pressure is often used as an indirect measure of altitude.

In most cases, an increase in temperature results in an increase in atmospheric pressure, assuming all other factors remain constant. This relationship is primarily due to the fact that warmer air molecules have higher kinetic energy, causing them to move more vigorously and exert more force per unit area on surfaces.

By knowing both characteristics of the air, it is possible to determine an approximate altitude by the barometric pressure equation. 

The barometer measures the air pressure, by a membrane inside the IC that deforms under applied pressure. Through the deformation of the membrane, the resistance of the membrane changes. The single resistances of the single strain gauges are connected in a diamond-shaped configuration, which is in balance without deformation. As soon, as the membrane is deformed, the resistance imbalance creates a electrically measurable derivation. This derivation is then used to be converted into pressure readings. It's important for the barometer IC to have direct access to the surrounding air, hence it is typically placed near an air inlet of the rocket for accurate pressure measurements.

In reality these measurements, are additionally influenced by air humidity (as humidity changes air density), diurnal pressure variations, as well as high and low pressure zones that occur because of weather conditions. The absolute altitude readings are therefore only within a few tens of meters. However, if the environmental conditions remain relatively constant during test operations, a relative accuracy, which is more important to determine the reached altitude, can be as accurate as +-0.5m. 

These changes in environmental conditions and the resulting inaccuracies can't be changed by highest precision barometric pressure sensor. 

Typical parameters that will be given when selecting a barometer are:
- the operation range which gives you the pressure range in hPa your barometer will be able to measure. Air pressure ranges from 1013 hPa at seal level to 56hPa at 65km altitude. 
- the absolute pressure accuracy, gives the pressure derivation from the actual pressure at a certain sea level. It is most important if we would want to determine the absolute altitude of any point. 
- the relative pressure accuracy, outlines the inaccuracy for applications in which we want to determine the pressure change. It is most important to determine altitude during model rocket flight. 
- the noise in pressure, gives the amplitude of random fluctuations in our measurement. 
- the temperature coefficient offset (TCO), clarifies the change in measured pressure based on increased or decreased heat of the sensor. 
- the long term stability (12 months), indicates the change in measured pressure over an extensive time period. We can think of this measurement to be a long term drift. 
- sampling rate, is the same as the output data rate on the IMUs. 

Now, let's look at a specific example of a barometer the BMP388 from Bosch. 
#### BMP388 Implementation
##### Properties
The BMP388 incorporates both a pressure and a temperature sensor, as is common for barometers. When looking at its datasheet again we are able to evaluate the sensor's properties. 

It has a operation range that ranges from 300 to 1250 hPa, which is more than enough to cover our altitude range. Its absolute pressure accuracy is +-0.5hPa, which we could translates to a meters above sea level measurement with an accuracy of +-4m. The relative pressure accuracy is +-0.08hPa, which translates to an altitude measurement relative to a setpoint with an accuracy of +-0.66m. The setpoint will in our case almost always be at the level of the launchpad. This makes the relative accuracy most important to determine the altitude, or change in elevation. 

The BMP388 has a noise in pressure at lowest bandwidth and highest resolution of only 0.03Pa. 
Its TCO is +-0.75Pa/K and its long-term values over a 12 month period are still within +-0.33hPa. 
All of that with a maximum sampling rate of 200 Hz. 

The BMP388 allows for the classic 4-wire SPI, and a special SPI interface that only needs three wires. Further, it features an I2C interface and an interrupt pin. 
##### Oversampling and IIR
The BMP388 is able to run different oversampling modes (from none to 32 times oversampling) and can apply an IIR (infinite impulse response) filter (ranging again from none to 32).   
Oversampling improves the accuracy and resolution of measurements by sampling the input signal more frequently and then averaging these samples. The oversampling rate is adjustable and can be set to different. The higher the oversampling rate, the higher the resolution, the higher the power consumption and the higher the resolution. However, as more samples are combined in a single measurement, the output data rate decreases with increasing oversampling. 

The IIR filter helps in smoothing the output data by reducing short-term fluctuations and noise, providing a more stable reading. The filter coefficient can also be set from zero to 32 and determines the strength of the filtering, with higher coefficients providing more smoothing. Stronger IIR filtering provides smoother data but may introduce a slight lag in response to rapid changes in pressure or temperature.

We can set both the oversampling and the IIR individually for both the pressure and the temperature sensor. 

##### Power Supply
The sensor is supplied with regulated 3.3V and is equipped with bypass capacitors on the power inputs to make the power supply more stable. Their capacitance is recommended to be 100nF, and the type should be of a SMD ceramic capacitor. 

##### SPI Connection and Interrupt 
The BMP388 will be implemented using the four-wire SPI interface, similar to the BMI088:
- **SCK to SCK**
- **MOSI to SDI**
- **MISO to SDO**
- **GPIO to CS**
Additionally, another GPIO pin will be connected to the interrupt pin to indicate when new data is ready.

#### Voltmeter
Another very useful sensor for model rocketry is the voltmeter. The voltmeter is intended to measure the battery's voltage level to ensure a sufficient power supply.

There are many way in which we can measure a the voltage of our LiPo battery.
There are dedicated battery monitoring ICs available that provide protection against overvoltage, undervoltage, overcurrent, short-circuits, and even overtemperature. 
There are even battery fuel gauge ICs that do not only determine the battery's voltage but also its stored capacity. 
However, there is a simpler way of roughly determining the battery's voltage level, which is done  by using a voltage divider in combination with an ADC. 

#### Voltage Divider with ADC
All of the three microcontrollers we previously discussed, have their own analog input pins. Most often they work by an integrated analog to digital converter. However, the analog input pins of our microcontrollers only function in a range of 0 to 3.3V. If we were to apply a higher voltage to the pins, they would undergo permanent damage. Our 3 celled LiPo battery has a voltage range of 11.1V to 12.6V, which is magnitudes to high for the ADC to measure. 

However, there is a way to indirectly measure the battery's voltage level without damaging the ADC. This is done by a voltage divider. A voltage divider is basically a resistor circuit that consists of two resistors put in series. To this divider the battery voltage is applied. Now we can calculate the equivalent serial resistance, and divide the entire voltage by this value. What we get is the flowing current. By multiplying the current with the resistances, we get the voltage drop across the two resistors. The voltage drop across the resistors varies with the current, which again varies with the applied voltage. By selecting the correct resistor value, we can create a voltage of 0 to 3.3V for the input range of 0 to 12.6V across the bottom resistor to which we connect the ADC. 

##### Implementation of ADC Voltmeter
So, let's device our first ADC voltmeter.
First, we have to determine the input voltage range which we want to be able to measure. 
Ideally, we would use a larger range, in our case we could go with 0-13.3V. 
Then, we have to think about the lower voltage range that should be present at our ADC. 
In this case of our microcontrollers our ADCs withstand around 3.3V. So, let's go with a lower voltage range of 0-1.88V. So, the battery voltage of 13.3V corresponds to the at the ADC measured voltage of 1.88V. 

The next step is to select one resistor, based on which we then can calculate the second resistor. 
It is important to know that the higher the resistance value we chose, the lower the continuous current consumption will be. A good value for the upper resistor could be 20kOhms for example. 

We can calculate the voltage across the second resistor by determining the current times the second resistor. 
$V_{ADC}=\dfrac{V_{BAT}*R_2}{R_1 + R_2}$

Then, we can insert our maximum values, which are 13.3V for Vbat and 1.88V for the VADC, and the value for our first resistor. 
$1.88V*20000Ω = 13.3V*R_2 - 1.88V*R_2$

After that we only have to extract R2 to one side, and evaluate its resistance. 
$R_2 =\dfrac{1.88V*20000Ω}{13.3V-1.88V}=3292Ω$

Now we have an ideal resistor value, with which we can now select an appropriate one. The next closest available is a 3.3kΩ resistor. 
By calculating the network again with this resistor we come to the conclusion that 13.3V correspond to 1.8836V. 
As you know the value of the measured voltage range is given in a number. For a 12-bit ADC, a value of 4095 would correspond to the voltage level 3.3V.

What battery voltage would correspond to 3.3V at the ADC? 
Let's determine the current by 3.3V/3300Ω=0.001A 
Then multiplied by the equivalent resistance we would 23.3kΩ * 0.001A = 23.3V. 
So, 3.3V at the ADC correspond to a battery voltage of 23.3V.

Therefore, we can calculate the battery voltage by dividing the numeric number x by the maximum number 4095. We know that the maximum number corresponds to 23.3V and that the relationship between X and the maximum number is linear. 

$V_{BAT} = \dfrac{n_{ADC}}{4095}*23.3V$

However, keep in mind that both resistors are not ideal and do have a slight offset of their ideal resistance. Consequently, we have to calibrate our resistor divider before the first use. 
To do so, we measure the battery voltage of the LiPo and compare the measured voltage by the voltage our voltmeter estimated.

$f_{COR} = \dfrac{V_{ACTUAL}}{V_{VOLTMETER}}$

We can calculate the deviation of the two values and receive a factor, with which we will simply multiple our results in the software. 

$V_{BAT} = \dfrac{n_{ADC}}{4095}*23.3V*f_{COR}$

#### Other Sensors
While we discussed the four most vital sensors that most every advanced model rocket will need (the gyroscope, accelerometer, barometer, and voltmeter) there are many more that you may require on your won project or flight computer. 

Three sensors that can be especially useful are the magnetometer, which is another of determining the rocket's orientation, the GNSS receiver - a GPS module to determine the rocket's position in 3D space, and ultrasonics sensors for close distance monitoring. 

##### Magnetometer
A magnetometer is the third way in which we can determine the rocket's orientation. A magnetometer measures the magnetic field that is present in its environment. As you know, Earth has a very strong magnetic field that is measurable around the world. We can think of the Earth as big bar magnet with magnetic field lines that range from the magnetic North to the magnetic South pole. The magnetometer can measure these magnetic field lines and their direction. Based on these measurements, it can estimate its own orientation. You can think of a magnetometer to be a compass. 

For a 3DOF (Degrees of Freedom) magnetometer that is used to determine orientation, we can think of it as having three compasses around three different axis. Through that we know exactly where the magnetic field is coming from. As the magnetic poles do not suddenly change, we can determine the orientation of the vehicle based on these measurements. 

However, the problem with a magnetometer is that other magnetic fields that are present in the real world can render the magnetometer's measurements useless, just as the accelerometer becomes useless when thrust is present. The biggest concern why we haven't yet incorporated a magnetometer to our designs, is the fact that our voltage regulation circuit features an inductor. This inductor creates a strong magnetic field which would partly impede the magnetometer. 

Yet, if careful consideration is taken into account when designing your PCB your project might benefit of adding this type of sensor! 

##### GNSS Receiver 
Another very important sensor is the GNSS receiver. 
GNSS stands for Global Navigation Satellite System. 
As the name suggests this systems allows users on Earth to determine their position in 3D dimensional space on Earth. This is done by a satellite constellation that usually sits in GEO (geo-stationary orbit). The GEO orbit is special as the satellites in this orbit are in sync with the Earth's rotation, which means that they always cover the same regions. 

In order for it to work, the device that wants to determine its position has to connect to at least four satellites. The satellites know their location, and feature exact timing. These satellites can now send their location data and their time data to the device that wants to determine its location. The device also knows the current time and can calculate the time that elapsed from the time the data was sent to the time it was received. Based on this time it can calculate the distance it has to the satellite, as the device knows the speed at which the information travels. Now one distance alone does not determine the position in 3D space. Only if this procedure is repeated with two more satellites, the device can determine where it sits in 3D space. We can image a sphere around each of the satellites that has the radius of the measured distance. Where the three or spheres intersect, is then the position of the device. We might think that three satellites are enough to determine the position. However, in order for the system to work we actually need a fourth one. The fourth satellite provides the device with accurate real-time data that is essential for calculating accurate distances. GNSS satellites all feature nuclear clocks with tremendous accuracy, which is why the device itself must be provided with accurate timing data. With an even larger number in satellites, it can increase the accuracy further. With this system accuracies of half a meter can be achieved in 3D space. 

When we want to integrate this system into our flight computer we have to select the receiver that does communicate with these satellites and calculate its position. 

One aspect we must consider when selecting such a receiver, is what satellite constellations it can receive. There many GNSS constellations including United States’ GPS (Global Positioning System), Europe’s Galileo, China’s Beidou, Russia’s GLONASS, India’s IRNSS, and Japan’s QZSS. Each position system has better coverage in one area and worse in another. If we were to launch in the U.S. the GPS system might be superior, while if we were to launch in Europe we probably would want to receive Galileo. The good thing is that there are GNSS receivers that can receive multiple constellations. 

If you want to integrate GNSS into your own project, you might want to look at the GNSS receivers from UBLOX such as the NEO-M9N. For implementing them, Sparkfun's breakout boards schematics might help you to do so on your own. 

##### More Sensors
There are so many sensors that could be useful for model rocketry applications that we will not be able to discuss them all in this course. 

Still, for you to get an idea of which sensors there are, I want to briefly list a few that might be interesting for your projects. 
- Ultrasonic sensors that determine distance based on the elapsed time that an ultrasonic sound wave needs to travel. Similarly to the echolocation bats use. This might be helpful to determining relative altitude to the ground or for obstacle avoidance. 
- Humidity, temperature, and air quality sensors to determine the state of the atmosphere. 
- Ultraviolet sensors for determining UV radiation, which you could use to assess Ozon layer depletion or levels of radiation to protect human from sun burns. 
- Radiation sensor (Geiger Counter), for gauging the exposure of radiation the flight computer experiences. 
- A weight cell for measuring the rocket's thrust in real-time to adjust the stabilization algorithm.
- Photoresistor to monitor the trigger of heating wires as well as engine ignition.  
- Strain gauges positioned on the rocket to gauge mechanical stress.
- Or seismometer to evaluate vibrations during flight. 
- And much much more! 

Most of the sensors come with SPI or I2C or are even analog devices, which you can simply read out by hooking them up to on of the ADC channels. 

The implementation principle is the same for all of them. 
You determine which property you want measure, source a part that can do exactly what you need, and implement it on your PCB according to its datasheet. 
#### Summary
The three most vital sensors that most every rocket will need are the gyroscope, the accelerometer, and the barometer. 

The gyroscope measures the angular rate, which we can then translate into the rocket's orientation by integrating and feeding it into a orientation representation model like Euler angels or Quaternions. Its measurements are very accurate over a short amount of time and aren't influenced by variations or other outside circumstances. However, they tend to drift over time. We calibrate them in order to minimize the drift. Yet, after some time every gyroscope will be off to a certain degree.

The accelerometer unfortunately cannot be used during model rocket flights, as the total thrust does not point to the Earth's center but is hard to predict. Remember it depends on the Earths gravitational acceleration, the the thrust curve and the engine's resulting acceleration, as well as the angle the TVC mount is currently in. However, it can be perfectly used to provide the gyroscope with a setpoint while sitting stationary at the launchpad. In that case only the gravitational acceleration is present, and orientation can be measured easily and without drift. The accelerometer's data can also be used after burnout of the rocket engine. During flight, accelerometers are also heavily influenced by vibrations. 

The third essential sensor is the barometer, which measures pressure and temperature to determine the altitude based on the barometric pressure equation. With increasing altitude the pressure decreases and with increasing temperature the pressure increases as well. It's relative accuracy can be quite high, however its absolute accuracy depends on a few more factors, such as humidity, diurnal fluctuations in pressure, as well as low and high pressures zones based on weather situations. 

Another sensor that can be useful is a voltmeter, which can be most easily implemented by using a resistor divider and one of the ADC channels on the microcontroller. With it we can determine the battery voltage, and notify the user if not enough voltage is present. 

There are still more sensors that might be highly useful, such as a magnetometer to determine the orientation of the rocket based on Earth's magnetic field, a GNSS receiver to evaluate the vehicle's position by using the positioning satellite systems, and many many more. 

Most sensors are connected by a SPI or I2C protocol, and some can be read out in an analog way. Many also feature interrupt pins by which they can indicate to the microcontroller that new data is ready. The sensor's datasheet is always the most important document to look at when implementing a sensor. It states the sensor's characteristics, and often provides a diagram with how to properly implement the sensor. 

## Level 8 - Outputs
### Lecture
Now, the microcontroller and its sensors are implemented and we basically have created a data logger. In essence, our flight computer is now able to interpret its environment. However, it can not yet intervene in its environment. The flight computer might notice that it unstable by 30° in the yaw axis. However, it has no way of changing those circumstances yet. This is where the flight computer's outputs come into play. 
#### RGB LED
The first and easiest output to setup is an LED. An LED can be helpful in flight computers for visual indication to the user. We can use an LED to show that the board is powered on, we could use an LED that to indicate the current flight state, and much more.

As you already know an LED is a diode that emits light if current is flowing through it in forward-bias. Remember that a LED also has a reverse-bias in which stops to be conductive. If the threshold voltage of a diode is overcome it becomes conductive in its forward bias. The voltage at which the LED emits light is called the forward voltage. 

The forward voltage varies on the color of the LED. 
A red LED has a forward voltage of 
1.8-2.2V, 
a green one of 2-3V
and a blue one of 3-3.5V.
Those are only typical values and the LEDs generally exist in many different forms. 

##### LED
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

#### Pyro Channels
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

#### PWM for Servo
To be able to control the servos that are located inside our thrust vector control system, we have to understand the concept of PWM (pulse width modulation). As we mentioned previously, most microcontrollers are only able to create digital outputs and often do not feature a DAC. Instead they switch the outputs on and off continuously to get a voltage that falls between the maximum 3.3V and 0V. The voltage that is achieved depends on the duty cycle of the signal, which is the ratio of the active time over the total time. To create a steady voltage this signal must than be filtered by adding a capacitor to the circuit. 

In a case of controlling a servo, we use the same principle, but spare the capacitor. 
A servo motor is a type of electric motor that incorporates a potentiometer. The potentiometer, also known as a variable resistor, consists of a rotary component that changes its resistance as it rotates. This rotation is directly linked to the position of the servo motor's output shaft. Through that the servo can accurately control its horn position. Consequently, most servos are limited to a range between -90 and +90 degrees in rotation. The potentiometer within the servo provides feedback to the servo controller, allowing it to adjust the motor's position to match the desired angle specified by the PWM signal. 

Servos have three wires. The power line that requires anything from 4 to 6V, the GND line, and the signal line. On the signal line, we provide the servos with information of what angle it shall target. This information is provided by a PWM signal with a duration of 20ms.
An active period of 1.5ms corresponds to the center position of the servo, so 0°.
An active period of 2ms corresponds to plus 90°, and an active period of 1ms corresponds to -90°. Anything in-between corresponds to the other angle values. Servos interpolate between these extremes based on the pulse width received. For example, a pulse width of 1.75ms corresponds to +45 degrees, while 1.25ms corresponds to -45 degrees. Through alternating the active period, we can indicate which angle the servo should take on. 

> Oscilloscope for PWM analysis 

#### SD Card
Another component that we might consider as output would be an SD card to which we can store our flight data. As we mentioned previously an SD card is basically a Flash storage with a specific form factor. There are micro SD cards and regular SD cards. For most flight computers we will use the micro SD cards to spare PCB space. 

To implement an SD card to our design, we have to add an SD card connector. There two ways in which those connectors hold the SD card in place. In summary, spring-loaded connectors feature a spring mechanism to secure the SD card in place and facilitate easy removal, while pluggable connectors offer a simple, friction-based connection for easy insertion and removal of the SD card without additional locking mechanisms.

When connecting the SD card, we use SPI again. The SD card needs to be powered by 3.3V with an added capacitor of 100nF. 
We connect the 
SCK to CLK
MISO to DAT0, 
MOSI to CMD
and the chip select of the SD card tot he CD or DAT3 pin. 
Through those simple connections the microcontroller can interface the SD card seamlessly.

#### Summary
LEDs are diodes that emit light in forward bias. They have a forward voltage that should drop across them and a rated current. To limit the current, when a voltage that is larger than the forward voltage is applied, a current limiting resistor is interposed. 
RGB LEDs use the three colors red, green, and blue to create any color and are often incorporated into a single package. 

For microcontrollers with too little GPIO output current, a driver IC can be used. The driver IC is basically a transistor array that allows to control high currents with low current microcontroller, while adding protection to the microcontroller. A low-side driver is easiest to use as the gate voltages are referenced to ground, and different source voltages can be on the load side. The transistor is basically interposed between the load and GND, compared to the high-side driver that is interposed between source and the load. 

Buzzers work by an electromagnet that moves a diaphragm. The oscillation of the diaphragm creates sound waves that we are able to hear. The oscillation is either created by an already incorporated IC than the buzzer is an active buzzer. Or we have to create this control signal by PWM, which additionally allows as to alter the pitch. 

Pyro channels are needed to trigger heating wires and electric ignitors. The basically interpose an N-channel MOSFET between the battery source and GND. The heating wires and electric ignitors are connected to a screw terminal that has the battery voltage connected to one pin and the drain of the MOSFET to the other pin. The MOSFET is controlled by a voltage that the microcontroller applies to the gate. It also features a pull-down resistor between gate and source, to prevent accidental power on, and adds a current limiting resistor to the gate to protect the microcontroller. We can add an LED to indicate when the pyro channel is turned. 

Servos are electric motors that feature a potentiometer for closed-loop angle control, and often only have a range of motion of +-90°. To control them a PWM signal with a duration of 20ms is supplied. The active region tells the servo which angle it shall target. If its 1ms it should steer to -90, if it's 1.5ms it should reach 0°, and if it is 2ms it should target +90°.

Finally, an SD card is flash storage that we can interface by SPI to store flight data. There are two types one that secures the SD card by a click (spring-loaded), and ones that secure the SD card by friction. 

## Level - Stack Analysis
### Lecture
With having covered all the main circuits for now, we can once again look at Stack, and learn about the circuits that we have used there.
#### CORE
![](/assets/images/a6700-0328%20-%20frame%20at%200m12s-2.jpg)
- Stack Core is concerned with the management of the entire flight computer system. 
- As you can see, it features an XT60 connecter for a battery.
- The battery that we choose to power the flight computer is a three celled LiPo battery with a capacity of 500mAh and a C-rating of 25. 
- Further, the PCB incorporates the LM2596 voltage regulator. Remember the LM2596 has a pin with which it can be activated. To that pin, we connected the switch. The input capacitor, the inductor, and the diode, as well as the output capacitor. Note that the inductor is as far away from control signals as possible. 
- The regulated 5V of the buck regulator are fed into a 3.3V linear regular the ASM1117-3.3 with two tantalum capacitors. 
- The main microcontroller of the flight computer system is this ESP32-WROOM-32E, which allows for easy programming via the Arduino IDE and easy WiFi and Bluetooth capabilities. 
- The ESP32 is programmable via the Micro USB port and the CH340 with the auto-reset circuit next to it. We added two buttons for manual reset and boot control. 
- Further, it features an RGB LED, a Buzzer, and a voltmeter. 
- And finally, the connector through which Vbat, 5V, 3.3V, GND, and an I2C bus are transmitted between the different boards. 
-
#### FUSION

![](/assets/images/a6700-0327%20-%20frame%20at%200m3s%20-%202.jpg)
- The second board features the STM32F7RET6 microcontroller. There are a lot of capacitors for the VDD, and here we have the VDDA filtering circuit. 
- Two buttons for boot and reset control. 
- The serial wire debug interface, as our main programming interface through an ST-Link V2. 
- A micro USB port as a backup. 
- Then, we have the crystal oscillator with its two capacitors. 
- The gyroscope and accelerometer (the BMI088) with its capacitors. 
- The barometer (the BMP388) also with capacitors. 
- An RGB LED. 
- Several backup pins to be able to connect the sensors with outside microcontrollers.
- And solder places for pull up resistors for the utilized SPI protocol. 
- Finally, this board features ESD protection. ESD stands for electrostatic discharge.
- You might recognize that we sometimes get electrically charged, for example when rubbing a balloon on your head, causing your hair to stand up. Sometimes you might even experience a slight electric shock when touching a metal object afterwards. 
- These electric shocks are in the thousands of volts. If we were to touch our PCBs in that state, they would obviously become permanently damaged. This is why we added ESD protection to all main connectors on the FUSION board. 
#### OUT
![](/assets/images/a6700-0330%20-%20frame%20at%200m5s%20-%202.jpg)
- The final board Stack Out features the STM32G030K8T6 microcontroller. 
- This microcontroller does not have to pins for the oscillator circuit, which makes the use of a crystal as an oscillator not feasible. However, this board requires accurate timing, as it shall control the servos of our flight computer. 
- There is only one pin to which the timing signal shall be inputted. Here we used an highspeed external oscillator. An oscillator is basically a component that only requires a voltage and then outputs a steady oscillation signal on its output pin. 
- Further, this version also has the serial wire debug connector, and one reset button. 
- Due to the small STM32 package there was also no pin for the boot control.
- We have five servo connections with 1x3 right-angled male pin headers. 
- An RGB LED, and
- Five high current MOSFET pyro channels, with indicator LEDs. As connectors, we used pluggable systems terminal blocks. This allows for easy connect and disconnect, as well as access when inserting heating wires and electric ignitors. 
- And again, ESD protection. 