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
<iframe width="560" height="315" src="https://www.youtube.com/embed/58GRvLRFcb4?si=NeR_7JKmpwnh5kvQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture 
This lecture will immerse us in the world of the basic building blocks that make up everything - atoms and their even smaller components. We will learn about the Coulomb force and how the elements are categorized in the periodic table. We will look at the Bohr-Rutherford atomic model and learn what ions are. Even though you might think that these things don't really belong in an electronics course, you'll understand why we need to learn them at the next level. 
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
$ε_0 = 8.85*10^{-12} \dfrac{F}{m}$

Another think you might wonder about is why the protons inside the nucleus do not repel each other. This is because there's another force present the so-called nuclear force. This force is magnitudes higher than the electrostatic force, yet it only occurs at very small proximities like those found in the core.

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

Further, there are ions, which result of an imbalance between electrons and protons in an element. The atom can either be charged positively - cations,  negatively - anions, or it can be neutral. 

### Activity
- labeling the atom 
- naming element by periodic table 
- Bohr model and valence electrons
- metals non-metals?
- anion vs cation?

## Level 3 - Current
<iframe width="560" height="315" src="https://www.youtube.com/embed/7nQuIP_uvTM?si=9LSt_SmRO6_Hzwvl" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture 
In this lecture, we will learn about how atoms bond with each other. Specifically, we will take a look at the bonding mechanisms between metals. After that, we will be able to understand electric current. We will discuss the direction of the current flow. Finally, we will differentiate between direct and alternating current.  

#### Atom Bonding
The materials we know from our day-to-day life, result from atoms bonding to form something. They can bond with each other through different forms. Metals, for example, bond with non-metals through an ionic bond, non-metals bond with each other through covalent bonds, and metals bond to each other through a metallic bond. 

To understand electric current, we first have to understand the metallic bond. As you previously heard, every element wants a complete outer shell layer. Non-metals usually want to receive electrons to fill up their outer layer because their outer layer is already quite full. Metals, on the other hand, want to give up electrons, as their outer layer is quite empty, and filling it up would be harder to do. 

#### Metallic Bonding
Metals can achieve this state by bonding with each other through a metallic bond. When metals form a metallic bond, they give up their electrons in the outer layer. The remaining atoms are positively charged cations. These cations would repel each other. However, the released electrons form an electron gas that fits between the cations. The positive cations and electrons attract each other, which causes the cations to form a regular structure. 

#### Electric Current
Based on our understanding of the metallic bond, we can explain what electric current is. In simple terms, electric current is the flow of electrons (sometimes ions) through a material. In the case of a metal structure, this movement can occur easily, as delocalized electrons are available. The freely moveable electrons inside the metal push each other forward, and the electrons can flow from one end of the material to another. 

A material that allows for electric current flow is called a conductor, and the property of how well a material supports electric flow is called conductivity. 

We can compare electric current with the flow rate of a water pipe. The flow rate in a water pipe gives the volume of water that passes through a water pipe per second and is specified in liters per second. Similarly, electric current gives the number of charges that pass through a conductor in one second. The electric current is stated in the unit Ampere. 

We learned that the electron's charge is positive and that the proton's charge is negative. Both charges have the same magnitude, which is called the elementary charge e zero, given with $e_0 = 1.602*10^{-19} A*s$. The unit of a charge is designated in Ampere times seconds, which is the same as a Coulomb. 

This means that an electric current of 1 Amp is equivalent to a total of $\dfrac{1}{1.602*10^{-19}}=6.2*10^{18}$ electrons flowing through the conductor in one second. 

$I = \dfrac{q}{t}$

#### Flow Direction
In a basic circuit with a battery, a lamp, and two metal conductors, electrons flow from the minus to the plus port of the battery. The flowing electrons transfer energy from the battery to the lamp, causing the lamp to light up. If we disrupt one of the two conductors, the loop is no longer closed, and the electrons can no longer push each other forward, allowing no current to flow.

Electrons move from the minus to the plus pole. However, electrical engineers always label the flowing direction of the current to be from the plus to the minus pole. They created this representation called the "conventional representation" because early scientists did not know whether the protons or the electrons were moving and guessed wrong. Because all formulas used today build upon the wrong flow direction of the current, we still have to use the conventional representation. 

#### Direct Current vs. Alternating Current
The current described here is called direct current (DC). In DC, the current is flowing in one direction only. When designing our flight computer, we will almost always be using DC. 

However, there is another form that you should have heard of and understand, which is called alternating current. The current coming from the power grid is AC. Almost all of your consumer devices are powered by AC. As the name suggests, the current changes periodically in direction and amplitude in the form of a sine wave. 
The frequency with which this change happens is called the AC power supply frequency. You probably already have heard that in most of Europe, it is 50Hz (50 times per second), while in the US it is 60Hz (60 times per second). Consequently, Europe consumer devices are not necessarily compatible with the devices in the US. 
#### Summary
So, atoms can bond with each other to form a structure. 
Metals bond with metals through a metallic bond. 
Every metal element gives up its valence electrons to have a full outer layer. Through that, they become positively charged. 
These cations would usually repel each other. However, the discarded electrons form an electron gas between the cations and hold them together in a regular structure. 

The current is comparable to the flow rate in a water pipe. It is the movement of electrons in a conductor. The electrons push each other forward and transport energy from one source to another. Electric current is measured in Ampere and tells us how much charge travels through a conductor in one second.

A conductor is a material that allows current to flow. Metals are always good conductors, as the delocalized electrons can move freely. 

The conventional direction of current flow is from the plus to the minus pole, which is used by electrical engineers in all sorts of formulas. It is also what you should use when drawing the direction of the current. However, in reality, the electrons move from the minus to the plus pole. 

Finally, we can divide the current into DC and AC. DC current flows in one direction only, while the alternating current changes periodically in direction and amplitude. 
## Level 4 - Voltage
<iframe width="560" height="315" src="https://www.youtube.com/embed/-SRMYzVknP4?si=2RhHp4FLpQJvd-mW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Now we know that electrons can flow inside a metal and that the flow rate is called electric current. However, you may ask yourself why this movement occurs.

The invisible force that pushes the electrons from one battery pole into the other is called voltage. The higher the voltage, the more electrons will flow from one end of the battery to the other. 

This definition is simplistic and describes what the voltage does. However, it does not tell as how it is defined. 

The voltage is defined as the difference in **electric potential** between two points. 

This concept might seem confusing at first. After this lecture, you'll understand this definition and the concept of voltage more thoroughly.

Let's break it down. 
First, what is an electric potential? 

#### Electric Potential
Electric potential is the work needed to move a charged particle of 1 coulomb from infinity to a certain distance from another charged particle. 

Let's use the water analogy again to make this concept easier to grasp. Imagine a water tank placed at a certain height. The height at which the water tank is placed corresponds to its potential energy. The higher the altitude of the tank, the more potential energy the water has.
You might remember that potential energy in this context is given by the formula:
$E = m*g*h$
where m is the mass, g is the acceleration due to gravity, and h is the height.

For electric potential, the formula is:
$U = -\dfrac{q_2}{4*\pi*e_0}*\dfrac{1}{r_2}$ 
where q_2 is the charge, ϵ0 is the permittivity of free space, and r_2​ is the distance from the charge.

The higher the charge, the higher the electric potential.
The smaller the distance to the charge, the higher the electric potential.
Along the same radius r_2 the electric potential remains constant. 

#### Water Analogy
Now, let's return to the water analogy. Imagine we have two pools at different altitudes connected by a water pipe. Pool 1 is at a higher water and thus potential energy level than Pool 2. However, knowing the altitude of the water level in Pool 1 alone doesn't tell us how fast the water will flow from Pool 1 to Pool 2. To determine the flow rate, we also need to know the altitude of Pool 2.

If the water level of Pool 2 is at the same altitude, no water will flow from Pool 1 to Pool 2. However, if there is an altitude difference of several hundreds of meters, water will flow fast. 

So, to figure out the flow rate of the water, it doesn't matter at which altitude either of the two pools is, but only what the altitude difference between them is. 

#### Voltage
The same is true in an electric circuit. The electric potential of one point won't tell us how much current will flow. In fact, if we only have one point, no current will flow. 

Only if we have a second point with a different electric potential that we connect to the first through a conductor do we have electric current. This electric current solely depends on the difference in electric potential and not on the electric potential per se. 

This difference in electric potential is the voltage, which is always a relative measurement. If we say we have an AAA battery with a voltage of 1.5V, we mean that the electric potential difference between the plus and minus pole is equivalent to 1.5V. 

#### Power Supply
For an electric circuit to function, we provide this pushing force or this difference in electric potential through a power supply.

A battery creates this electric potential difference between its poles by converting chemical energy into electrical energy. The battery attains a state in which the minus pole acquires electron excess while the plus pole lacks electrons. This imbalance pushes the electrons from the minus pole to the plus pole if connected through a conductor. If they do not, nothing happens, as electrons can't travel through air.

We can also create this pushing force by using a lab bench power supply connected to the power grid. 
#### Summary
So, the electric potential resembles the altitude of the water level in a pipeline system. If we only have one unconnected pool, no water will flow. If we then connect pool 1 to another, water will flow. How fast it will flow depends only on the difference in altitude of the water levels. 

In an electric circuit, the electric potential alone won't tell us how much current will flow in a circuit. If we have one pole with a potential energy not connected to anything, no current will flow. 

Only the difference in electric potential causes electrons to move from one potential to another if connected through a conductor. We can create this electric potential difference or push force through a battery, a lab bench power supply, or any other voltage source. 









## Level 5 - Resistance and Schematic
<iframe width="560" height="315" src="https://www.youtube.com/embed/3aD4S-XhU-E?si=Ygy74rekQYtbScmX" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Through our deep dive into atom theory, we learned that the flow of electrons or charged matter, in general, is called an electric current, while the pushing force behind it is called voltage. 

Now, we will learn about the relationship between the current and the voltage, which is called the resistance. Further, you will get to know the first component - the resistor. 

#### Resistance
We can think of the resistance as the diameter of the water pipe. As we established previously, the flow rate will be higher the higher the water level difference is. However, there's a second constraint, which is the diameter of the pipe. The smaller the diameter the less water will flow. 

In electricity, the water pipe diameter analog would be the resistance of the conductor. 

#### Ohms Law
The current and the voltage are, in fact, proportionally linked through Ohms law: 

$R = \dfrac{U}{I}$  given in $\ohm$
U ... Voltage [V]
I ... Current [A]
#### Resistor 
Almost every component, even a conductor, such as a wire, has some resistance. A wire without a resistance would be analogues to a tube with an infinity diameter. Often, the resistance is so small that it is neglectable.

Nevertheless, in some cases, we want to limit the flowing current of a circuit intentionally. In this case, we have to introduce the resistance on purpose and have to use our first component - the resistor.

#### Value
A resistor provides a specific value of resistance. 
It is often made out of a carbon composition that is partially conductive and remains relatively constant in resistance over a wide temperature spectrum. The carbon composition is covered in plastics for isolation and two leads are added for easy implementation in a circuit. 

Further, they come with color rings that represent the resistor's value. They have a total of four to five rings, while one ring is slightly spaced further apart than the rest. We always read the rings from the left, so that the further spaced ring is on the very right. The first two to three rings represent the digits of the resistor value, while the fourth ring provides the multiplier. The fifth and final ring provides the tolerance, usually either ±5% or ±10% of the resistor value. The final format is X.X...X * 10^Y ± Z%.

![](/assets/images/Resistor_color_code.png)

#### First Look at a Schematic 
To represent how different components are connected to form a functional electric circuit, we use something that is called a schematic. 

Every component has its dedicated symbol. A resistor, for example, is represented in this way. There are two different symbols for a resistor. One is used in Europe, and one is used in the US. We will use European symbols for the rest of this course. 

Something that we will need in every schematic is the voltage source. Usually, a standard battery is represented by this symbol, where the longer line represents the plus pole. 
We connect different components by drawing lines between them. 

Just like that, we set up our first schematic of a resistor powered by a battery. 

Let's calculate the current in a circuit. 
Let's say we supply a voltage of 9V by a battery, and for the resistor we chose one that has four rings. A brown, black, and red one on the left and a gold on the right. Brown stands for a 1, black for a 0, and red for a multiplier of 10^2. So, we have 10*10^2 = 10* * 100 = 1000 Ohm. The gold ring represents the deviation, which is +-5%. So, we expect the resistance value to be within 950 to 1050 Ohm. 

If we want to know how much current is flowing in our circuit, we have to reformulate Ohm's law to output the current:

$I = \dfrac{U}{R} = 9mA$

So, a voltage of 9V over a resistor of 1000 Ohm results in a current of 9 mA. 

Now, let's create a test circuit. 
This time we supply a voltage of 9V with a lab bench power supply and use this resistor with five rings right here.  Now, first, we have to determine the resistor's value. Let's first orient the resistor so that the ring with the larger spacing is on the right. Then, we have a brown ring, three black rings, and another brown ring. 
The first three rings are the digits, in this case 1 0 0, while the four ring is the multiplier. In this case 10^0. So, we get a resistance value of 100 Ohm with an accuracy of +-1% as defined by the last brown ring. 

Let's measure that with our multimeter. A multimeter is a measurement instrument, with which you can measure many different electrical properties, such as voltage, resistance, conductivity, and more. A multimeter is highly recommendable tool for electronic enthusiasts, as it highly helps to trouble shoot your projects and is cheap to access. 

We can again calculate the current and get: 
$I = \dfrac{U}{R} = 90mA$

Let's test if the calculated values apply in reality as well. As you can see, we plugged the resistor into a breadboard and used jumper cables to connect the resistor to the crocodile clamps of the lab bench power supply. 
Our lab bench power supply has the beneficial feature that we can adjust the voltage according to our needs. Further, it incorporates an ammeter to measures the current flowing in the circuit. 
As you can see the lab bench power supply indicates a flowing current of 0.09A, which is exactly the current of 90mA we expected. 

#### Summary
So, the proportionality constant of voltage and current is called the resistance and is given in Ohm. We can compare the resistance to the diameter of a water pipe, which in combination with the height difference of the two pools, determines the flow rate of the water. 

Ohm's law states that the relationship between the voltage and the current is the resistance. 

Every component, even a wire, has some resistance, and sometimes, we even want to introduce resistance intentionally, which is when we have to use a resistor. 

Resistors indicate their resistances by their color rings. The first two to three rings represent the digits of the resistor value, while the second-last ring provides the multiplier, and the final ring provides the tolerance. 

We can illustrate the wiring of our components by a schematic with the specific symbols each component has. A battery is indicated by a symbol with a longer and shorter line, where the longer line represents the positive terminal and the shorter line represents the negative terminal. A resistor is represented by a rectangle with two leads extending from either end.

By connecting the different symbols, we indicate how they should be wired when building the physical circuit. We can calculate the current that flows in a standard battery resistor circuit, by using Ohm's law. 

## Level 6 - Resistor Circuits
<iframe width="560" height="315" src="https://www.youtube.com/embed/NmUKCjEVO2w?si=7Y2wy-ncY_WXqpZU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
As we have seen in the last lecture, it is relatively easy to calculate the flowing current when using just one resistor. But how can we calculate the current that flows in a circuit, if we use more than one?

In this lecture, you will learn about resistors in series and parallel circuits. Further, you will be taught Kirchhoff's laws which will help you to analyze complex circuits, and you will hear about short circuits. 

#### Resistor in Series
In the example with the single resistor, the 9V of the battery drops across the resistor. If we add a second resistor in series, the total voltage drop across both resistors must still be 9V. The electric potential difference provided by the lab bench power supply did not change. Consequently, the voltage drop across the individual resistors must be less so that they have a voltage drop of 9V together.  

If we want to know the flowing current, we have to apply Ohm's law again, which requires us to use a single resistance only. To do that, we have to calculate the equivalent resistance of the two single resistances.  

This sequential arrangement of the two resistors is called a series circuit. For resistors in series, the total resistance is found by adding their resistances together:
$R_t = R_1 + R_2 + R_3 ...$

Let's add a second resistor with this color code (red, black, red, gold). The red and black represent a digit of 20, while the third red represents a multiplier of 100. Gold again represents a tolerance of +-5%. 
So, we have a resistance value of 2k Ohm with -5%. 

If we add R_2 to R_1, we get a total resistance of  3k Ohms. 
By recalculating the current with this equivalent resistor, we get a current of 3mA. 

In our water pipeline analogy, the resistance is analogous to the diameter of the tube. If we add a second resistor in series to the first in our circuit, we increase the total resistance and, as a result, decrease the current. Similarly, decreasing the diameter of the pipe in our analogy would increase resistance to water flow, just as adding a second resistor increases the resistance in an electric circuit.

Let's create a similar test circuit again: 
We use the 100 Ohm resistor from before again, and now add a 220 Ohm resistor, indicated by red, red, black, brown, brown. 
This results in a total resistance of 320 Ohm. 
We supply 9V again, which results in a current of 28.125mA.

And as we can see the lab bench power supply indicates 0.002A. You have to be aware that our lab bench measures currents only with an accuracy in the range of mA. So, the 20mA we got here, indicate that are calculation was again correct! 

#### Resistor in Parallel 
There is a second way to add a resistor, called in parallel. In this example, a total of 9V would drop across each resistor. 

If we now wanted to calculate the equivalent resistance, we have to add their inverses:
$\dfrac{1}{R_t} = \dfrac{1}{R_1} + \dfrac{1}{R_2} + \dfrac{1}{R_3} ...$

If we do this in our example, we have to add 1/1k + 1/2k  to get 1/ESR. 
Resulting in an equivalent resistance of  666.66 Ohms, which means that the current increased compared to the first example. 
We would now get a flowing current of 13.5mA.

You could compare adding a second resistor in parallel to adding a second tube in our water pipeline. A second tube would allow more water to flow through, effectively increasing the total flow rate, just as adding a second resistor in parallel decreases the total resistance and increases the current flow.

Let's arrange a similar test circuit again. 
We use the two resistor (the 100Ohm, and 220 Ohm) from before again and hook them up in a parallel arrangement. The equivalent resistance is 68.75 Ohm, which results in a current of 130.9mA. As you can see, our calculation was correct again! 

To get a more vivid understanding of what exactly happens in the circuit, we also need to discuss Kirchhoff's laws. Kirchhoff's laws are fundamental in circuit analysis and consist of two main principles.

#### Kirchhoff's Voltage Law
One of Kirchhoff's laws states that in a closed loop, the sum of the directed voltages must be zero. 

If we look at our example with the single resistor again, we see that the battery provides a voltage from the plus pole to the minus pole of 9V, while the resistor has a voltage drop in the opposing direction of also 9V. 
If we account for the direction, we get 9V - 9V, resulting in a sum voltage of the closed loop of zero. 

If we look at our second example with the two resistors in series, we can see why the total voltage across them must again be zero and why the individual voltage drop across each resistor must be less. 

If we insert an equivalent resistance, the voltage drop must again be 9V, as the sum in a closed loop must always be zero, according to this law. 
In reality, each of the two resistors has an individual voltage drop. The first 3V and the second one 6V. In total 9 - 6 - 3V again results in a net zero voltage. We can calculate their specific voltage drops by using Ohm's law again, this time reformulated for the voltage:

$U = R*I$

1000 * 0.003 = 3V
2000 * 0.003 = 6V. 

Remember, we were only able to calculate the current because we used an equivalent series resistance. So, before we can calculate the voltage drops across each resistor, we will always have to calculate the current. 

The same applies to our series test circuit, with the 100 Ohm and 220 Ohm resistors. We know that the flowing current should be 2.8125 mA. So, if we multiply this current with the resistances, we get: 

2.8125V and 6.1875V, which together is exactly 9V. 

We can see that our calculations are correct if we measure the voltage with a multimeter. As calculated, we have a voltage drop of 2.8125V across the first resistor and a voltage drop of 6.1875V across the second. If we look at the total voltage drop we have 9V. 

#### Kirchhoff's Current Law
The other Kirchhoff's law states that in a circuit the current splits in a junction. In any given node in a circuit, the total amount of current must be zero. The current that flows into a node must be the same as the current that flows out of the node. If we think about the concept, it makes perfect sense, as otherwise energy would be lost. 

In our first and second resistor circuit examples, we do not have any junctions. So, let's immediately analyze Circuit Three. 

We first can apply the rule of net zero loops. So, we can immediately identify that the voltage drop across resistor one and resistor two both must be 9V. 

We can calculate the currents for both paths. 
I1 = 9/1000 = 9mA
I2 = 9/2000 = 4.5mA

If we want to know the current flowing before the junction or the current that the battery provides, we have to apply Kirchhoff's current law. The sum of currents must be zero in a node. Therefore, the input current must be the same as the sum of the two output currents. 

I3 = I1 + I2 = 13.5mA

In addition, it's important to note that according to Kirchhoff's Current Law, the current remains constant along a single line or branch of the circuit. This principle is logical, as the electrons that move into one side of the conductor must move out of the other side, much like how water that enters a tube must eventually leave the tube.

#### Short Circuit
To illustrate Kirchhoff's voltage law in a little more depth, let's consider the following scenario:
Instead of connecting one pole of the battery to a resistor and then to the other pole of the battery, we could also connect one battery pole directly to the other battery pole. 

The voltage would want to push the electrons from the minus pole to the plus pole. Remember, the number of electrons that can flow per second depends on the resistance that is standing in the way of the electrons. 

In this case, the only resistance standing in the way is the resistance of the wire and the internal resistance of the battery. This resistance is very small and corresponds to a water tube with an almost infinite diameter, which means that the flow rate or current is astronomically high. 

Still, the voltage drop across the wire and the internal resistance will be 9V, as the sum of net voltages is zero.

The amount of current flowing is way too much in this scenario. The electrons are moving at such a rapid speed that they create an immense rise in temperature. Either the wire or our battery will fail mechanically only moments after the current begins to flow. Accidentally connecting the plus to the minus, is what we call in electronic terms a "short circuit".

When connecting the positive and negative crocodile clamps of our lab bench power supply, a short circuit is created. However, it's essential to note that the power supply incorporates protective features designed to mitigate potential risks. One of these features is a current-limiting mechanism, which caps the flow of current to a maximum of 10A. Do not try this at home though! 

As electrical engineers, we do our best to avoid short circuits at any cost, as they can destroy our circuits and components, initiate fire, or even harm somebody. 

#### Summary
To summarize: 
If we use multiple resistors, we have to use an equivalent series resistance to calculate the current in the circuit. 

We differentiate between putting a resistor in series and parallel:
In series, we add the resistances of the single resistors together, which can be compared to decreasing the size of the diameter in the water tube. 

When putting resistors in parallel, we add the reciprocals of the resistances together to receive the reciprocal of the equivalent resistor. Even though we added a second resistor, we still increased the current. It is like adding a second tube to the water pipeline. Even if the added tube is small, it would still increase the overall flow rate. 

Further, we learned that the directional sum of the voltages in a closed loop must be zero and that the sum of the currents in a node must be zero.

We talked about a short circuit, which occurs when the positive and negative poles of the power supply are connected directly, either accidentally or due to a fault in the circuit. This creates a path of very low resistance, allowing a large amount of current to flow through the circuit. This can cause significant damage to components, generate excessive heat, and potentially lead to fires or other hazards. Therefore, it is crucial to avoid short circuits at all times.

## Level 7 - Capacitance
<iframe width="560" height="315" src="https://www.youtube.com/embed/T2ymzSzFjs4?si=h5uu17BzT8yNW8xm" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


<iframe width="560" height="315" src="https://www.youtube.com/embed/28Kisy15diA?si=o6WfG9l2kKMFwGad" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Lecture
In this lecture, we're moving on to our next electronic component: the capacitor. 
We'll start by exploring the concept of capacitance, then move on to understand the structure of capacitors, their various applications, capacitor circuits, and the different types of capacitors encountered in flight computer development.

In the realm of flight computer design, capacitors are essential components, playing a crucial role in voltage regulation circuits, microcontroller implementations, and sensor integrations. Be sure to pay close attention during this lecture, as capacitors play a vital role in flight computer design!

#### Structure
First, let's examine the schematic symbol of the capacitor. There are primarily two different symbols used. One indicates a capacitor that can be used bidirectionally, while the other signifies a polarized capacitor, which can only be used in one direction.

The symbol represents its physical structure well, as every capacitor consists of two plates with a certain distance from each other. 

When we apply a voltage to the two plates, the electrons want to move from the negative pole to the plus pole. Yet, the electrons can't move from the negative to the positive pole, as they are not connected through a conductor. 

The voltage still pushes the electrons from the minus pole to their attached plate. On there, they distribute equally, as equal charges repel each other. Conversely, some electrons from the plate connected to the positive pole of the source are attracted towards that pole.

The electron excess on the plate connected to the negative battery pole, makes it negatively charged, while the electron void on the plate connected to the positive battery pole, makes it positively charged.

#### Capacitance
The amount of charges that fit onto the plates depends on the pushing force (the voltage) that is applied to the plates. The proportionality between the charge and the voltage is the capacitance. 

$C = \dfrac{Q}{U}$  given in $\dfrac{A*s}{V}$  or $F$ Farads

If we look at a charge over voltage diagram, we can see that the charge raises linearly with the voltage. Further, we see that for different capacitance values, the slopes are steeper or gentler. 

In reality, every component has some capacitance. However, there are cases in which we want to have a lot of capacitance intentionally. Then, we will need a capacitor. 

The capacitance of a capacitor or the ability of the capacitor to hold electric charges, mainly depends on three factors: 
$C = \dfrac{\epsilon_r*\epsilon_0*A}{d}$  

The first is the plate area. The larger the plates, the more electrons or cations will fit onto the plate. 
The electrons on the negatively charged plate are attracted to the cations on the positive plate. Consequently, the closer the plates, the larger the attraction, which means that more charges will occupy the plates. 
Finally, the material between the two plates will also modify the electric field's strength. By decreasing the field strength, more charges will fit onto the plates. 

#### Usage
By loading the plates, energy is stored within the capacitor. 
$W = \dfrac{U*Q}{2} = \dfrac{C*U^2}{2}$

The higher the applied voltage and the higher the capacitance of the capacitor, the more energy will be stored within the capacitor. We can think about a capacitor to be similar to a battery. It stores less energy, but it can release its energy way faster. 

A common use case for a capacitor is the filtering of fluctuations or noise in an unsteady voltage supply. 

Let's imagine a circuit with a lamp powered by a battery. If we disrupt the conductor, the lamp will immediately turn off. However, if we place a capacitor parallel to the lamp, the capacitor will be charged while the battery is connected. When we disrupt the connection to the battery, the voltage no longer pushes the electrons into the capacitor plates. So, the electrons can move from the negative plate to the positive plate and provide the lamp with electrical energy. The lamp will continue to light up until the capacitor plates are unloaded. 

#### Water Analogy
In the water analogy, the capacitor is a water tank between two pipes. If we were to interrupt the flow of the first pipe without a water tank, the second pipe would immediately be without water. However, if we placed a water tank between the two pipes, the water would continue to flow even after we turned off the first pipe, as long as there was water in the tank. If the tank is empty, then the second pipe would also come to a stand. The water tank also acts as a buffer in our water pipeline. 

In the context of flight computer design, we often utilize multiple capacitors to ensure stable and reliable operation. Let's explore how incorporating a second capacitor can impact the functionality of our circuitry.

#### Capacitor in Parallel 
We also want to calculate an equivalent capacitance. Only this time, the formulas are exactly the opposite of the formulas we used for the resistors. 

If we add a second capacitor in parallel, both capacitors will experience the same voltage, as the net voltage in a loop must be zero. Both capacitors have their capacitances, so we know that both will have their charges according to the capacitance formula. Consequently, the total charge of the capacitors is the sum of the charge of the first and the second capacitors. 

$Q = Q_1 + Q_2$

To receive the total charge, we can calculate the sum of the two individual charges.

$C = \dfrac{Q}{U}$

$C = \dfrac{Q_1+Q_2}{U} = \dfrac{Q_1}{U} +\dfrac{Q_2}{U} = C_1 + C_2$

As the voltage is the same for both, we can add the capacitances to acquire an equivalent capacitance. The formula is the same as the one for resistors in series. 

#### Capacitor in Series 
If we add a second capacitor in series to the first, the electrons will distribute equally across all four plates. Consequently, every plate and every individual capacitor will have the same charge. However, each individual capacitor will have a different voltage drop.

The equally charged plates are due to the fact that similar charges want to repel each other. The charges acquire as much distance from each other as possible, which is why they spread across all four plates.

$Q = Q_1 = Q_2$
The charge is the same for both capacitors. 

$U= U_1 + U_2 = \dfrac{Q_1}{C_1}+ \dfrac{Q_2}{C_2}$
The total voltage drop across the two capacitors must still be the battery voltage. 

$\dfrac{Q}{C} = \dfrac{Q_1}{C_1}+ \dfrac{Q_2}{C_2}$

As the charge of the equivalent capacitor would be the same as the charge of any one of the single capacitors, we can cancel the charges and get the formula for capacitors in series. 

$\dfrac{1}{C} = \dfrac{1}{C_1}+ \dfrac{1}{C_2}$

Adding capacitors in series reduces their overall capacitance, similar to the resistance of resistors in parallel. 

#### Capacitor Types
In the realm of flight computer design, we often encounter three primary types of capacitors: electrolytic, ceramic, and tantalum capacitors. Understanding their differences and applications can be crucial when designing electronic systems for your model rockets. Let's take a closer look at each one and how they might fit into your flight computer designs.

##### Aluminum Electrolytic Capacitor
Aluminum electrolytic capacitors, known as Elko, feature two aluminum plates, with one plate possessing an oxidation layer formed when exposed to air, acting as a dielectric. They also contain an electrolyte, allowing ions to move freely. 

Notably, Elko capacitors are polarized due to the presence of the oxidation layer on one electrode. The polarization makes them only usable in DC voltages. They offer high capacitances, ranging from several µF to mF, in a compact form. Despite being cost-effective and suitable for high-voltage applications, they have a limited lifespan due to electrolyte degradation over time.

##### Tantalum Electrolytic Capacitor
The tantalum electrolytic capacitors are often referred to as tantalum capacitors. Instead of aluminum, they use a tantalum metal for the plates. Further, they also feature an oxide layer as the dielectric, have an electrolyte, and are also polar. 

They provide stable capacitances over a wide range of temperatures and frequencies. Their capacitance values are typically lower than their Elko counterparts, but they excel in stability and reliability. They have a long lifespan but are more expensive, and sensitive to sudden voltage spikes. 

##### Ceramic Capacitor
Ceramic capacitors utilize ceramic as a dielectric, with the most common type being multilayer ceramic capacitors (MLCCs).

They are non-polarized, which means that they are useable unidirectionally. They come at wide ranges of capacitance values from pF to µF. They are used in both low and high-voltage applications.
They excel in high frequency, making them suitable for high-frequency applications, and are available in small sizes, ideal for space-constraint designs like those found on flight computers. 
Their capacitance can vary with temperature change and applied voltage. Higher precision and stabler types can be quite expensive. 

#### Summary
Every conductor can store charge. The more voltage that we apply, the more charge it can store. The relationship between the charge and the voltage is proportional and called capacitance. We give capacitance in Farad, which is an enormous unit.

A capacitor can either be unidirectional or directional and consists of two plates. When applying a voltage, we charge one plate positively and one negatively. The larger the area, the more charges it can store. The closer the distance of the plates, the higher the attraction and the more charges will load the area. For further increased capacitance, capacitors use a dielectric.

By loading the plates, a capacitor stores energy. We can use this energy to buffer an unsteady signal. So, a capacitor works similarly to a battery. Compared to a battery, it stores way less energy. However, it can release energy quickly. These characteristics make a capacitor used on almost every circuit.

If we add multiple capacitors, we have to determine the equivalent capacitance. In series, the capacitors experience the same voltage. In this case, the charges of the single capacitors add up. Therefore, the capacitances of the single capacitors add up as well. In parallel, the charges of the single capacitors are the same, as the charges want to spread equally across all plates. However, the voltages across the capacitors are not the same. To get the equivalent capacitance, we add the reciprocals of the single capacitances and receive the reciprocal of the equivalent capacitance.

Finally, there are many different capacitor types.
The aluminum electrolytic capacitors feature high capacitances, are cheap, polar, and have a limited lifespan. 
The tantalum capacitors have slightly lower capacitances at the same volume but are very stable in temperature and voltage changes. However, they are more expensive, sensitive to voltage spikes, and still polarized.
The ceramic capacitors, especially the MLCCs, are non-polarized, available in tiny form factors, and excel in high-frequency applications. However, their capacitance can vary with voltage and temperature. They have lower capacitance values. 
### Example
#### Transcript 
Now, let's demonstrate this concept hands-on.

To begin, we need a power source of 5V, a breadboard, a capacitor (ideally in the range of μF and able to withstand at least 5V), a 330 Ohm resistor, an LED (we used white), and a jumper wires. 

Let's set up the circuit:
- Start by placing the white LED onto the breadboard and connect the longer lead to the positive rail of the breadboard and the shorter one to a 330 Ohm resistor. 
- We connect the other end of the resistor to the negative terminal. 
- Further, we connect a capacitor from the positive terminal to the negative terminal in parallel to the LED. This capacitor should later provide voltage when the circuit is disconnected from the power supply. 
- Finally, we connect the positive rail of the breadboard to the positive pole of the power supply and the negative rail to the negative pole of the power supply. 

As soon as voltage is applied to the circuit, the capacitor charges. If we now disconnect the wire briefly, the capacitor continues to supply the LED with voltage, bridging the time the battery is disconnected. 

## Level 8 - Semiconductor and Diode
<iframe width="560" height="315" src="https://www.youtube.com/embed/qTu7wQJbnaY?si=ODHeszIma9d0nYk0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


<iframe width="560" height="315" src="https://www.youtube.com/embed/F5tJNmRe5TY?si=KlugeGmqlySTQ8Qn" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
In this lecture, you'll get to know yet another component: the diode. 
We'll kick things off by exploring the concept of covalent bonding, setting the stage for our understanding of semiconductor materials. From there, we'll learn about semiconductors and the concept of doping. We'll then dissect the p-n junction for you to understand the workings of a diode. 

Diodes are indispensable in-flight computer design, serving various critical functions such as reverse current protection, voltage limitation, and indicating user flight states. 


#### Covalent Bonding
At the very beginning, we explained that atoms bond with each other to form a different structure. We also said that we can separate the elements in the periodic table into metals and non-metals. Further, we mentioned that metals bond with metals through metallic bonding, while non-metals bond with non-metals through covalent bonding.

To describe a semiconductor, we have to be aware of the concept of covalent bonding.

Remember: every atom wants to have a full outer layer of electrons. The outer layer of non-metals is almost complete. So, they might only lack one or three electrons. For them, it is easier to acquire the additional electrons than to give up all their electrons. In covalent bonding, two elements that lack electrons unite and share one to three electrons with each other. Through that, both elements reach the desired state and have an equivalent of a full valence layer. 

The electron of the first element is then also attracted to the nucleus of the second element and the electron of the second element is also attracted to the nucleus of the first element.

#### Semiconductor
A conductor is a material that allows charged matter to move freely. 
An insulator on the other hand is a material that has no freely moving electrons, making current impossible to occur. 
Then there are semiconductors. These have a full outer layer and also no freely moving electrons. However, if a large enough potential is applied,  the electrons can move and the material becomes conductive. 

The most used semiconductor material is silicon. Pure silicon is a structure that consists of many silicon atoms, each bonding with four other silicon atoms covalently. Most electrons are bonded in this structure. However, there are a few electrons that can escape their bonds by getting enough energy, and this is what makes silicon partly conductive. 
 
#### Doping
But what makes silicon ultra useful is doping. 
When doping, elements are inserted into the silicon structure that are foreign.

If phosphorus with five outer electrons is inserted, the structure has suddenly an excess electron. This is called an n-type semiconductor. 

If on the other hand aluminum with three valence electrons is inserted, the structure lacks an electron, which creates a place where there should be an electron in the structure but where there isn't - a so-called hole. This process also increases the conductivity, as the electrons move inside the structure to fill up the hole, which again creates a new hole. However, we like to think that the holes are moving, and as holes lack electrons, we think about them as moving positive charges. We call this structure a p-type semiconductor. 

Even though their names are negative and positive-type semiconductors, they are not charged negatively or positively. They have the same number of protons and electrons inside them. The terms n- and p-type semiconductor only refer to the sign of charge that can move.

#### P-N Junction
These properties become only useful if we add these two doped semiconductors together. 
If we put a n-type next to a p-type semiconductor, we get what is called a p-n junction. 

In the border between the two regions, electrons move from the n-region to the p-region to fill the electron holes. This creates what is called a depletion region, in which there are no freely moving electrons or holes. A slim region of the p-side becomes negatively charged, while a slim region of the n-side becomes positively charged. This creates an electric field, which prevents more electrons from moving from the n to the p-side. The depletion region acts like a barrier. 

When we now connect a voltage source to the p-n junction, with the positive pole connected to the p-side and the negative pole connected to the n-side. We push the electrons to move from the n-side to the p-side. This is what we call forward bias. However, for the movement to occur, the pushing force - the voltage - must be high enough to overcome the barrier. If the voltage is higher than 0.7V, the barrier is overcome and the p-n junction becomes conductive.

If we reverse the polarity of the battery, we connect the positive pole to the n-side and the negative pole to the p-side. Something entirely different happens. The electrons on the n-side are attracted to the plus pole, while the holes on the p-side are attracted to the minus pole. Therefore, the depletion region or barrier expands and no current can flow. 

#### Diode
What we just create is a diode. A diode is an electrical component that uses a PN junction to only allow current to flow in one direction.

The symbol of a diode consists of a triangle with a vertical line and a horizontal line. The side of the triangle with the vertical line represents the cathode, while the opposite side represents the anode. Forward bias occurs when the diode's anode is connected to the positive pole and the cathode to the negative pole. This configuration allows current to flow through the diode in the direction of the arrowhead of the symbol.

We can use a standard diode on our flight computers to protect them from reverse voltage or to rectify alternating current to direct current by a full-wave rectifier. 

However, there are also other forms of diodes.
The ones most notable for flight computer design, are the Schottky diode, the light emitting diode, and the Zener diode. 

##### Schottky Diode
The Schottky diode uses a metal-semiconductor junction instead of a PN junction. By utilizing this junction, Schottky diodes can achieve faster switching speeds and exhibit lower forward voltage drops compared to their P-N junction counterparts.

Due to their ability to operate in fast switching speeds and their low dropout voltage, we often use them on switching voltage regulation circuits. 

##### LED
Light emitting diodes, emit light when current flows through them. They find widespread use in flight computers for status indicators, such as power indicators, system alerts, and communication status lights. LEDs are available in various colors, making them ideal for visual feedback in electronic systems. However, they require the use of a current limiting resistor, as they otherwise could become permanently damaged. 

##### Zener Diode
Unlike standard diodes, which conduct current in one direction only, Zener diodes can also conduct in the reverse direction when the voltage exceeds a specific threshold called the Zener voltage. Zener diodes can be used to protect our flight computer input channels from overvoltage.

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

### Example
#### Transcript
Now, let's put theory into practice with a hands-on demonstration.

To begin, we need a power source of 5V, a breadboard, a standard 1N4007 diode, a 330 Ohm resistor, an LED (we used white), and a jumper wires. 

- Start by connecting the positive terminal of the lab bench power supply to one end of the breadboard, and the negative terminal to the other. 
- Now, place the standard silicon diode into the breadboard, ensuring that its cathode, marked with a stripe, is connected to the negative rail.
- Next, connect one end of the resistor to the anode of the silicon diode, and the other end to the positive rail. This creates the path for our current to flow.
- If we now turn on the lab bench power supply, we can see that the current is flowing just as expected.
- However, if we change the polarity, the current stops flowing, as the diode is in reverse bias!
- If we use an LED instead of this standard diode, it will even light up when in forward bias. 
- Again, in reverse-bias, no current is flowing. 

## Level 9 - The Transistor
### Lecture
There is one more component that is used in practically every electronic device today and makes all our technologies possible. It is another application of semiconductor technology, and you certainly heard about it at some point - the transistor. The transistor is like a switch that can turn on and off current flow. However, it does so without needing any mechanical components.

We will first revise the PN-junction and then discuss the first form of transistors - the BJTs; we will dive into MOSFETs and their different variations.; and finally, we will look at the schematic symbols of the various transistor types.
   
#### P-N Junction
Remember the P-N junction that is within every diode. 
A p-doped semiconductor is next to a n-doped semiconductor. In the border region, electrons move from the n-side to the p-side to fill up some electron holes. 
Through that, a slim region on the n-side becomes slightly positively charged, while a slim region on the p-side becomes slightly negatively charged. 
There's an electric field that goes from the n to the p side, which makes it hard for more electrons to move from the n to the p side. 
If we apply a forward bias voltage of more than 0.7V, the depletion region shrinks, and the material becomes conductive. 
In reverse bias, the electrons are attracted towards the plus pole, the depletion area increases, and no current can flow. 

#### BJT
The simplest form of a transistor is the BJT (Bipolar Junction Transistor). It works by adding another n or p-doped semiconductor to a P-N Junction. 
If we add an N region, we get an NPN.
And if we add a P region, we get a PNP transistor. 

##### NPN
Let's analyze the NPN-type transistor. 
The transistor consists of three ports. 
One is connected to the first N region, which is called the emitter.
Another connected to the second N region is called the collector.
The port connected to the P region is called the gate.

We can think about a transistor as consisting of two diodes facing in opposing directions. If we apply a voltage from the emitter to the collector, one of them is always in reverse bias and won't allow current to flow. 

However, if we apply a positive voltage to the P region, electrons from the n region are attracted to the base. Through that, the depletion area decreases, and the electron holes of the P region fill up.

Because there is no depletion region anymore, the electrons from the first N region are attracted to the plus pole of the battery connected from the emitter to the collector and current can flow between the emitter and collector.   

The higher the current on the base, the less the depletion region, the less the resistance between emitter and collector, and the higher the current flow between emitter and collector. 

$I_{CE}=I_B*H_{fe}$
The collector-emitter current is magnitudes higher than the base current. In fact, the base current and the collector-emitter current are proportionally linked by the proportionality constant Hfe that we can find in data sheets of transistors. 

#### MOSFET
A more advanced transistor version is the MOSFET, which is used in almost every integrated circuit today. Your laptop and phone contain billions of them, and with each passing year, their sizes shrink drastically. Today, the smallest are only 7-10nm small. A silicon atom is 0.2nm tall, which clarifies how tiny these transistors are today.

MOSFET stands for 
Metal Oxide Semiconductor Field Effect Transistor 

There are many different types of MOSFETs. 
Firstly, we can separate them into enhancement and depletion-type MOSFETs, which we can subdivide into N-channel and P-channel MOSFETs. 

##### N-Channel Enhancement Type
Let's look at the N-channel enhancement type MOSFET. 
It again consists of three regions, two N-regions, and one P-region.
This type of transistor consists of four pins. 

The emitter equivalent is called the source and is attached to the first N-region. The collector equivalent is called the drain and is connected to the second N-region. The base equivalent is called the gate and is connected to the P-region but with an insulator or dielectric between the gate and the P-region. The fourth pin is connected across the gate and internally connects to the source.

If we connect a battery between the source and drain, there would be no current flow, as one of the P-N junctions is in reverse bias. 
However, if we additionally apply a voltage to the gate pin, an electric field is created between the substrate pole and the dielectric. Electrons move from the N-junction to the dielectric and fill up some electron holes in the P-region. The more voltage we apply at the gate, the more electrons are attracted. This plate works similar to a capacitor. 
At some point, there are freely moving electrons in the upper part of the P-region, which creates a tunnel between the two N-regions in which electrons can move. 

This illustration explains the primary difference between a BJT and a MOSFET. A MOSFET is voltage-controlled rather than current-controlled, meaning no current flows through the gate. However, a brief current burst is needed to charge the gate's capacitance.

When we increase the drain-source voltage VDS, the drain-source current IDS increases linearly at the beginning. However, the second N-region removes electrons from its border that travel to the plus pole of the battery, while holes on the other side move to the substrate body. Therefore, the depletion region of the second N-region increases. Through that, with increased drain-source voltage, the tunnel becomes narrower again, and the current does not increase linearly anymore but reaches a saturation, which we call saturation current. 

However, by increasing the gate voltage, the tunnel becomes wider. We can increase the drain-source voltage further before we reach this saturation voltage. Consequently, we can entirely control the drain-source current by the voltage we apply to the gate. This characteristic makes the MOSFET ultra-useful and gives it another name, a so-called voltage-controlling device.  

##### P-Channel Enhancement Type and PNP BJT
The P-channel enhancement type MOSFET operates similarly to the N-channel but with reversed polarities. It consists of two P-regions and one N-region.

To switch on the P-channel enhancement type MOSFET, we have to apply a negative voltage to the gate. The negative voltage creates an electric field that attracts holes from the P-regions into the N-region near the gate. These holes accumulate in the N-region, forming a conductive path or "channel" between the source (first P-region) and the drain (second P-region).
With the channel formed, holes can move from the source to the drain when a voltage is applied between them, allowing current to flow through the MOSFET. Source and drain are also switched. The source is connected to the positive pole, while the drain is connected to the negative pole. 

A PNP BJT works in a similar way but is current-controlled rather than voltage-controlled. In a PNP transistor, when a small current is applied to the base, it allows a larger current to flow from the emitter to the collector. 

##### N-Channel Depletion Type
We will also briefly discuss in what ways an N-channel depletion type MOSFET is different to the enhancement type. 

In the depletion type MOSFET, we already have a pre-existing tunnel manufactured into the MOSFET, which means that without the gate turned on, current can flow from the source to the drain. By applying a negative gate voltage to the depletion type MOSFET, the depletion region decreases, and the tunnel becomes narrower to the point of being able to turn the MOSFET completely off by applying a negative voltage to the gate. 

#### Symbols
Now let's take a look at the circuit symbols of the different transistor types. 

Let's first look at the bipolar junction transistor symbols:
In NPN transistor symbol, the arrow points outward from the base to the emitter, while in a PNP transistor, the arrow points inward from the emitter to the base. The letters E, B, and C represent the emitter, base, and collector terminals, respectively.

Next up, let's take a look at the MOSFET's symbols: 
In the N-channel MOSFET symbol the arrow point from source inward to the gate. For the P-channel MOSFET the arrow point from the gate to the source. 

In all cases, the third pin on the right side of the symbol represents the connection between the substrate and the source. For depletion-type MOSFETs, the three terminals on the right-hand side are connected, indicating the pre-manufactured terminal. The letters S, D, and G represent the source, drain, and gate terminals of the MOSFETs, respectively.

BJTs operate as current-controlled devices, relying on a continuous base-emitter current to remain active. 

In contrast, MOSFETs are voltage-driven, making them inherently more efficient. This voltage-driven characteristic grants MOSFETs several advantages: they boast lower power consumption, and superior switching efficiency compared to BJTs. 

Additionally, MOSFETs typically offer faster switching speeds, making them ideal for high-frequency applications. Moreover, MOSFETs exhibit better thermal stability and can handle higher power densities than BJTs, contributing to their widespread use in modern electronics. Furthermore, MOSFETs are more scalable, allowing for easier integration into advanced semiconductor technologies.
#### Summary
A transistor is another semiconductor. We can use it as a switch or a voltage-controlling device in a circuit. One of its simplest forms is the BJT, which is created by adding an N or a P region to a PN junction. 

For an NPN-type BJT, we get three connections called the emitter (connected to the first N-region), the collector (connected to the second N-region), and the base (attached to the P-region).
The two PN junctions function as two opposite-facing diodes. If we apply a voltage from the emitter to the collector, one of them is in reverse bias, which means that no current can flow. 
However, if we apply a positive voltage to the base, electrons are attracted from the N-region and fill up some of the electron holes of the P-region. If enough voltage is applied, there are freely moving electrons in the P-region, which makes it conductive. Consequently, current can flow from the emitter to the collector. 
The higher the base-emitter current, the more freely moving electrons, and the higher the emitter-collector current. The two currents are linked through the proportionality Hfe. 

Another form is the MOSFET (Metal Oxide Semiconductor Field Effect Transistor). A N-channel enhancement type MOSFET consists of four ports: source, gate, drain, and substrate body. The substrate port is internally attached to the source pin. The source is connected to the first N region, the Drain to the second, and the Gate is connected to the P-region. However, between the gate and the P-region, there is a dielectric, which allows no current to flow, and opposite the gate is the substrate body plate. 

When we apply a voltage between the gate and the source, an electric field between the gate and the substrate body is created. This electric field draws electrons from the N-region to the plate, which again fills up electron holes, and if enough voltage is applied the plate becomes negatively charged as in a capacitor. This charged region creates a tunnel between the two N-regions, which makes current flow possible.

By increasing the drain-source voltage, the current rises linearly in the ohmic region of the transistor. The higher the drain-source voltage gets, the larger the depletion region on the drain N-region becomes because it is in reverse bias. This enlargement in the depletion area limits the drain-source current, which we call the saturation current. The saturation current changes with the applied voltage to the gate, as the gate voltage can enlarge the tunnel. 

For a P-channel MOSFET, the voltage must be applied with the source at a higher potential than the drain. To turn the P-channel MOSFET on, the gate voltage must be lower than the source voltage. This means that a negative voltage relative to the source needs to be applied to the gate to create the channel between the source and the drain.

Finally, in the N-channel depletion type MOSFET, a conductive channel (or tunnel) is pre-manufactured into the device. By applying a negative voltage to the gate, the channel can be narrowed or closed, reducing or stopping the current flow.

MOSFETs have faster switching speeds, higher efficiency, and are more scalable, leading to their more frequent use compared to BJTs.
### Example
#### Transcript 1
Now, let's put theory into practice with a hands-on demonstration.
In the first example, we will switch an LED on and off in a low-side application by using a NPN transistor. In the second one, we will do the same in a high-side application by using a PNP transistor. 

First, the NPN transistor circuit
To begin, we need a power source of 5V, a breadboard, a standard BC547 transistor, a 102.60k Ohm resistor, a push button, an LED (we used white), and jumper wires. 

- Start by connecting the positive terminal of the lab bench power supply to one end of the breadboard, and the negative terminal to the other. 
- Now, place the BC547 transistor into the breadboard, ensuring that its three pins are at three different breadboard lines. 
- By looking at the datasheet, we can see that the left pin is the collector, while the right pin is the emitter. 
- We connect the anode of the LED to the 3.3V line. 
- Next, we connect the cathode of the LED to the collector, and the emitter to GND. 
- We connect the 5k Ohm resistor to the base, and the other end of the resistor to the push button switch. 
- Finally, we connect the push button switch to the 3.3V line again. 

We know that the voltage drop from base to the emitter is approximately 700mV. 
Further we apply 3.3V to the base over the 100k resistor. 
If we subtract the 3.3V - 0.7V, we get a voltage that will drop across the resistor of 2.6V. 
We can now divide those 2.6V by the 100k resistor, and get a flowing current IBE of 0.000026A. 
By multiplying this current with the factor hfe (100-800), we get a flowing collector emitter current of 2.86mA to 20.8mA. By using the proportionality constant we were able to spare the current limiting resistor in front of the LED. 

If we now push the button on our circuit, the IBE current is flowing, and the transistor becomes conductive between the collector and the emitter. Consequently, the LED lights up.  

#### Transcript 2
Now, let's do a similar example with the PNP transistor the BC557. 
For the PNP transistor (BC557) circuit, we'll create a high-side switching application to control the LED. Here's how you can set it up:

Needed Materials: 
1. 3.3V power source (such as a battery or a bench power supply)
2. Breadboard
3. BC557 PNP transistor
4. 10k Ohm resistor
5. Push button
6. LED (white)
7. Jumper wires

(Same materials before, but instead of the BC547 we use a PNP BC557 transistor)

Hook up:
1. Connect the positive terminal of the 3.3V power source to one end of the breadboard and the negative terminal to the other end.
2. Place the BC557 PNP transistor onto the breadboard, ensuring that its three pins are at three different breadboard lines.
3. Connect the emitter of the BC557 transistor to the positive rail of the breadboard.
4. Connect the collector of the BC557 transistor to the anode of the LED.
5. Connect the cathode of the LED to GND.
7. Connect the base to the 100k resistor.
8. Connect the other resistor end to the push button.
9. Connect the other end of the push button to the positive rail of the breadboard.

Demonstration: 
1. With the setup completed, the LED should be off initially since the transistor is in cutoff mode (no base current).
2. Press the push button to apply a positive voltage to the base of the BC557 transistor.
3. When the base voltage is applied, the transistor turns on, allowing current to flow from the positive rail through the LED to the emitter, and then through the transistor to ground. The LED should light up.
4. Release the push button to remove the base voltage, and the transistor will turn off, cutting off the current flow to the LED, causing it to turn off.

This demonstration showcases the high-side switching capability of the PNP transistor, allowing you to control the power to the LED from the positive side of the circuit.

## Level 10 - Induction 
### Lecture
As we continue our journey through electronic components, we now turn our attention to the inductor. 

We will begin by describing the magnetic field a bar magnet creates, which will pave the way for us to grasp the concept of electromagnetism. Subsequently, we will be ready to understand inductance and our next component - the inductor - and its applications in circuit design.  

#### Magnets
An electric charge creates an electric field that is an imaginary area in which another electric charge experiences a force - the coulomb force. There are positive and negative electric charges which can exist on their own.

Now, on the other hand, there are magnets. If we look at a bar magnet, we can see that each magnet has a magnetic North and magnetic South pole. Magnetic field lines travel from the magnetic North to the magnetic South pole.

If we now wanted to have only a magnetic South pole, one would think that by cutting a bar magnet in half, we would get exactly that. However, it turns out that if we cut a bar magnet in half, we get two bar magnets with magnetic South and North poles. We can't create a single magnetic South or a magnetic North pole. They always exist together. 

There are also ferromagnetic materials, like iron, which can become magnetic. In iron, grain boundaries form during creation, with each grain acting like a tiny permanent magnet facing in a random direction. Due to this randomness, there's no net magnetic field.

However, if we apply a large magnetic field to the ferromagnetic material, the grain's magnets align with the magnetic field. If the outside magnetic field is strong enough, the grain's magnets will be aligned even after we remove the external magnetic field. Now, the ferromagnetic material has become a magnet on its own. 

We can destroy its magnetic properties by heating the magnet, which randomizes the inner bar magnets again.

#### Electromagnetism
There's a connection between electricity and magnetic fields, which is called electromagnetism. 

Electrically charged particles that move create a magnetic field. When there's a current flowing through a wire, a magnetic field is created, which forms concentric circles around the wire.
We can determine the direction of such a field by using the right-hand rule, which states that by gripping the wire and aligning the thumb in the direction of the conventional current flow, the other fingers will show the direction of the magnetic field. 

The magnetic flux density given in the unit Tesla, gives us a rough idea of the strength of the magnetic field around a wire. 
$B = \dfrac{\mu_0*I}{2*\pi*r}$ ... magnetic field strength A/m or T
$\mu_0=4*\pi*10^{-7} \dfrac{H}{m}$  ... permeability of free space 
 
The strength of the field decreases with increasing distance from the wire and increases with increased current flow.

##### Electromagnetic Induction
So, we have seen that current in a wire creates a concentric magnetic field around the wire.
Conversely, a changing magnetic field can induce an electric current in a conductor. This process is known as electromagnetic induction.

One of the fundamental properties of a magnetic field is that it wants to remain steady. If we suddenly turn off our power supply, the magnetic field won't immediately be gone, as it wants to resist the change. Instead, it will slowly decrease. The magnetic field change leads to an induced current and voltage. The induction keeps the current flowing and induces a voltage, even though the supply is off.  

On the contrary, if we were to turn on the current again, the whole current wouldn't immediately occur because the magnetic field first needs to build up. In this case, an induced current and voltage in the opposite direction would be present before the magnetic field builds up entirely.

The wire stores energy in the form of magnetism. We characterize the ability of the wire (or any conductor) to store energy in the form of a magnetic field by a property called inductance, denoted as L and measured in Henrys (H).

Inductance is a measure of how effectively a conductor can store magnetic energy for a given current. It depends on factors such as the shape of the conductor, the number of turns in a coil, and the presence of a magnetic core.

We can calculate the induced voltage by multiplying the inductance with the change in current. 
$V = L*\dfrac{dI}{dt}$ ... Voltage

#### Inductors
We can increase the magnetic field of a conductor by creating many turns of wire to create a coil. The turned wire increase the inductive effect the magnetic field has, which forms the basis of our next component:
The inductor. 

Often, the inductor features a metal core, which increases the inductance further. 

The symbol of an inductor in circuit diagrams is typically represented as a series of loops or coils, reflecting its physical structure and function.

So, what are the use cases of the inductor that result from its properties?
A capacitor wants to keep the voltage steady, while an inductor wants a persistent current flow.  
If we turn off a flowing current, the inductor would continue to push electrons in the direction of the flow for a while. If we were to turn on the current, the inductor would hinder the electrons at first before the magnetic field is established. So, the inductor creates a lag in current changes, while a capacitor produces a lag in voltage changes. An inductor hinders instantaneous changes in current. 

And that's for what it's used. 
They're essential for maintaining steady current supplies, leveraging their energy storage capability in applications such as switching mode power supplies. Moreover, they're often combined with capacitors to form LC circuits, effectively reducing ripple in switched-mode power supplies, where ripple signifies periodic variations in direct voltage, typically stemming from deriving DC voltage from alternating current.

When implementing conductors in a circuit design, they have a few implications. 
First of all, they are relatively spacious compared to capacitors. Further, the magnetic field they create can influence nearby signal lines or integrated circuits, which must be accounted for when designing the layout of a printed circuit board (PCB). Finally, inductors can be influenced by applying a magnetic field to them. 

#### Summary
Magnetic field lines are always present in a closed loop. Therefore, there can't be a single magnetic North or a South pole. 

The interplay between electric charges and magnetic fields is called electromagnetism. 
Moving electric charges create a magnetic field. For example, current flowing in a wire creates a concentrical electric field around the wire. 
Further, if the magnetic field changes, current is induced in the wire. 

A magnetic field always wants to remain steady and stores energy.
If we turn on the voltage source so current can flow through a wire, the magnetic field induces a current and voltage in the opposing direction until the magnetic field is built up.
If we turn off the voltage source, the magnetic field also wants to maintain its current state and induces a current so it can continue to flow for a while. Consequently, an inductor creates a lag in current. 

If we were to create multiple turns of wire, we could increase this effect and create something that is called an inductor. We measure inductance in Henry.
Often, inductors feature a ferromagnetic metal core to increase the inductance even further. 
Ferromagnets are metals that become magnetic by applying a strong external magnetic field. 

We use inductors to store energy, to smoothen a current supply, or in company with a capacitor to create a stable DC from a switch mode power supply. When creating the layout, we must carefully consider their placement so that their magnetic field does not influence signal lines or integrated circuits, and so it isn't influenced by a magnetic field itself. 

### Example
In this demonstration, we'll explore how an inductor can continue to provide power to an LED even after disconnecting the power supply, utilizing the energy stored in the inductor's magnetic field.

To build this circuit, we need the following components:
1. A power source (5V)
2. A breadboard
3. A standard inductor (10mH)
4. An LED (any color)
5. A diode (1N4007 or similar, to protect the LED from reverse voltage)
6. A resistor (220Ω, to limit the current to the LED)
7. A push button
8. Jumper wires

Hook up:
1. Connect the positive terminal of the power supply (5V) to one end of the breadboard.
2. Connect the negative terminal (GND) to the other end of the breadboard.
3. Place the inductor (10mH) into the breadboard, ensuring one of its leads is connected to the positive rail
4. Connect the anode (longer lead) of the LED to the other end of the inductor.
5. Connect the cathode (shorter lead) of the LED to one end of the 220Ω resistor.
6. Connect the other end of the resistor to the negative rail (GND).
7. Place the diode in parallel to the inductor, LED, and resistor. 


- When we first connect the circuit to the power supply, the inductor will resist the change in current, and the LED will only slowly start to light up, as the inductor builds up its magnetic field. 
- After some time the magnetic field is at its maximum, and the LED lights fully. 
- When we disconnect the circuit from the power supply, the inductor will try to maintain the current flow due to its stored energy.
- This will cause the LED to remain lit for a short period of time as the inductor releases its stored energy.
- The diode that we included in this example is an optional safety measure. Inductive loads can create large voltage spikes in the reverse direction when suddenly disconnected from a power supply. To ensure that these reverse voltage spikes do not damage the LED, the diode has been inserted. A diode used in this way is referred to as a flyback diode.

## Level 11 - Crystal Oscillator 
### Lecture
Before we delve into examining model rocket flight computer circuits, it's crucial to grasp one last foundational technology: the basics of a microcontroller's timekeeping, the crystal oscillator.

Have you ever wondered how a clock keeps time? 
Since its origin, it has used some oscillator that marks the elapsing of one second by which it turns its pointers. The oscillator itself changed many times over the creation of the clock. At first, it used a pendulum. Then, something similar to a tuning fork, an LC circuit, and today, a piezoelectric crystal. 

Similarly to a watch, our integrated circuit also needs some impulse generator to control servos, read out sensor data, or transmit information through the air. 

#### LC circuit 
The first way to create timing is by using an LC circuit. 
Let's connect a charged capacitor to a resistor. 
As soon as the resistor is connected, the current becomes maximum as the voltage is highest at the beginning. The current then slowly decreases until the capacitor is uncharged.

Now, let's consider what happens if we replace the resistor with an inductor. 
The capacitor has a maximum voltage at the beginning and wants to create a maximum current. However, the inductor resists changes in current and induces a voltage in the opposite direction. Therefore, the current only slowly rises. 

The inductor builds up its magnetic field until the current reaches its maximum. Then, it decreases as the capacitor empties. However, this time, the inductor resists the current decrease and induces a voltage and current that wants to keep the flow going. The inductor pushes current into the capacitor and charges it again but in reverse polarity. Consequently, the current flow is in the reverse direction for the next half. The cycle begins again, and the current of an LC circuit takes the shape of a sine wave. This sine wave is the oscillator signal we have been looking for. 

In an ideal world, this oscillation would go on forever. However, there is some resistance in the circuit. So, it is an RLC circuit. The resistance gradually decays the amplitude until no oscillation is left. 

$V = L*\dfrac{dI}{dt}$ 

$I = C*\dfrac{dV}{dt}$ 

#### Piezoelectricity 
The piezoelectric effect is a phenomenon where a quartz crystal generates a voltage when subjected to mechanical stress. Conversely, if a voltage is applied across a quartz crystal, it undergoes elastic deformation. Upon removal of the voltage, the crystal returns to its original shape, generating a voltage in the process.

In a crystal oscillator circuit, this effect is harnessed by using the voltage signal generated by the quartz crystal. This signal is amplified and fed back to the crystal. The result is that the crystal oscillates at a precise resonance frequency, determined by the rate of expansion and contraction of the crystal. This resonance frequency enables the crystal to function akin to an RLC circuit but with significantly lower energy loss per cycle.

The symbol for a quartz crystal in circuit diagrams typically consists of a rectangle with two parallel vertical lines on each side. A horizontal line is connected to each of the lines, representing the pins. The rectangle itself symbolizes the quartz crystal element.

When selecting a quartz crystal component for a circuit, we can typically choose the resonance frequency from a range of options. Common resonance frequency options include frequencies such as 4 MHz, 8 MHz, 16 MHz, and so forth, depending on the crystal's intended use and the system's clock requirements.

When selecting quartz crystals, other factors to consider include frequency tolerance, temperature stability, and load capacitance. Load capacitors are often required in conjunction with the quartz crystal. These capacitors help stabilize the crystal's oscillation by providing the necessary capacitance for the circuit.
#### Summary
To ensure precise timing for communication protocols and integrated circuits, we commonly utilize quartz crystals. 

When a voltage is applied to a quartz crystal, it contracts and subsequently releases a voltage as it returns to its original state. By amplifying and feeding back this voltage output into the crystal, oscillation is achieved. This oscillation, characterized by the crystal's natural resonance frequency, is notably more power-efficient than other methods, as it minimizes energy loss per cycle.

When selecting a quartz crystal, we must select the resonance frequency, frequency tolerance, temperature stability, and load capacitance. Load capacitors are needed to stabilize the crystal's oscillation. 
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