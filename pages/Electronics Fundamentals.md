---
layout: page
title: Electronics Basics
permalink: elec-design
---
## This path is work in progress!
The material that we provide in the following levels is by now means complete but it might help you to learn about the subject yourself, while we are working on providing content for you! 

## Level 1 - Introduction to the Electronics Path
### Lecture 
We know you are eager to develop your flight computer right away. However, we have to get you set up with the fundamentals first. Trust me, I have been there, designing my first flight computer without caring about the fundamentals, and well I can tell you that my first designs didn't work out as planned. 

For you to get the best understanding of circuit design possible, we have to start at the beginning. 
We will start within the atom and take a look at an even smaller unit - the electron. Then, we will zoom out and take a look at how atoms bond with each other. We will learn about the force that acts between them, describe what an electric charge is, and look at the concept of electric fields. Further, we will learn about conductivity, electric current, and electric potential difference or voltage.

You may wonder why we would want to understand all these theoretical concepts first. 
Well, almost every circuit uses a combination of the following components, of which you might already have seen some. (Video of the components)
To understand any one of them, you have to be familiar with their underlying concepts. 
This one, for example, is called a resistor. To understand it, you have to know about electric current, voltage, and ohms law. 
If you use a set of multiple resistors, you will have to learn about Kirchhoff's laws. 
Then here we have a capacitor. To understand it you additionally will need to know about electric charge. 
Finally, to understand a diode and a transistor we will have to understand how p-n junctions function. 

Within the first section of this electronics course, we will cover the theoretical fundamentals as well as the basic electronics components. In the second section, we will learn how to arrange those components to create functional circuits of which we can devise our flight computer. In the third section, we will dive into PCB design using the PCB design software Easy Eda. At the end, you will create your extension module for the Stack flight computer, and you will be able to self-develop flight computers.

All may sound terrifying to you at the beginning. Yet, stick with us and you will see that those concepts are way easier than as they sound. 
## Level 2 - The Electron

### Lecture 
In this lecture, we will dive into the world of the electrons. We will learn about the coulomb force, and how elements are categorized through the periodic table. We will look at the Bohr-Rutherford atom model, and we will learn about what Ions are. Although those things don't really sound like they belong in an electronics course, you will understand why we have to learn about them at the subsequent level. 
#### The Atom
Our world, everything you see, consists of extremely tiny building blocks - the so-called Atoms. Their name comes from the ancient Greek word Atomos, which stands for "uncuttable". Previously, they were thought to be undividable, but science has found out that they consist of even smaller units. 

These units are called - protons, neutrons, and electrons. 
The protons are charged positively, the neutrons are neutral, and the electrons are charged negatively.

An atom can be divided into a core and a shell. The core or nucleus consists of neutrons and protons and makes up more than 99% of the weight. The shell, on the other hand, consists of electrons and makes up the majority of the volume. As the neutrons aren't charged and the protons are charged positively, the net charge of the core is positive. 

You might know that similar charges repel each other while opposing charges attract each other. 
This is why the electrons are attracted to the nucleus. The force that acts between them is called the coulomb force. 

#### The Coulomb Force

This force is calculated after this formula: 

$F_C = \dfrac{1}{4*\pi*ε_0}*\dfrac{q_1*q_2}{r^2}$

$r$ ... Distance between q1 and q2

As we can see, the force decreases with increased space between them. Further, it increases with the charge of the elements. The larger the charge, the larger the force, and the greater the distance, the lower the force. 

The factor in front also features the vacuum permittivity constant that is given in farad per meter. 
$ε_0 = 8.85*10^{12} \dfrac{F}{m}$

However, you might wonder why the protons inside the nucleus do not repel each other. This is because there's another force present the so-called nuclear force. This force is magnitudes higher than the electrostatic force, yet it only occurs at very small proximities like those found in the core.

#### Periodic Table
Each atom consists of at least one proton in the core. The number of protons in the core significantly changes the properties of the element. This is why humanity came up with a way of classifying those elements with the so-called periodic table. An atom with one proton, for example, is referred to as hydrogen. An atom with two protons, on the other hand, is called helium. One with three protons is lithium, and one with four is called beryllium. The number you can see in the upper left of the periodic table elements is the atomic number, which is equivalent to the number of protons in the core. 

#### Bohr's Model 
There are different models with which the layout of the atom can be described. One of the first and simplest description is the one of Rutherford and Bohr. 

In their model there are different shell layers. Each shell layer can only contain a specific number of electrons. This number increases with the shell number after the formula $2n^2$. This means that there can be a total of 2 electrons in the first shell, 8 electrons in the second shell, and 18 electrons in the third shell. The higher the shell number the higher the energy that can be stored in the shell. The shell with the lowest energy is always filled first. So the next shell layer is only opened when the previous layer is already full. It is important to understand that every atom wants to have a full outer shell layer of electrons. These outer shell electrons are called the valence electrons. 

Now let's take a look at the periodic table again. The row in the periodic table represents the number of shells each element has. So if an element is listed in row two, this means that it has a total of two shell layers. If it is listed in row three, it has three shell layers, and so on. The column of the periodic table represents how many electrons there are in the outer shell layer. This means that the elements on the far left have only one electron in the outer layer, while the ones in the far right have a full outer shell layer of electrons. The ones in the far right are called noble gases. This is the condition every element wants to achieve.  

The elements in the periodic table are also separated into different groups. In its basics there are non-metals and metals. Metals usually have relatively few valence electrons, while non-metals are usually rich in valence electrons.

This will be important for you to understand the concept of conductivity later on! 

#### Ions
In normal circumstances, each atom has as many electrons in the shell as protons in the core, which means that the net charge of the atom is neutral. However, if we add or remove an electron from the shell, we get a charged atom, a so-called ion. An atom with added electrons in the shell is net negatively charged, as the number of electrons is higher than the number of protons. This is called an anion. An atom with removed electrons, on the other hand, is positively charged. We call this a cation. 

#### Summary
So, our world consists of atoms, and these atoms consist of a core and a shell. The shell is filled with electrons, while the core is filled with protons and neutrons. The electrons are held in the shell by the attracting electrostatic force that occurs because of the opposing charges of electrons and protons. The protons are held together by an even stronger force, the so-called nuclear force. 

Depending on the number of protons you get different elements. There's the Bohr model which describes the shell of the atom to consist of layers, while the electrons that sit in the outer layer are called valence electrons. 

Further, there are ions, which result in an imbalance between electrons and protons in an element. The atom can either be charged positively - cations,  negatively - anions, or it can be neutral. 

### Activity
- labeling the atom 
- naming element by periodic table 
- Bohr model and valence electrons
- metals non-metals?
- anion vs cation?

## Level 3 - Current

### Lecture 

#### Atom Bonding
The materials that we know from our day to day life, result from atoms bonding with each other to form something bigger. They can bond with each other through different forms. Metals, for example, bond with other non-metals through an ionic bond. Non-metals bond with each other through covalent bonds. And metals bond to each other through a metallic bond. 

Now, for us to understand electric current we first have to understand the metallic bond. 
As you previously heard, every element wants to have a full outer shell layer. This means that non-metals usually want to receive electrons to fill up their outer layer, because their outer layer is already quite full. Metals on the other hand normally want to give up electrons, as there outer layer is quite empty and filling it up would be more difficult to do. 

#### Metallic Bonding
Metals can achieve this state by bonding with each other through a metallic bond. When metals forms a metallic bond they give up their electrons in the outer layer. This means that the remaining atom are positively charged - cations. These cations would repel each other. However, the released electrons form a electron gas that fits between the cations. The positive cations and electrons attract each other, which causes the cations to form a regular structure. 

Because of this regularity, the metals receive their typical characteristics. Because of their bonding strength they are rigid bodies at room temperatures and have high boiling points. Further, they can be modified relatively easily through bending, forging, and so on. Each layer of cations in the rigid structure can be moved without destroying the bonds between them. 

#### Electric Current
Based on our understanding of the metallic bond, we can explain what electric current is. 
In simple terms, electric current is the flow of electrons (sometimes ions) through a material. In the case of a metal structure, this movement can occur easily as there are already delocalized electrons available. The freely moveable electrons inside the metal push each other forward and through that the electrons can flow from one end of the material to another. 

A material that allows for electric current flow is called an conductor, and the property of how well a material supports electric flow is called conductivity. 

We can compare electric current with the flow rate of water in a pipe. The flow rate in a water pipe gives the volume of water that passes through a water pipe per second and is given in liters per second. Similarly, electric current gives the number of charges that passes through a conductor in one second. The electric current is given in the unit Ampere. 

We already learned about the fact that electrons are charged negatively and that protons are charged positively. Both an electron and a proton have the same amount of charge. Their charge is called the elementary charge e zero and is given with $e_0 = 1.602*10^{-19} A*s$. The unit of a charge is given in Ampere times seconds which is the same as a Coulomb. 

This means that an electric current of 1 Amp is to a total of: $\dfrac{1}{1.602*10^{-19}}$ electrons flowing through the conductor in one second. 

$I = \dfrac{q}{t}$

#### Flow Direction
If we look at a basic circuit with a battery, a lamp, and two metal conductors, electrons are flowing from the minus to the plus port of the battery. Through this flowing movement energy is transferred from the battery to the lamp, causing the lamp to light up. If we disrupt one of two conductors, we no longer have a closed loop. Therefore, the electrons can no longer push each other forward, and no current flows. 

Electrons move from the minus to the plus pole. However, electrical engineers always label the flowing direction of the current to be from the plus to the minus pole. This representation called the "conventional representation" arose, because early scientists did not know whether the protons or the electrons are moving, and made the wrong guess. Because all formulars of that are used today build upon the wrong flow direction of the current, we still have to use the conventional representation. 

#### Direct Current vs. Alternating Current
The current that we described here is also called direct current (DC). In DC, current is flowing in one-direction only. When designing our own flight computer, we will almost always be using DC current. 

However, there is another form that you should have heard of an understand, which is called alternating current. The current coming from the power grid is AC. In fact, almost all of your consumer devices will be powered by AC. As the name suggests, the current changes periodically in direction and amplitude in the form of a sine wave. 
The frequency with which this change happens is called the AC power supply frequency. You probably already have heard that in most of Europe it is 50Hz (50 times per second), while in the US it is 60Hz (60 times per second). This is also why Europe consumer devices are not necessarily compatible with the devices in the US. 
#### Summary
So, atoms can bond with each other to form a bigger structure. 
Metals bond with metals through a metallic bond. 
Every metal element gives up its valence electrons to have a full outer layer. 
Through that they become positively charged. 
These cations would usually repel each other, however the electrons that were given up form an electron gas that is between the cations and holds them together in a regular structure. 

Current is the same in electricity as the flow rate in a water pipe. It is basically, the movement of electrons in a conductor. The electrons push each other forward and through that can transport energy from one source to another. It is measured in Ampere and tells us how much charge is transported through a conductor in one second.

A conductor is a material that allows current to flow. Metals, are always good conductors, as the delocalized electrons can move freely. 

The conventional direction of current flow is from the plus to the minus pole, which is used by electrical engineers in all sorts of formulas. It is also what you should use when drawing the direction of the current. However, keep in mind that in reality the electrons move from the minus to the plus pole. 

Finally, current can be split into DC and AC current. While DC current is a flow in one direction only, while the alternating current changes periodically in direction and amplitude. 
## Level 4 - Voltage
### Lecture
Now we know that electrons can flow inside a metal, and that the flow-rate is called electric current. However, you may ask yourself why this movement occurs.

The invisible force that pushes the electrons from one battery pole into the other is called the voltage. The higher the voltage, the more electrons will flow from one end of the battery to the other. 

This is quite simplistic and describes what the voltage does, but not how it is defined. 

The voltage is defined as the difference in **electric potential energy** between two points. 

This sentence is probably quite confusing to you. So let's break it. 

What is an electric potential? 
#### Electric Potential
It is the work needed to move a charged particle of 1 coulomb from infinity to a certain distance to another charged particle. 

In classical physics we know that the work is defined as:

$W = F*s$
The force times the distance. 

If we now apply this principle to calculate the work needed to move a charged particle from distance $r_1$ to distance $r_2$. Then, we know according to the formula of the coulomb force that the force changes between those two points. 

At point 1 the force will be: 
$\dfrac{1}{4*\pi*e_0}*\dfrac{q_1*q_2}{r_1^2}$

While at point 2 the force will be: 
$\dfrac{1}{4*\pi*e_0}*\dfrac{q_1*q_2}{r_2^2}$

To calculate the average force that occurs over the entire distance, we have to use the geometric average for the radius which is:
$r_1*r_2$

$W = \dfrac{1}{4*\pi*e_0}*\dfrac{q_1*q_2}{r_1*r_2}*({r_1-r_2}) = \dfrac{1}{4*\pi*e_0}*q_1*q_2*(\dfrac{1}{r_1}-\dfrac{1}{r_2})$

Now, we know the work that is needed to move a charged particle q_2 to q_1 from the distance r_2 to r_1. However, remember that the electric potential is defined as moving a charge of q = 1C from infinity to radius r_2. 
This means that we have to divide the work by the charge q_1 and insert infinity for r_1 to get the electric potential. 

$U = \dfrac{W}{q}$

$U = -\dfrac{q_2}{4*\pi*e_0}*\dfrac{1}{r_2}$   with the unit by $\dfrac{J}{C}$ Joule per Coulomb or $V$ Volts 

#### Water Pipeline
When we again take a water pipeline to explain the functioning of electricity, then we could say that the altitude at which the water level is corresponds to the electric potential energy. The higher the altitude of the water level the higher is the potential energy of it. 

Let's image we have two pools at different altitudes and connect them through a water pipe. Pool 1 is at an higher water level than pool 2. Now, we know at which altitude the water level of pool 1 is. However, this alone will not tell us how fast the water will flow from pool 1 to pool 2. To know that, we also have to know at which altitude the water level of pool 2 is. 

If the water level of pool 2 is almost at the same altitude, almost no water will flow from pool 1 to pool 2. However, if there is an altitude difference of several hundreds of meters, water will flow pretty damn fast. 

So, to figure out the flow rate of the water, it actually doesn't matter at which altitude either of the two pools are, but only what the altitude difference between them is. 

#### Voltage
We can take this concept and apply it to electricity one on one. The electric potential energy of one point alone, won't tell us how much current will flow. In fact, if we only have one point no current will flow at all. 

Only if we have a second point with a different electric potential energy that we connect to the first through a conductor we have an electric current. And this electric current solely depends on the difference in electric potential energy and not in the electric potential energy per say. 

This difference in electric potential energy is what we call the voltage, and it is always a relative measurement. So if we say we have AAA battery with a voltage of 1.5V then what we actually mean that the electric potential energy difference between the plus and minus pole is equivalent to 1.5V. 

#### Power Supply
For a electric circuit to function we have to provide this pushing force, or this difference in electric potential energy in some way. 

This is done through a power supply.

A battery creates this electric potential difference between its two poles by converting chemical energy into electrical energy. The battery basically attains a state in which the minus pole acquires an excess in electrons, while the plus pole lacks electrons. Through this imbalance the electrons are pushed from the minus pole to the plus pole if they are connected through a conductor. If they are not connected nothing happens, as electrons can't travel through air.

The pushing force can also be created by using a lab bench power supply that is connected to the power grid. 
#### Summary
So, the electric potential energy can be compared to the altitude of the water level in a pipeline system. If we only have one unconnected pool, no water will flow. If we then connect pool 1 to another, water will flow. How fast it will flow does only depend in the difference in altitude of the water levels. 

This same principle applies to the electric potential energy. It alone only won't tell us how much current will flow in a circuit and if we have only one pole with a certain potential energy not connected to anything, no current will flow at all. 

It is actually, the difference in electric potential energy that causes electrons to move from one potential to another if they are connected through a conductor. 

This electric potential difference is created by using a battery, a lab bench power supply, or any other voltage source. 
## Level 5 - Resistance
### Lecture
Through our deep dive in atom theory, we learned that the flow of electrons or charged matter in general is called electric current, while the pushing force behind it is called the voltage. 

The current I and the voltage U are linked with each other through something called the resistance. 

The resistance can be though of the diameter of the water pipe. As we established previously, the flow rate will be higher the higher the water level difference is. However, there's a  second constraint, which is the diameter of the pipe. The smaller the diameter the less water will flow. 

In electricity the water pipe diameter analog would be the resistance of the conductor. 
#### Ohms Law
The current and the voltage are linked through Ohms law: 

$R = \dfrac{U}{I}$  given in $\ohm$

#### Resistor 
Almost every component, even conductors, such as wires, have some sort of resistance. A wire without a resistance would be analogues to a tube with an infinity diameter, and we know that something like that does not exist. Often, the resistance is so small that it can be neglected.

Nevertheless, in some cases we want to limit the flowing current of a circuit intentionally. 
This is where the first component a resistor comes into play. 

A resistor provides an specific value of resistance. 

It is often made out of a carbon composition that is partially conductive and remains relatively constant in resistance over temperature change. The carbon composition is covered in plastics for isolation and two leads are added for easy implementation in a circuit. 

Further, they come with color bands that can tell us what the resistor value is. 
They come in the following format: X.XX * 10^X
The first three rings represent three digits of the resistor value, while the fourth ring provides the multiplier. 
The fifth and final ring provides the variation in resistance value, which is usually either +- 5 or +- 10% of the resistor value. 
## Level 6 - Schematics and Resistor Circuits
### Lecture
#### First Look at a Schematic 
In order to represent how different components are connected with each other to form a functional electric circuit, we use something that is called a schematic. 

Every component has its own dedicated symbol. A resistor for example is represented in this way. Actually, there are two different symbols for a resistor one that is used in Europe and one that is used in the US. We will use the European symbols for the rest of this course. 

Something that we will need in every schematic is the voltage source. Usually a standard battery is represented by this symbol, where the longer line represents the plus pole. 
To connect different components with each other we just draw simple lines. 

Just like that, we set up our first schematic of a resistor powered by a battery. 
We will supply a voltage of 9V by our lab bench power supply and for the resistor we will use one with 1k Ohms. 

If we want to know how much current is flowing in our circuit, we have to reformulate Ohm's law to output the current:

$I = \dfrac{U}{R} = 9mA$

This results in a current of 9 mA. 

Now let's test the same circuit in reality. 
As you can see, we plugged the resistor into a breadboard and used jumper cables to connect the resistor to the crocodile clamps of the lab bench power supply. 
Our lab bench power supply has the beneficial feature that we can adjust the voltage that we want to have according to our needs. Further, it incorporates an ammeter which measures the current flowing in the circuit. 

If we calculated correctly, we should now see our lab bench power supply supplies around 9mA of current. 

So, it is relatively easy to calculate the flowing current when using just one resistor. But, how can we calculate the current that flows in a circuit if we use more than one resistor?

#### Resistor in Series
In our example with a single resistor the 9V of the battery drop across the resistor.
If we now add a second resistor in series, the total voltage drop across both resistors must still can't be more than 9V, because remember this electric potential difference is provided by the our voltage source the battery. At the same time, this means that the voltage across the individual resistors must be less, so that together they have 9V. 

If we now wanted to know the flowing current, we have to calculate an equivalent resistance. 

For serial resistors this is done by adding their resistances together
$R_t = R_1 + R_2 + R_3 ...$

If we add a second resistor with another 2k Ohms, we get a total resistance of 3k Ohms, which means that the current would have to be 3mA. If we test this in our real circuit, we can see that it still holds true. 

In our water pipeline analogy the resistance is the diameter of the tube. If we add a second resistor in series to our first in our circuit, we increase the resistance and decreases the current. 
Decreasing the diameter in our analogy would do the same and also decrease the flow-rate.  

#### Resistor in Parallel 
There is a second way in which we could add a resistor, which is called in parallel. In this example a total of 9V would drop across each resistor. 

If we now wanted to calculate the equivalent resistance, we have to add their inverses:
$\dfrac{1}{R_t} = \dfrac{1}{R_1} + \dfrac{1}{R_2} + \dfrac{1}{R_3} ...$

If we this time we would have to 1k resistors, and get an equivalent resistance of 500 Ohms, which means that the current actually increased compared to the first example. 
We would now get a flowing current of 18mA, which we again can see holds true with our lab bench power supply. 

You could compare adding a second resistor to adding a second tube in our water pipeline. A second tube of the same diameter would also double the flow-rate. 

To get a more vivid understand of what exactly happens in the circuit we also have to discuss Kirchhoff's laws. 


#### Kirchhoff's Voltage Law
One of Kirchhoff's laws states that in any closed loop, the sum of the directed voltages must be zero. 

If we look at our example with the single resistor again, we see that the battery provides a voltage from the plus pole to the minus pole of 9V, while the resistor has a voltage drop in the opposing direction of also 9V. 
If we take the direction into account we get:
9V - 9V, which results in a sum voltage of the closed loop of zero. 

If we look at our second example with the two resistors in series, we can see why the total voltage across them must again be zero, and why the individual voltage drop across each resistor must be less. 

If we insert an equivalent resistance, the voltage drop must again be 9V, as the sum in a closed loop must always be zero, according to this law. 
In reality each of the two resistors has its own voltage drop. The first 3V and second one also 6V. In total 9 - 6 - 3V again results in a net zero voltage. 
We can calculate their specific voltage drops by using Ohm's law again, this time reformulated for the voltage:

$U = R*I$

Remember, we were only able to calculate the current, because we used an equivalent series resistance. So, before we are able to calculate the voltage drops across each individual resistors, we will always have to calculate the current. 

We can see that our calculations are correct, if we measure the voltage with this device that is called a multimeter. A multimeter is a measurement instrument, with which you can measure many different electrical properties, such as voltage, resistance, conductivity, and more. 
As you can see, across each single resistor we have a voltage drop of 4.5V and if we look at the voltage drop that occurs across both of them we have 9V. 

#### Kirchhoff's Current Law
The other Kirchhoff's law states that in a circuit the current splits in a junction. In any given node in a circuit the total amount of current must be zero. This means that the current that flows into a node must be the same as the current that flows out of node. If we think about the concept, it makes perfect sense, as otherwise energy would be mysteriously lost. 

In our first and second resistor example, we do not have any junctions. So, let's immediately analyze circuit three. 

We first can apply the role of net zero loops. So, we can immediately identify that the voltage drop across resistor one and resistor two both must be 9V. 
If we know the voltage and the resistance we can calculate the currents for both paths. 
Now, if we want to know the current that is flowing before the junction or that the battery provides, then, we have to apply the Kirchhoff's current law. The sum of currents must be zero in a node. Therefore, the input current must be the same as the sum of the two output currents. 

#### Short Circuit
To illustrate Kirchhoff's voltage law in a little more depth, let's consider the following scenario:
Instead of connecting one pole of the battery to a resistor and then to the other pole of the battery, we could also connect one pole of the battery directly to the other pole of the battery. 

The voltage would want to push the electrons from the minus pole to the plus pole. Remember, the number of electrons that can flow per second, depends on the resistance that is standing in the way of the electrons. 

In this case, the only resistance standing in the way, is the resistance of the wire and the internal resistance of the battery. This is like a water tube that is almost infinitely large. This means that the flow-rate or current is astronomically high. 

Still, the voltage drop across the wire and the internal resistance together will be zero, as the sum of net voltages is zero.

The amount of current flowing, is way too much in this scenario. The electrons are moving at such a rapid speed, that they create an immense raise in temperature. Either the wire or our battery will fail mechanically only moments after the current begins to flow. Accidentally connecting the plus to the minus, is what we call in electronic terms a "short circuit".

As electrical engineers, we to do our best to avoid short circuits at any costs, as they can destroy our circuits and components, initiate fire, or even harm somebody. 
#### Summary
To summarize: 
A schematic is a method to visually represent the wiring of electric components. 
We have specific symbols for each electric component. 
This, for example, is the symbol for a battery. 
And this is the European symbol of a resistor. 
By connecting the different symbols with each other, we indicate how they should be wired when building the physical circuit. 

We can calculate the current that flows in a standard battery resistor circuit, by using Ohm's law. 
If we use multiple resistors, we have to use an equivalent series resistance to be able to calculate the current that is flowing in the circuit. 

We differentiate between putting a resistor in series and in parallel:
In series, we add the resistances of the single resistors together. This can be compared to decreasing the size of the diameter in the water tube. 

When putting resistors in parallel, we add the reciprocals of the resistances together to receive the reciprocal of the equivalent resistor. Even though, we added a second resistor, we still increase the current. It is like adding a second tube to the water pipeline. Even if the added would be fairly small, it would still increase the overall flow-rate. 

Further, we learned that the directional sum of the voltages in a closed loop must be zero, and that the sum of the currents in a node must be zero as well.
We talked about a short circuit, in which the plus and minus pole of the power supply are connected accidentally, and talked about how this should be avoided at all times. 
## Level 7 - Capacitance
<iframe width="560" height="315" src="https://www.youtube.com/embed/GBu29s-65q4?si=KBHga9H893E6qcI8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Lecture
#### Capacitance
For us to understand the term capacitance we have to first recall charge and voltage.
A charge is the total amount of electrons a conductor can take up, while voltage is the electric potential difference that causes the electrons to move. 

Remember: in a conductive materials such as metals, the electrons are pushing each other forward when they experience a voltage. If there would be no freely moving electrons, there would be no movement and the material wouldn't allow current, which means that the material wouldn't be a conductor. 

Every conductor takes up a charge. In a metal the charges are the electrons. 
Scientists found out that the amount of a charge a conductor takes up rises proportionally with the voltage. 

The proportionality between the charge and the voltage is what we call the capacitance. 

$C = \dfrac{Q}{U}$  given in $\dfrac{A*s}{V}$  or $F$ Farads

If we look at a charge over voltage diagram we can see that the charge raises linearly with the voltage. Further, we see that for different values of capacitance the slopes are steeper or gentler. 

In reality, every component has some kind of capacitance. However, there are cases in which we want to have a lot of capacitance intentionally. Then, we will need a capacitor. 

This is the symbol of the capacitor. There different symbols for different types of capacitors. One for example can be used unidirectional while another can only be implement in a circuit in one direction only without damage. 

#### Homogenous Electric Field
The symbol represents its physical structure quite well, as every capacitor consists of two plates with a certain distance to each other. 

When a voltage is applied, it wants to push electrons from the negative pole to the plus pole. The electrons from the minus pole move to their attached plate and distribute equally, as equal charges repel each other. This means that the first plate is charged negatively. 

The plus pole of the voltage wants to receive electrons. Therefore, the delocalized electrons of the second plate are pushed into the plus pole. This means that the second plate is charged positively.

Every electric charge is surrounded by an electric field. 
An electric field is an imaginary area in which electric charges experience a force. 

$E=\dfrac{F}{q}$  given in  $\dfrac{N}{m}$

The force another charge experiences in the electric field is the coulomb force. We can insert q_1, which cancels with the nominator, and, therefore, see that the electric field only depends on the second charge and its radius to the first point charge. 

Two electrically charged plates also have such a field. If we were to overlap every single electric field of the electrons and cations that are sitting on each plate, we get something like a wave front. Even though the field lines of a single electric charge are circular, we get resulting field lines that are parallel with each other. 

This means that at any point between those two plates a electric charge would experience the same force. Let's imagine, we insert a negative charge between the plates. The positively charged plates want to attract the charge, while the negative plate wants to repel it. Because we assume that the two plates have almost an infinite length, the sum of forces would be the same at any point in the plate. This is what we call a homogenous electric field. 

Between the two capacitor plates we have a homogenous electric field. 
#### Usage
The plates are loaded with electric charge. However, the electrons will not move from the negative to the positive pole.

By loading the plates, energy is stored within the capacitor. 
$W = \dfrac{U*Q}{2} = \dfrac{C*U^2}{2}$

The higher the applied voltage and the higher the capacitance of the capacitor, the more energy will be stored within the capacitor. 

Although the amount of energy that is stored is pretty limited, it can be released very very fast. We can think about a capacitor to be similar to a battery. It stores less energy, but it can release its energy way faster. 

We use the capacitor in our circuits, for example, to act as an buffer in a unsteady voltage supply.
Let's image a circuit with a lamp that is powered by a battery. If we disrupt the conductor the lamp will immediately go out. However, if we were to place a capacitor in parallel to the lamp. The capacitor would be charged while the conductor is intact. When the conductor is disrupted. The electrons are no longer pushed into the capacitor plates. So, the electrons can move from the negative plate to the positive plate, and in turn provide the lamp with electrical energy. This means that the lamp will continue to be on for a short amount of time until the capacitor plates are unloaded. With a large enough capacitor, we can buffer the time in which the conductor is 
disrupted by powering the lamp through the capacitor. 

In our water analogy, the capacitor would be a water tank between two pipes. If we were to interrupt the flow of the first pipe without a water tank, the second pipe would immediately be without water. However, if we placed a water tank between the two pipes, the water would continue to flow even after we turned of the first pipe, as long as there is water in the tank. If the tank is empty, then the second pipe would also come to a stand. In this way, the water tank also acts as a buffer in our water pipeline. 

If we know recreate this circuit in reality, we have to use push button to create these conductor disruptions. This button basically connects the two conductors by a mechanic mechanisms. If we press it, we release this mechanic connection, and no current can flow any longer. 
If we powered the lamp only by a steady voltage supply and place a push button in-between one of its conductors, we can see that the lamp immediately goes out as soon as we press the button. If we now insert a capacitor after the switch, the capacitor will be charged as long as the switch is closed. If we now press the switch very briefly, the capacitor continues to supply the lamp with voltage, and it doesn't go out. 

#### Capacitor Formula
Now, you may wonder how the capacitance of a capacitor depends on the physical layout of it.
For that, the capacitor formula comes into play:

$C = \dfrac{\epsilon_r*\epsilon_0*A}{d}$  

As you can see, the capacitance increases with an increased area of the plate. The larger the area the more electrons ore cations will fit onto the plate. 
On the other hand the capacitance increases by decreasing the distance between the two plates. This makes also perfect sense, as the electrons on the negatively charged plate are attracted to the cations on the positive plate. The closer the plates the larger the attraction, which means that more charges will want to occupy the plates. 

The material between the two plates will also modify the electric field strength between them. 
The epsilon zero in the formula represents the assumption that we have a vacuum between the two plates. 
$ε_0 = 8.85*10^{12} \dfrac{F}{m}$ ... Vacuum permittivity 

However, most of the time we have a dielectric between the two plates. 
A dielectric decreases the strength of the magnetic field by a certain factor, which enables the plates to receive a higher charge per voltage. 

The effect the dielectric has on the capacitance is represented by the relative permittivity.
$\epsilon_r$ ... relative permittivity 

Now, the question again arises of what will happen if we put a second capacitor in our circuit. 
We also want to calculate an equivalent capacitance. Only this time, the formulas are exactly the opposite to the formulas that we used for the resistors. 
#### Capacitor in Parallel 
If we add a second capacitor in parallel. Both capacitors will experience the same voltage, as the net voltage in a loop must be zero. Both capacitors have their capacitances, so we know that both will have their charges according to the capacitance formula. 
This means that the total charge of the capacitors is the sum of the charge of the first and the second capacitor. 

$Q = Q_1 + Q_2$

So for the total charge we can insert the sum of the two separate charges.

$C = \dfrac{Q}{U}$

As the voltage is the same, we can simply add the capacitances to acquire an equivalent capacitance:

$C = \dfrac{Q_1+Q_2}{U} = \dfrac{Q_1}{U} +\dfrac{Q_2}{U} = C_1 + C_2$

#### Capacitor in Series 
If we add a second capacitor in series. Both capacitors will have the same amount of charge, but will have a different voltage drop across them. That all plates must be charged equally is due to the fact that similar charges want to repel each other and that they want to acquire as much distance to each other as possible. This can be best achieved if they spread across all four plates equally. 

Depending on the capacitances of the two capacitors, the voltage across the two capacitors will not be different.

$Q = Q_1 = Q_2$

$U= U_1 + U_2 = \dfrac{Q_1}{C_1}+ \dfrac{Q_2}{C_2}$

$\dfrac{Q}{C} = \dfrac{Q_1}{C_1}+ \dfrac{Q_2}{C_2}$

As the charge of the an equivalent capacitor would be the same as the charge of any one of the single capacitors, we can cancel the charges and get the formula for capacitors in series. 

$\dfrac{1}{C} = \dfrac{1}{C_1}+ \dfrac{1}{C_2}$

Adding capacitors in series, reduces their overall capacitance. 

#### Capacitor Types
There are many ways in which this intentional capacitance is achieved. Therefore, there are also many different capacitor types. You will now learn about the three most notable ones: the electrolytic capacitor, ceramic capacitor, and the tantalum capacitor. 

##### Aluminum Electrolytic Capacitor
The aluminum electrolytic capacitors - also called Elko - consist of two plates made out of aluminum. One of the plates has an oxidation layer, which occurs when aluminum is in contact with air and is a form of corrosion. This layer prevents further corrosion and acts as a dielectric layer in the Elko. Remember that the dielectric changes the 𝜖𝑟 (relative permittivity) and increases the capacitance. The aluminum electrolytic capacitors also consist of an electrolyte, which is a substance in which there are charged particles (ions) that can move freely within. In the case of this capacitor, the electrolyte allows ions to move, which helps maintain the capacitor's functionality. However, the capacitor itself does not become conductive through the electrolyte because there is also the dielectric layer that insulates the two plates from direct electrical conduction.

Since only one of the aluminum electrodes has the oxidation layer, the capacitor can only be used in one direction, and is not feasible for alternating currents and limited to DC applications. 

Aluminum electrolytic capacitors have high capacitances between several µF and mF in a relatively small volume. They are low-cost and available for high voltage applications. The electrolyte degrades over time, which results in a limited lifespan. 

##### Tantalum Electrolytic Capacitor
The tantalum electrolytic capacitors are often simply referred to as tantalum capacitors. Instead of aluminum they use a tantalum metal for the plates. Other than that they also features an oxide layer as the dielectric, too have an electrolyte, and are also polar. 

They provide stable capacitances over a wide range of temperatures and frequencies. Their capacitance values are typically lower than their Elko counterparts, but they excel in stability and reliability. They have a long lifespan, but are more expensive, and sensitive to sudden voltage spikes. 

##### Ceramic Capacitor
The ceramic capacitors use a ceramic as a dielectric. The most common type of them are the MLCCs, which consist of multiple layers of ceramic and metal stacked together. 

They are non-polarized, which means that they can be used unidirectionally. They come at wide ranges of capacitance value from pF to µF, and are used in both low and high voltage applications.
They excel in high frequency, making them suitable for high-frequency applications, and are available in very small sizes, ideal for consumer electronics. 

Their capacitance can vary with temperature change and applied voltage. Higher precision and stabler types can be quite expensive. 

#### Summary
Every conductor is able to store charge. The more voltage that is applied the more charge can be stored. The relationship between the charge and the voltage is proportional and called capacitance. It is given in Farad, which in practice is a quite large unit.

A capacitor can either be unidirectional or directional, and basically consists of two plates. When applying a voltage one plate is negatively charged while the other is positively charged. The larger the area, the more charge can be stored, and the closer the distance of the plates the higher the attraction, the more charges will load the area. To increase the capacitance further, a dielectric is used.

By loading the plates a capacitor stores energy. This energy can be released to buffer an unsteady signal. So, capacitor works similarly to a battery. Compared to a battery it stores way less energy, but it can release the energy way faster. These characteristics make a capacitor used on almost every circuit.

If we add multiple capacitors, we also have to determine the equivalent capacitance. In series, the capacitors experience the same voltage and the charges of the single capacitors add up, which means that the capacitances of the single capacitors can be added. In parallel the charges of the single capacitors are the same, as the charges want to spread equally across all plates. The voltages across the single, capacitors however are not the same. To get the parallel equivalent capacitance, we add the reciprocals of the single capacitances and receive the reciprocal of the equivalent of the capacitance.

Finally, there are many different capacitor types.
The aluminum electrolytic capacitors that feature high capacitances, are cheap, but are polar, and have a limited lifespan. 
The tantalum capacitors, which have slightly lower capacitances at the same volume, but are very stable of temperature and voltage changes. However, they are more expensive, sensitive to voltage spikes, and still polarized.
The ceramic capacitors, especially the MLCCs, which are non-polarized, available in very small form factors, and excel in high frequency applications. However, their capacitance can vary with voltage and temperature, and they have lower capacitance values. 
## Level 8 - Semiconductor and Diode
<iframe width="560" height="315" src="https://www.youtube.com/embed/guyFDPdGvFk?si=PI0bmzEbSoIIVaQd" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Lecture
#### Covalent Bonding
At the very beginning we explained that atoms bond with each other to form a different structure. We also said that the elements in the periodic table can be split into metals and non-metals, and that metals bond with each other through metallic bonding, and that non-metals bond with non-metals through covalent bonding.

To describe a semiconductor, we have to be aware of the concept of covalent bonding.
Remember: every atom wants to have a full outer layer of electrons. For non-metals the outer layer is almost full. So, they might only lack one-three electrons. For them it is easier to acquire the additional electrons than to give up all their electrons. In covalent bonding two elements that lack electrons unite and share one to three electrons with each other. Through that, both elements reach the desired state and have an equivalent of a full valence layer. 

The electron of the first element is then also attracted to the nucleus of the second element and the electron of the second element is also attracted to the nucleus of the first element.

#### Semiconductor
A conductor is a material that allow charged matter to move freely. 
An insulator on the other hand is a material that has no freely moving electrons and, therefore, which makes it impossible for current to occur. 
Then there are semiconductor. These have a full outer layer and also no freely moving electrons. However, if a large enough potential is applied to them the electrons are able to move and the material becomes conductive. 

The most used semiconductor material is silicon. Pure silicon is a structure that consists of many silicon atoms, each bonding with four other silicon atoms covalently. Most electrons are bond in this structure. However, there are a few electrons that can escape their bonds by getting enough energy, and this is what makes silicon partly conductive. 
 
#### Doping
But what really makes silicon ultra useful is doping. 
When doping, elements are inserted into the silicon structure that are foreign.

If phosphorus with five outer electrons is inserted, the structure has suddenly an excess electron. This is called an n-type semiconductor. 

If on the other hand aluminum with three valence electrons is inserted, the structure lacks an electron, which creates a place where there should be an electron in the structure but there isn't - a so called hole. This also increases the conductivity, as the electrons move inside the structure to fill up the hole, which again creates a new hole. However, we like to think that the holes are moving, and as holes lack electrons, we think about them as moving positive charges. 
This is what we call a p-type semiconductor. 

Even though their names are negative and positive type semiconductor. They are not charged negatively or positively, because they have the same number of protons and electrons inside them. It actually only refers to the sign of charge that can move.

#### P-N Junction
These properties become only really useful if we add these two doped semiconductor together. 
If we put a n-type next to a p-type semiconductor, we get what is called a p-n junction. 

In the border between the two regions, electrons move from the n-region to the p-region to fill the electron holes. This creates what is called a depletion region, in which there are no freely moving electrons or holes. A slim region of the p-side becomes negatively charged, while a slim region of the n-side becomes positively  charged. This creates an electric field, which prevents more electrons from moving from the n to the p-side. The depletion region acts like a barrier. 

When we now connect a voltage source to the p-n junction, with the positive pole connected to the p-side and the negative pole connected to the n-side. We push the electrons to move from the n-side to the p-side. This is what we call forward bias. However, for the movement to occur the pushing force - the voltage - must be high enough to overcome the barrier. If the voltage is higher than 0.7V, the barrier is overcome and the p-n junction becomes conductive.

If we reverse the polarity of the battery, and we connect the positive pole to the n-side and the negative pole to the p-side. Something entirely different happens. The electrons on the n side are attracted to the plus pole, while the holes on the p-side are attracted to the minus pole. Therefore, the depletion region or barrier expands an no current can flow. 

#### Diode
What we just creates is a diode. A diode is an electrical component that allow current to flow in one direction, while it prevents current from flowing in the other direction. 

A diode can be very useful, to protect our circuit from reverse voltage. It can also be used to convert alternating current to direct current. There are also special forms of diodes, such as LEDs (light emitting diodes) that emit light when voltage is applied in forward bias, or Zener diodes that have a breakthrough voltage after which they also become conductive in the reverse bias. Zener diodes can be used to protect our input channels from over voltage. 

#### Summary
When atoms bond covalently, they share their outer electrons to reach a full valence layer. 
There are conductors, isolators, and something in between that is called a semiconductor. 
The widest used material is silicon, which is a crystal like structure. 
The silicon structure can be doped by adding phosphor with an extra electron to create an n-type semiconductor, or by adding aluminum with a lack of an electron to create a p-type semiconductor. 
In the n-type semiconductor, electrons can move freely, while in the p-type semiconductor electron holes move freely. 
When placing an n-type semiconductor next to a p-type semiconductor, we get something that is called a p-n junction. Some of the electrons move to the p-side to fill up the holes, which creates an electric field that prevents further movement. 
If we apply voltage in forward bias this barrier can be overcome, and the material becomes conductive. 
If we apply voltage in reverse bias, the holes move to the negative side, while the electrons move to the plus pole of the battery, which makes the barrier even bigger, and allows no current to flow. 
Through that, we have created a component which allows current to flow in only one direction, which we call a diode. 
A diode can be used to protect our circuits against reverse voltage, or to rectify alternating current to direct current. There a special diodes, such as LEDs, which light up in forward bias and Zener diodes, which allow us to protect our devices from overvoltage. 
## Level 9 - The Transistor
### Lecture
There is one more component that is used in practically every electronics device today, and makes all our technologies possible. It is another application of semiconductor technology and you certainly heard about it at some point - the transistor. The transistor is like a switch that can turn on and off current flow. However, it does so without needing any mechanical components. 

#### P-N Junction
Remember the P-N junction that is within every diode. 
A p-doped semiconductor is next to a n-doped semiconductors. In the border region, electrons move from the n-side to p-side to fill up some electron holes. 
Through that, a slim region on the n-side becomes slightly positively charged, while a slim region on the p-side becomes slightly negatively charged. 
There's an electric field that goes from the n to the p side, which makes it hard for more electrons to move from the n to the p side. 
If we now apply forward bias voltage of more than 0.7V, the depletion region shrinks and the material becomes conductive. 
In reverse bias the electrons are the depletion area increases and no current can flow. 

#### BJT
The easiest form of a transistor is the BJT (Bipolar Junction Transistor). It works by adding another n or p-doped semiconductor to a P-N Junction. 
If we add a N region, we get an NPN.
And if we add a P region, we get a PNP transistor. 

##### NPN
Let's first analyze the NPN type transistor. 
The transistor consists of three ports. 
One is connected to the first N region, which is called the emitter.
Another is connected to the second N region, and is called the collector.
Then there is the gate that is connected to the P region. 
We can also think about a transistor, as consisting of two opposing diodes.
If we apply a voltage from emitter to collector, one of them is always in reverse bias and won't allow current to flow. 
Now if we apply a positive voltage to the P region, electrons from the reverse biased n region are attracted to the base. Through that, the depletion area decreases and electron holes of the P type are filled. 
Because there is no depletion region anymore, the electrons from the first N region are attracted to the plus pole of the battery connected from emitter to collector, and current can flow between emitter and collector. 

The higher the current on the base the less the depletion region becomes, the less the resistance between emitter and collector, and the higher the current flow between emitter and collector. 

$I_{CE}=I_B*H_{fe}$
The collector-emitter current is magnitudes higher than the base current and in fact is proportional by the proportionality constant Hfe that can be found in data sheets of transistors. 

#### MOSFET
A more advanced transistor version is the MOSFET, which is used in almost every integrated circuit today. Your laptop and phone contains billions of them, and with increasing years their sizes shrink drastically. Today the smallest are only 7-10nm small. A silicon atom is 0.2nm tall, which clarifies how small these transistors already are today.

MOSFET stands for 
Metal Oxide Semiconductor Field Effect Transistor 

There are many different types of MOSFETs. 
Firstly, the can be separated into enhancement and depletion type MOSFETs, which again can be sub-divided as N-channel and P-channel MOSFETs. 

##### N-Channel Enhancement Type
Let's look at the N-channel enhancement type MOSFET. 
It again consist of three regions, two N-regions, and one P-region again.
This type of transistor consists of four pins. 
The emitter equivalent is called source and is connected to the first N-region, 
the collector equivalent is called drain and is connected to the second N-region, 
and the base equivalent is called gate and connected to the P-region. However, there is a insulator or dielectric in-between the gate connection and the P-region. 
There is a fourth pin across the gate and connected to the source. 

If we were to connect a battery between source and drain, there would be no current flow, as one of the P-N junction again is in reverse bias. 
However, if we additionally apply a voltage to the gate pin, a electric field is created between the substrate pole and the dielectric. Electrons move from the N-junction to the dielectric and fill up some of the electron holes in the P-region. The more voltage we apply at the gate, the more electrons are attracted. This plate works similar to a capacitor. 
At some point there are freely moving electrons in the upper part of the P-region, which creates a tunnel between the two N-regions in which electrons can move. 

This explains the first major difference between a BJT and a MOSFET. As you can see, no current is flowing through the gate, which means that the MOSFET is controlled by the voltage and not the current. However, keep in mind that there is a short current burst required to charge the capacitance of the plate on the gate. 

When increasing the drain source voltage VDS, the drain source current IDS increases linearly at the beginning. However, the second N-region removes electrons from its border that travel to the plus pole of the battery, while holes on the other side are moved to the substrate body. This means that the depletion region o the second N-region increases. Through that, with increased drain source voltage, the tunnel becomes narrower again, and at some point the current does not increase linearly anymore but reaches a saturation, which we call saturation current. 

When we, however, again increase the gate voltage, the tunnel becomes wider, which means that we can increase the drain source voltage further before we reach this saturation voltage. 
This means that, we can entirely control the drain source current by the voltage that is applied on the gate. This makes the MOSFET ultra useful, and gives it another name, a so called voltage controlling device. 

##### N-Channel Depletion Type
We won't dive into how P-channel MOSFETs work.
However, we will briefly discuss in what ways an N-channel depletion type MOSFET would be different.

In the depletion type MOSFET, we already have a pre-existing tunnel manufactured into the MOSFET, which means that without the gate being turned on, current can already flow from the source to the drain. By applying a negative gate voltage to the depletion type MOSFET, the depletion region to the P-region substrate increases and the tunnel becomes narrower to the point of being able to turning the MOSFET completely of by applying a negative voltage to the gate. 

#### Summary
A transistor is another semiconductor, which can be used as a switch or as a voltage controlling device in a circuit. 
One of its simplest forms the BJT is created by adding a N or a P region to a PN junction. 

For a NPN type BJT, we get three connections called the emitter (connected to the first N-region), the collector (connected to the second N-region), and the base (connected to the P-region).
The two PN junctions function as two opposite facing diodes. If we apply a voltage from emitter to collector, one of them is reverse-bias, which means that no current can flow. 
However, if we apply a positive voltage to the base, electrons are attracted from the N-region and fill up some of the electron holes of the P-region. If enough voltage is applied, there are freely moving electrons in the upper part of the P-region, which makes it conductive. Through that, current can flow from emitter to collector and the transistor is turned on. 
The higher the flowing base emitter current, the more freely moving electrons, the higher the emitter collector current. The two currents are linked by the proportionality Hfe. 

Another form is the MOSFET (metal oxide semiconductor field effect transistor). A N-channel enhancement type MOSFET, consist of four ports: source, gate, drain, and substrate body. The substrate port is internally connected to the source pin. Source is connected to the first N region, Drain to the second, and Gate is connected to the P-region. However, between the gate and the P-region there is a dielectric, which allows no current to flow and opposite of the gate is the substrate body plate. When we now apply voltage between the gate and the source, a electric field between the gate and the substrate body is created. This electric field draws electrons from the N-region to the plate, which again fills up electron holes, and if enough voltage is applied the plate becomes negatively charged just as in a capacitor. This creates a tunnel between the two N-regions is, which makes current flow possible.

By increasing the drain source voltage, the current rises linearly in the ohmic region of the transistor. The higher the drain source voltage gets, the larger the depletion region on the drain N-region becomes because it is in reverse bias. This enlargement in depletion area, creates a limit to the drain source current, which we call the saturation current. The saturation current changes with the applied voltage to the gate, as the gate voltage can enlarge the tunnel. 

And finally, in the N-channel depletion type. There is already a tunnel present, and by applying a negative voltage to the gate the tunnel can be closed. 
## Level 10 - Induction 
### Lecture
#### Magnets
An electric field is created by an electric charge, and is an imaginator area in which another electric charge would experience a force - the coulomb force. There are positive and negative electric charges, and each of them can consist on their own.

Now, on the other hand there are magnets. If we look at a bar magnet, we can see that each magnet has a magnetic North and magnetic South pole. Magnetic field lines always travel from the magnetic north to the magnetic south pole.

If we now wanted to have only a magnetic South pole, one would think that by cutting a bar magnet in half we would get exactly that. However, it turns out that if we cut a bar magnet it half, we get two bar magnetic with each having a magnetic South and North pole. In fact, there is no way of creating just a magnetic South or a magnetic North pole, they always exist together. 

A bar magnet is created out of a metal. Some metals like iron are what we call ferromagnetic. When iron is created it forms grain boundaries. We think of each grain as having a permanent magnet inside that faces in a random direction. As every grain's magnet faces in an entirely different direction, there is no net magnetic field. 

However, if we apply a large magnetic field to the ferromagnetic material, the grain's magnets align with the magnetic field, and if this outside magnetic field was strong enough, the grain's magnets will stay in that alignment after the field was applied. Now this ferromagnetic material, became a magnet on its own. 

Its magnetic properties can be destroyed by heating up the magnet which randomizes the inner bar magnets again.

#### Electromagnetism
Now, there is electromagnetism. The connection between magnetic fields and electric current. 

Electrically charged particles that move create a magnetic field. This means that in a wire where there is current, a magnetic field is created. In a wire the magnetic field is in concentric circles around the wire. 
The direction of such a field can be determined by used the right hand rule, which states that by gripping the wire and aligning the thumb in the direction of the conventional current flow, the other fingers will show the direction of the magnetic field. 
The strength of the field decreases with increases distance to the wire. 

The reverse of this law states that if there is a magnetic field and we move a wire inside the magnetic field, current is induced in the wire. 

Finally, if the magnetic field changes, current is again induced in the wire, and if the current flow changes we get an induced voltage as well. 

Okay, let's look at the example with the wire creating a magnetic field again. 
If current is present, electrons move through the wire, which creates a concentrical magnetic field around the wire. One of the fundamental properties of a magnetic field is that it wants to remain steady. If we suddenly turned off our power supply, the magnetic field won't immediately be gone, as it wants to resist the change. Instead, it will slowly decrease. However, keep in mind that a magnetic field change leads to an induced current and voltage. The induction keeps the current flowing for a while and induces a voltage, even though the supply is already turned off. 

On the contrary, if we were to turn on the current again, the full current wouldn't immediately occur, because the magnetic field first needs to build up. In this case an induced current and voltage in the opposite direction would be present before the magnetic field was built up completely.

The wire stores energy in the form of magnetism. 

The parameter that describes the wire's characteristics of that energy is called inductance L given in Henry. 

The induced voltage can be calculated by multiplying the inductance with the change in current. 
$V = L*\dfrac{dI}{dt}$ ... Voltage

#### Inductors
By creating many turns of wire and creating a coil, we can increase the magnetic field that is created, and thus increase the inductive effect the magnetic field has. 
This forms the basis of our next component:
The inductor. 
Often the inductor additionally features a metal core, which increases the inductance. 

Here is the symbol of the inductor. 

So, what are the use cases of the inductor that result out of its properties?
A capacitor wants to keep the voltage steadily, while an inductor wants a steady current flow.  
If we were to turn off a flowing current, the inductor would continue to push electrons in the direction of the flow for a while. If we were to turn on current, the inductor would hinder the electrons at first before the magnetic field would be fully established. So, the inductor creates a lag in current changes, while a capacitor creates a lag in voltage changes. A inductor hinders instantaneous changes in current. 

And that's exactly for what it's used. 
For a steady current supplies a inductor is used, just as capacitors are used for steady voltage supplies. 
Another use case would be to store energy in the form of magnetic fields. In for example, switching power supplies. 
And yet another use example would be to use an inductor in conjunction with a capacitor to create a LC circuit for removing ripple from switched-mode power supplies. Ripple is a periodic variation in direct voltage. It occurs if DC current/voltage is derived from alternating current/voltage. 
#### Downsides
Inductors are relatively big.
They create a magnetic field which can influence near by signal lines or integrated circuits, which must be accounted for when designing the layout of a printed circuit board (PCB).
Finally, inductors themselves, can be influenced by applying a magnetic field to them. 
#### Summary
Magnetic fields always have to be closed in themselves, which is why there can't be a North or a South pole on its own. 

There's a interplay between electric charges and magnetic fields that is called electromagnetism. 
If electric charges are moving they create a magnetic field. For example, current flowing in a wire creates a concentrical electric field around the wire. 
Reversely, if there's a magnetic field and we move a wire inside the field, current is induced in the wire. 
Further if the magnetic field changes, current is again induced in the wire. 

A magnetic field always wants to remain steady and stores energy.
If we turn on the voltage source so current can flow through a wire, the magnetic field induces a current and voltage in the opposing direction until the magnetic field is built up completely.
If we turn off the voltage source, the magnetic field also wants to maintain its current state, and induces a current so it can continue to flow for a while. Through that, a lag in current change is created. 

If we were to create multiple turns of wire, we can increase this effect and create something that is called an inductor. Inductance is measured in Henry.
Often, inductor feature a ferromagnetic metal core to increase the inductance even further. 
Ferromagnets, are metals that can be made magnetic by applying an strong outside magnetic field to them. 

Inductors are used to store energy, to smooth a current supply, or in company with a capacitor to create a stable DC current from a switch mode power supply. When creating the layout, their placement must be considered. So, that their magnetic field does not influence signal lines or integrated circuits, and so it isn't influenced by a magnetic field itself. 

## Level 11 - Crystal Oscillator 
### Lecture
Before we can take our first look at a model rocket flight computer and its circuits we have to discuss one final fundamental technology. Have you ever wondered how a clock keeps time? 
Since its origin it uses some sort of oscillator that marks the elapsing of one second by which it turns its pointers. The oscillator itself changed many times over the creation of the clock. At first it used a pendulum. Then something similar to a tuning fork, an LC circuit, to finally using a piezoelectric crystal. 

Similarly to a watch, our integrated circuit also need some kind of impulse generator. If we want to control servos, read out sensor data, or transmit information through the air, we always need accurate control signals. And those need timing. 

#### LC circuit 
The first way to create timing is by using an LC circuit. 
Let's consider connecting a charged capacitor to a resistor. 
As soon as the resistor is connected, the current would jump to be maximum and then slowly decrease until there is no charge left in the capacitor.

Now, let's consider what happens if we replaced the resistor by an inductor. 
The capacitor has maximum voltage at the beginning and wants to create maximum current at the beginning as well. However, the inductor resists change in magnetic field, which creates a induced voltage in the opposite direction. This means that the current only slowly rises. The current rises and the inductor builds up its electric field until the current reaches its maximum. Then, it  decreases as the capacitor empties. However, this time the inductor resists the current decrease, and induces a voltage and current that wants to keep the flow going. This pushes current into the capacitor and charges it again but in reverse polarity. This means that the current flow would be in the reverse direction for the next half. The cycle begins again, and the current of an LC circuit takes the shape of a sine wave. 

In an ideal world, this oscillation would go on forever. However, in reality there is some kind of resistance in the circuit. So, it actually is a RLC circuit. The resistance gradually decays the amplitude until no oscillation is left. 

$V = L*\dfrac{dI}{dt}$ 

$I = C*\dfrac{dV}{dt}$ 

#### Piezoelectricity 
Now, there is a better way of creating such an oscillator. 
It is done by using the piezoelectric effect! 

The piezoelectric effect states that a quartz crystal creates a voltage if it is deformed. So, if you were to hit a crystal you it would create a certain voltage. On the contrary, if you applied a voltage across a quartz crystal it would elastically deform. If the voltage is turned off again the crystal would create a voltage as it elastically goes back to its original shape. 
The crystal oscillator circuit works by using a voltage signal from the quartz crystal, amplifying it, and feeding it back to the crystal. 

The result is that the crystal functions like an RLC circuit with a precise resonance frequency (the rate in expansion and contraction of the crystal). It comes with the advantage of loosing way less energy per cycle compared to an RLC circuit.
If we look at quartz crystal as a component. The symbol looks like this and it comes with two pins. 

#### Summary
To create proper timing for our communication protocols and our integrated circuits, we use a crystal. 
A crystal contracts by applying a voltage and releases a voltage as soon as it is allowed to go back to its original state. By feeding the voltage output of the crystal, amplifying it and feeding it back into the quartz, an oscillation is achieved. This oscillation is more power efficient, as it loses less energy per turn.
## Level 12 - Glimpse at Stack
### Lecture
We learned about atom theory, electric charges, electric potential, voltage, Kirchhoff's laws, magnetic fields, and inductance to derive the function principle of the most used electrical components:
resistors, capacitors, inductors, semiconductors, including diodes and transistors, and oscillators. 

The concepts build the foundation upon which we will now be able to learn how to interconnect them to form circuits that we can use in our flight computers. 

For you to grasp how often we use these components in a flight computer, let's take a look at Stack. 

As you learned before Stack consists of three boards that function together: 
Stack CORE, Stack FUSION, and Stack OUT.

#### CORE
![](/assets/images/a6700-0328%20-%20frame%20at%200m12s-2.jpg)
- 13 Resistors
- 9 Capacitors
- 1 Inductor
- 3 Transistors 
- 5 Diodes
- 3 Switches 
#### FUSION

![](/assets/images/a6700-0327%20-%20frame%20at%200m3s%20-%202.jpg)
- 4 Resistors 
- 19 Capacitors
- 3 Diodes
- 2 Switches
- 1 Oscillator 
#### OUT
![](/assets/images/a6700-0330%20-%20frame%20at%200m5s%20-%202.jpg)

- 18 Resistors
- 4 Capacitors
- 5 Transistors 
- 8 Diodes
- 1 Switch
- 1 Oscillator

All of these modules also have a lot of other components that are called integrated circuits. 
These circuits also mostly consist of basic components themselves. 

CORE
- ESP32 Microcontroller
- CH340 USB to UART driver
- LM2596 Buck Converter

FUSION
- STM32F7 Microcontroller
- BMI088 Gyroscope and Accelerometer
- BMP388 Barometer
- ESD Protection

OUT
- STM32G0 Microcontroller
- ESD Protection 

In the next topic you just unlocked - **Electronics Circuits** - you will learn about how to arrange the basic components according to your needs to form functional units that we can use for our flight computers. Further, you will learn about the most essential integrated circuits (ICs) which we will use often in our designs. 