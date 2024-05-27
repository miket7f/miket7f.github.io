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

## Level - Specific Microcontrollers
### Lecture
Now, with all the microcontroller basics out of the way, let's look at three specific microcontroller examples. But before we do so, let's talk about breakout boards and on-PCB design.
#### Breakout vs Embedded Microcontroller
We can implement a microcontroller into our flight computer in one of three ways. 

The first way would be to use a third-party breakout board. Breakout boards are ready to use microcontrollers, where all the necessary components are already pre installed. The breakout board most often features a voltage regulator which provides the exact 3.3V needed, has an integrated crystal oscillator which provides the microcontroller with accurate timing, and incorporates a chip (a USB to UART bridge) for proper communication between the PC and microcontroller. Further, it features a pin header for easy access of the microcontroller pins and has the bootloader pre-installed. 
This implementation is easiest, as those breakout boards can be used out of the box. An Arduino Uno, an ESP32 Dev Module, or a Teensy, would all be examples of such breakout boards. The processor that they incorporate are from different companies. An Arduino Uno, for example, features an ATMEGA16 microcontroller. The disadvantage is the increased weight, as we have an additional PCB, and pin rows. Further, it is not as reliable as the connection between the pins could be error prone. However, it is very beginner friendly, and if we came to just damage the microcontroller it could be replaced more easily. 

The second way would be by using a so called module. A famous example is the ESP32-Wroom module, which we will look at. This module can be directly implemented on our own PCB and spares as a few steps compared with a full microcontroller implementation. Such a module internally features a crystal for timing, has a pre-installed bootloader, has extra FLASH memory, and a Bluetooth antenna. In this case we only have to be concerned with the USB to UART bridge, for programming, and the power management of the microcontroller. 

The final way would be an into the PCB embedded microcontroller. In this case we have to do all the implementation ourselves. We have to select a proper crystal, have to establish the USB to UART bridge, provide proper power management, and sometimes have to install the Bootloader. Additional functionalities like Bluetooth and WIFI, must also be implemented by us, which requires antenna design and RF matching. We will look at this implementation by using an STM32 microcontroller. This method allows us to adjust our design to our needs to the maximum degree, and results in the most lightweight PCBs, as we can decide which features we want to incorporate and which we want to exclude. 

#### Teensy 4.1


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

## Level - Stack Analysis

