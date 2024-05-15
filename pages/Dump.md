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