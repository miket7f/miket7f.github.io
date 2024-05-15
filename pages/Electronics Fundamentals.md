---
layout: page
title: Electronics Basics
permalink: elec-design
---
## This path is work in progress!
The material that we provide in the following levels is by now means complete but it might help you to learn about the subject yourself, while we are working on providing content for you! 

## Level 1 - Introduction to the Electronics Path

### Video Transcript 
We know you are eager to develop your own flight computer right away. However, we have to get you set up with the fundamentals first. Trust me, I have been there, designing my first flight computer without caring about the fundamentals, and well I can tell you that my first designs didn't work out as planed. 

For you to get the best understanding of circuit design possible, we have to start all the way at the beginning. We will start within the atom and take a look on an even smaller unit - the electron. Then, we will zoom out and take a look on how atoms bond with each other. We will learn about the force that acts between them, will describe what an electric charge is, and look at the concept of electric fields. Further, we will learn about conductivity, electric current, electric potential and the concept of the electric current. 

You may wonder why we would want to understand all these theoretical concept first? 
Well, almost every electric circuit on Earth uses a combination of the following components, of which you might already have seen some. (Video of the components)
To understand any one of them, you have to be familiar with their underlying concepts. 
This one, for example, is called a resistor. To understand it, you have to know about electric current, voltage, and ohms law. 
If you use a set of multiple resistors, you will have to learn about Kirchhoff's laws. 
Then here we have a capacitor. To understand it you additionally will need to know about electric charge. 
Finally, to understand a diode and a transistor we will have to understand how p-n junctions function. 

All may sound terrifying to you at the beginning. Yet, stick with us and you will see that those concepts are way easier than as they sound. 
## Level 2 - The Electron

### Video Transcript 
#### The Atom
Our world, everything you see, consists of extremely tiny building blocks - the so called Atoms. Their name comes from the ancient Greek word Atomos, which stands for "uncuttable". Previously, they were thought to be undividable, but science has found out that they, in fact, consist of even smaller units. 

These units are called - protons, neutrons, and electrons. 
The protons are charged positively, the neutrons are neutral, and the electrons are charged negatively.

An atom can be divided into a core and a shell. The core or nucleus consists of the neutrons and protons and makes up more than 99% of the weight. The shell on the other hand consists of the electrons, and makes up the majority of the volume. As the neutrons aren't charged and the protons are charged positively, the net charge of the core is positive. 

You might know that similar charges repel each other, while opposing charges attract each other. 
This is why the electrons are attracted to the nucleus. The force that acts between them is called the coulomb force. 

#### The Coulomb Force

This force is calculated after the this formula: 

$F_C = \dfrac{1}{4*\pi*e_0}*\dfrac{q_1*q_2}{r^2}$

As we can see, the force decreases with increased space between them. Further, it increases with the charge of the elements. The larger the charge, the larger the force, and the greater the distance, the lower the force. 

The factor in front, also features the vacuum permittivity constant that is given in farad per meter. 
$ε_0 = 8.85*10^{12} \dfrac{F}{m}$

However, you might wonder why the protons inside the nucleus do not repel each other? This is because there's another force present the so called nuclear force. This force is magnitudes higher than the electrostatic force, yet it only occurs at very small proximities like those found in the core.

#### Periodic Table
Each atom consists of at least one proton in the core. The number of protons in the core significantly changes the properties of the element. This is why humanity came up with a way of classifying those elements with the so called periodic table. An atom with one proton, for example, is referred to as hydrogen. An atom with two protons, on the other hand, is called helium. One with three protons, is lithium, and one with four is called beryllium. The number you can see in the upper left of the periodic table elements is the atomic number, which is equivalent to the number of protons in the core. 

#### Bohr's Model 
There are different models with which the layout of the atom can be described. One of the first and simplest description is the one of Rutherford and Bohr. 

In their model there are different shell layers. Each shell layer can only contain a specific number of electrons. This number increases with the shell number after the formula $2n^2$. This means that there can be a total of 2 electrons in the first shell, 8 electrons in the second shell, and 18 electrons in the third shell. The higher the shell number the higher the energy that can be stored in the shell. The shell with the lowest energy is always filled first. So the next shell layer is only opened when the previous layer is already full. It is important to understand that every atom wants to have a full outer shell layer of electrons. These outer shell electrons are called the valence electrons. 

Now let's take a look at the periodic table again. The row in the periodic table represents the number of shells each element has. So if an element is listed in row two, this means that it has a total of two shell layers. If it is listed in row three, it has three shell layers, and so on. The column of the periodic table represents how many electrons there are in the outer shell layer. This means that the elements on the far left have only one electron in the outer layer, while the ones in the far right have a full outer shell layer of electrons. The ones in the far right are called noble gases. This is the condition every element wants to achieve.  

The elements in the periodic table are also separated into different groups. In its basics there are non-metals and metals. Metals usually have relatively few valence electrons, while non-metals are usually rich in valence electrons.

This will be important for you to understand the concept of conductivity later on! 

#### Ions
In normal circumstances, each atom has as many electrons in the shell as protons in the core, which means that the net charge of the atom is neutral. However, if we add or remove an electron from the shell, we get a charged atom, a so called ion. An atom with added electron in the shell is net negatively charged, as the number of electrons is higher than the number of protons. This is called an anion. An atom with removed electrons, on the other hand, is positively charged. We call this a cation. 

#### Summary
So, our world consists of atoms, and these atoms consist of a core and a shell. The shell is filled with electrons, while the core is filled with protons and neutrons. The electrons are held in the shell by the attracting electrostatic force that occurs because of the opposing chargers of electrons and protons. The protons are held together by an even stronger force, the so called nuclear force. 

Depending on the number of protons you get different elements. There's the Bohr model which describes the shell of the atom to consist of layers, while the electrons that sit in the outer layer are called valence electrons. 

Further, there are ions, which result in through an imbalance between electrons and protons in a element. The atom can either be charged positively - cations,  negatively - anions, or it can be neutral. 

#### Activity
- labeling the atom 
- naming element by periodic table 
- Bohr model and valence electrons
- metals non-metals?
- anion vs cation?
## Level 3 - Current

### Video Transcript 

#### Atom Bonding
The materials that we know from our day to day life, result from atoms bonding with each other to form something bigger. They can bond with each other through different forms. Metals, for example, bond with other non-metals through a ionic bond. Non-metals bond with each other through covalent bonds. And metals bond to each other through a metallic bond. 

Now, for us to understand electric current we first have to understand the metallic bond. 
As you previously heard, every element wants to have a full outer shell layer. This means that non-metals usually want to receive electrons to fill up their outer layer, because their outer layer is already quite full. Metals on the other hand normally want to give up electrons, as there outer layer is quite empty and filling it up would be more difficult to do. 

#### Metallic Bonding
Metals can achieve this state by bonding with each other through a metallic bond. When metals forms a metallic bond they give up their electrons in the outer layer. This means that the remaining atom are positively charged - cations. These cations would repel each other. However, the released electrons form a electron gas that fits between the cations. The positive cations and electrons attract each other, which causes the cations to form a regular structure. 

Because of this regularity, the metals receive their typical characteristics. Because of their bonding strength they are rigid bodies at room temperatures and have high boiling points. Further, they can be modified relatively easily through bending, forging, and so on. Each layer of cations in the rigid structure can be moved without destroying the bonds between them. 

#### Electric Current
So that we understand a metallic bond, we can ask ourselves what electric current is?
In simple terms, electric current is the flow of charged matter - in most cases electrons - through a material. In the case of a metal structure, this movement can occur easily as there are already delocalized electrons available. The freely moveable electrons inside the metal push each other forward and through that the electrons can flow from one end of the material to another. 

A material that allows for electric current flow is called an conductor, and the property of how well a material supports electric flow is called conductivity. 

You can also compare electric current with the flow rate of water in a pipe. And while the flow rate in a water pipe is given by liters per second, we give the flow rate in a electric circuit the "electric current" in Ampere. It represents the charge that passes through a conductor in one second. 

We already learned about the fact that electrons are charged negatively and that protons are charged positively. Both an electron and a proton have the same amount of charge. Their charge is called the elementary charge e zero and is given with $e_0 = 1.602*10^{-19} A*s$. The unit of a charge is given in Ampere times seconds which is the same as a Coulomb. 

This means that an electric current of 1 Amp is to a total of: $\dfrac{1}{1.602*10^{-19}}$ electrons flowing through the conductor in one second. 

$I = \dfrac{q}{t}$

#### Flow Direction
If we look at a basic circuit with a battery, a lamp, and two metal conductors, electrons are flowing from the minus to the plus port of the battery. Through this flowing movement energy is transferred from the battery to the lamp, causing the lamp to light up. If we disrupt one of two conductors, we no longer have a closed loop. Therefore, the electrons can no longer push each other forward, and no current flows. 

Electrons move from the minus to the plus pole. However, electrical engineers always label the flowing direction of the current to be from the plus to the minus pole. This representation called the "conventional representation" arose, because early scientists did not know whether the protons or the electrons are moving, and made the wrong guess. Because all formulars of that are used today build upon the wrong flow direction of the current, we still have to use the conventional representation. 

#### Summary
So, atoms can bond with each other to form a bigger structure. 
Metals bond with metals through a metallic bond. 
Every metal element gives up its valence electrons to have a full outer layer. 
Through that they become positively charged. 
These cations would usually repel each other, however the electrons that were given up form an electron gas that is between the cations and holds them together in a regular structure. 

Current is the same in electricity as the flow rate in a water pipe. It is basically, the movement of electrons in a conductor. The electrons push each other forward and through that can transport energy from one source to another. It is measured in Ampere and tells us how much charge is transported through a conductor in one second.

A conductor is a material that allows current to flow. Metals, are always good conductors, as the delocalized electrons can move freely. 
## Level 4 - Voltage
### Video Transcript
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
### Video Transcript
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
### Video Transcript
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
### Video Transcript
#### Capacitance
For us to understand the term capacitance we have to first recall charge and voltage. Charge is the total amount of electrons a conductor can take up, while voltage is the electric potential difference that causes the electrons to move. 

Remember: in a conductive materials such as metals, the electrons are pushing each other forward when they experience a voltage. If there would be no freely moving electrons, there would be no movement and the material wouldn't allow current, which means that the material wouldn't be a conductor. 

Every conductor takes up a charge. In the metal the charge are the electrons. 
Scientists found out that the amount of charge a conductor takes up rises proportionally with the voltage. 

The proportionality between the charge and the voltage is what we call the capacitance. 

$C = \dfrac{Q}{U}$  given in $\dfrac{A*s}{V}$  or $F$ Farads

If we look at a charge over voltage diagram we can see that the charge raises linearly with the voltage. Further, we see that for different values of capacitance the slopes are steeper or gentler. 

Again, almost every component has some kind of capacitance. However, there are cases in which we want to have a lot of capacitance intentionally. Then, we will need a capacitor. However, before we can explain how capacitor works, we have to first understand the electric field. 
#### Electric Fields
An electric field is an imaginary area in which electric charges experience a force. 
Every electric charge is surrounded by such an electric field.

$E=\dfrac{F}{q}$  given in  $\dfrac{N}{m}$

The force another charge experiences in the electric field is the coulomb force. We can insert q_1, which cancels with the nominator, and, therefore, see that the electric field only depends on the second charge and its radius to the first point charge. 

$E = \dfrac{1}{4*\pi*e_0}*\dfrac{q_2}{r^2}$

For a point charge, we the electric field strength decreases with an increased distance.

#### Homogenous Field
Let's imagine two plates with a certain distance to each other to which a voltage is applied. The voltage want to push them from the negative pole to the plus pole. Therefore, the electrons move from the minus pole to the attached plate and distribute equally, as equal charges repel each other. The first plate is charged negatively. 

On the opposing plate, the delocalized electrons are pushed from the plate to the plus pole of the battery. This means that the second plate is charged positively. 

We said that every electric charge has a electric field around it. This means that those two electrically charged plates also have such a field. If we were to overlap every single electric field of the electrons and cations that are sitting on each plate, we get something like a wave front. Even though the field lines of a single electric charge are circular, we get resulting field lines that are parallel with each other. 

This means that at any point between those two plates a electric charge would experience the same force. Let's imagine, we insert a negative charge between the plates. The positively charged plates want to attract the charge, while the negative plate wants to repel it. Because we assume that the two plates have almost an infinite length, the sum of forces would be the same at any point in the plate. This is we call a homogenous electric field. 
#### Electric Flux

## Level - P-N Junction
## Level - The Diode
## Level - The Transistor

## Level - Electric Induction
## Level - Inductor

## Level - Oscillator 

## Level - 1st Look at Stack



