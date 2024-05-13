---
layout: page
title: Electronics Basics
permalink: elec-design
---
## This path is work in progress!
The material that we provide in the following levels is by now means complete but it might help you to learn about the subject yourself, while we are working on providing content for you! 

## Level 1 - Introduction to the Electronics Path

### Video Transcript 
We know you are eager to develop your own flight computer right away. However, we have to get you set up with the fundamentals first. Trust me, I have been there, designing my first flight computer without caring about the fundamentals, and well I can tell you that my design didn't work out as planed. 

For you to get the best understanding of circuit design possible, we have to start all the way at the beginning. We will start within the atom and take a look on an even smaller unit - the electron. Then, we will zoom out and take a look on how multiple electrons interact with each other. We will learn about the force that acts between them, will describe what an electric field is, and look at the concept of electric charge. Further, we will learn about conductivity, electric potential and the concept of the electric current. 

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
This is why the electrons are attracted to the nucleus. The force that acts between them is called the electrostatic force. 

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

#### The Coulomb Force

The force that is present between two charges is called Coulomb force. This force is calculated after the this formula: 

$F_C = \dfrac{1}{4*\pi*e_0}*\dfrac{q_1*q_2}{r^2}$

As we can see, the force decreases with increased space between them. Further, it increases with the charge of the elements. The larger the charge, the larger the force, and the greater the distance, the lower the force. 

The factor in front, also features the vacuum permittivity constant that is given in farad per meter. 
$ε_0 = 8.85*10^{12} \dfrac{F}{m}$

#### Electric Fields
An electric field is an imaginary area in which electric charges experience a force. 
Every electric charge is surrounded by such an electric field.

$E=\dfrac{F}{q}$  given in  $\dfrac{N}{m}$

The force another charge experiences in the electric field is the coulomb force. Therefore, we can insert q_2, which cancels with the nominator. We, therefore, see that the electric field only depends on first charge and the radius to it. 

$E = \dfrac{1}{4*\pi*e_0}*\dfrac{q_1}{r^2}$
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
To make up the materials that we know from our day to day life, atoms bond with each other to form something bigger. The can bond with each other through different forms. Metals, for example, bond with other non-metals through a ionic bond. Non-metals bond with each other through covalent bonds. And metals bond to each other through a metallic bond. 

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


## Level 5 - Voltage
### Video Transcript
Now we know that electrons can flow inside a metal, and the flow-rate is electric current. However, you may ask why this movement occurs?

The invisible force that pushes the electrons from of the battery into the other is called the voltage. The higher the voltage, the more electrons will flow from one end of the battery to the other. 

This is quite simplistic and describes what the voltage does, but not how it is defined. 
The voltage is defined as the difference in electric potential energy between two points. 

Now this might sound terrifyingly complex to some of you. 
So let's break it down. 

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

The electric potential is defined as moving a charge of q = 1C from infinity to radius r_2. 
This means that we have to divide the work by the charge q_1 and insert infinity for r_1 to get the electric potential. 

$U = \dfrac{W}{q}$

$U = -\dfrac{q_2}{4*\pi*e_0}*\dfrac{1}{r_2}$   with the unit by $\dfrac{J}{C}$ Joule per Coulomb or $V$ Volts 

#### Voltage
We first learned about the force that is present between charged particles the Coulomb force in order to be able to describe the electric field, which is an imaginary area in which a force is acting on another charged particle. The further away the second charge the lower the force. The lower the single chargers, the again the lower the force. 

Now, we can do an experiment were we move a charge from a point 1 to a closer point 2. We know that the force at the closer point 2 must be larger as the force in point 1. Further, we also covered a distance of (r_1 - r_2) while moving from point 1 to point 2. So we have an occurring force F and moved a certain distance s, which means that our charge conducted work. 

This work can be calculated and we arrived at the above described formula. Electric potential is the work that is required to move a point charge q to a certain point 2, but not from a point 1 but from infinity. Further, when describing the electric potential, one of the two point charges is assumed to have exactly one Coulomb. 

We learned about all those concepts, only to be able to describe the term voltage, which you definitely already heard about. The voltage is the electric potential difference between two points.


Conventional vs actual flowing direction. 

Volts push currents in an electric circuit
Behaves like a pushing force
A chemical reaction that creates a voltage

## Level - Resistance

## Level - Kirchhoff's Laws

## Level - The Capacitor

## Level - P-N Junction
## Level - The Diode
## Level - The Transistor

## Level - Electric Induction
## Level - Inductor


