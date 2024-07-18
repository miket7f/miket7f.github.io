---
layout: page
title: Electronics Integration
permalink: elec-int
---
#### Capacitor Formula Derivation

#### Electric Field
An electric field is an imaginary area in which electric charges experience a force. 
Every electric charge is surrounded by such an electric field.

$E=\dfrac{F}{q}$  given in  $\dfrac{N}{m}$

The force another charge experiences in the electric field is the coulomb force. We can insert q_1, which cancels with the nominator, and, therefore, see that the electric field only depends on the second charge and its radius to the first point charge. 

$E = \dfrac{1}{4*\pi*e_0}*\dfrac{q_2}{r^2}$

For a point charge, we the electric field strength decreases with an increased distance.

If we now were to draw a surface inside this electric field, we could determine something that is called the electric flux. The electric flux basically represents the amount of field lines that pass through a given surface: 

$\phi_E = E*A$ ... Electric flux in $\dfrac{N*m^2}{C}$
$A$ ... Surface through, which the electric field lines pass
$E$ ... Electric field 

When we know the electric flux, we can determine the charge Q by applying the first Maxwell law. 
$Q = \epsilon_0*\phi_E$
$ε_0 = 8.85*10^{12} \dfrac{F}{m}$ ... Vacuum permittivity 

Armed with all that knowledge, we can now mathematically derive the functional principle of a capacitor. 

We know that the capacitance is defined as:
$C = \dfrac{Q}{U}$  

Further, we know that the electric potential difference is work divided by the charge: 
$U = \dfrac{W}{Q}$

We can reformulate this to get the work out of a charge and a potential:
$W = U*Q$
In our case the electrons want to move from the negative plate to the positive. 
This willingness to move from the negative to the positive plate, basically represents a stored energy in the capacitor plates. 

On the other hand, we have a distance d, between the two capacitor plates that must be overcome. 
Work is also defined as:
$W = F*d$
d ... Distance

We also know that a particle experiences a force in the electric field:
$F = E*Q$

and we know that the electric field between two capacitor plates is constant. 
$W = E*Q*d$

Now, we can say that the stored energy of the capacitor must be the same as the energy that must be overcome to travel from one plate to the other. 
$W = U*Q= E*Q*d$

By crossing out the charge, we acquire that the voltage between the two plates only depends on the electric field and the distance between the two plates. 
$U= E*d$

For a charge Q we can insert $Q = \epsilon_0*E*A$. 
So, we get:

$C = \dfrac{Q}{U} = \dfrac{\epsilon_0*E*A}{E*d}=\dfrac{\epsilon_0*A}{d}$  

So, the capacitance of a capacitor only depends on the area of the plate, and on the distance of the two plates to each other. 

The capacitance of a capacitor can be significantly increased by putting a dielectric between the two plates. A dielectric decreases the strength of the magnetic field by a certain factor, which enables the plates the receive a higher charge per voltage. 

For a capacitor with a dielectric we add the relative dielectric number:
$C = \dfrac{\epsilon_r*\epsilon_0*A}{d}$  

$ε_0 = 8.85*10^{12} \dfrac{F}{m}$ ... Vacuum permittivity 
$\epsilon_r$ ... relative dielectric number 

Electric potential is the work needed to move a charged particle of 1 coulomb from infinity to a certain distance from another charged particle. 

You might recall that work defined in classical physics is:
$W = F*s$
The force times the distance. 

We can apply this formula to calculate the required work to move a charged particle from one point to another. We know that the Coulomb force between them increases with closer proximity.  

At point 1, the force will be: 
$\dfrac{1}{4*\pi*e_0}*\dfrac{q_1*q_2}{r_1^2}$

While at point 2, the force will be: 
$\dfrac{1}{4*\pi*e_0}*\dfrac{q_1*q_2}{r_2^2}$

We also know the distance over which we move our charge, which is r_2 - r_1.

The force will gradually change over the entire distance. Therefore, we have to use the geometric average to calculate the force. 

$W = \dfrac{1}{4*\pi*e_0}*\dfrac{q_1*q_2}{r_1*r_2}*({r_1-r_2}) = \dfrac{1}{4*\pi*e_0}*q_1*q_2*(\dfrac{1}{r_1}-\dfrac{1}{r_2})$

Now, we know the work needed to move a charged particle q_2 to q_1 from the distance r_2 to r_1. However, remember that the electric potential is defined as moving a charge of q = 1C from infinity to radius r_2. 
This means that we have to divide the work by the charge q_1 and insert infinity for r_1 to get the electric potential. 

This results in the electric potential:
$U = \dfrac{W}{q}$

$U = -\dfrac{q_2}{4*\pi*e_0}*\dfrac{1}{r_2}$   with the unit by $\dfrac{J}{C}$ Joule per Coulomb or $V$ Volts 

#### Capacitor Formula
Now, you may wonder how the capacitance is correlated to its physical layout. For that, the capacitor formula comes into play:

$C = \dfrac{\epsilon_r*\epsilon_0*A}{d}$  

As you can see, the capacitance increases with increased plate area. The larger the plates, the more electrons or cations will fit onto the plate. 

On the other hand, the capacitance increases by decreasing the distance between the two plates. The electrons on the negatively charged plate are attracted to the cations on the positive plate. The closer the plates, the larger the attraction, which means that more charges will occupy the plates. 

The material between the two plates will also modify the electric field's strength. The epsilon zero in the formula represents the assumption that we have a vacuum between the two plates. 
$ε_0 = 8.85*10^{12} \dfrac{F}{m}$ ... Vacuum permittivity 

However, in most cases, we have a dielectric between the two plates. 
A dielectric decreases the strength of the magnetic field by a factor, which enables the plates to receive a higher charge per voltage. 

The dielectric's effect is represented by the relative permittivity.
$\epsilon_r$ ... relative permittivity 

#### Homogenous Electric Field
Something we did not discuss yet, is the electric field. An electric field is the area around an electric charge, in which other electric charge experiences a force. 

The electric field of a point charge is essentially the Coulomb force experienced by another charge, divided by the magnitude of that charge. As the distance from the point charge increases, the strength of the electric field decreases.

$E=\dfrac{F}{q}$  and it is given in  $\dfrac{N}{m}$

where E is measured in Newtons per Coulomb (N/C), F is the force, and q is the charge.

Our two capacitor plates are also electrically charged, which means that they too have an electric field. However, the circular field lines of the individual charges overlap and result in field lines that are parallel to each other. 

At any point between those two plates, an electric charge would experience the same force. We call such an electric field a homogenous electric field. 

