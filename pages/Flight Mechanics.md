---
layout: page
title: Flight Mechanics
permalink: flight-mec
---
## Level 1 - Flight Forces 
People all over the world are building and launching model rockets. 

In conventional model rocketry, the success of a model rocket launch is usually determined by the altitude that is reached. 

The reached altitude is largely dependent on the following three aspects: the engine, the weight, and the aerodynamic shape of the vehicle. These aspects must be matched to each other for a conventional model rocket flight to be successful. 

### Weight
As you probably know there is a force that is acting on every object on Earth that is called the gravitational force. 

In its very basics form you might remember that it is calculated like this: 

$F_g = g * m$

$g \approx 9.81  \dfrac{m}{s^2}$ 

Where m is the mass and g is the local acceleration of free fall. 

This force must be overcome in order for the rocket to lift-off, and it is the primary impediment standing in our way to leave Earth. In fact, if it would have been even marginally higher, then escaping Earth would be impossible. On the other hand, if it would have been less, than life on Earth probably wouldn't have existed either. 

You might recognize that changing the local acceleration of free fall is impossible. So the only way to reduce the gravitational force, is to reduce the mass of the vehicle. This is why it is paramount in model and real rocketry **to make structures as light weight** as possible. 

In reality, the local acceleration is dependent on the location on Earth as well as the distance to the Earth's center of gravity. 

The approximation formula that was described above is derived from the following universal law: 
Between any two bodies of mass, there is a force that wants to attract the two bodies of mass to each other. 

The force can be calculation following  Newton's law of universal gravitation: 

$F = G*\dfrac{m_1*m_2}{r^2}$

$G = 6.67*10^{-11} \dfrac{m^3}{kg*s^2}$ ... Newtonian constant of gravitation 

This force depends on the masses of both bodies, as well as on the distance of the two bodies to each other. In most cases this effect can be neglected. However, Earth's and other Planet's mass is enormous. 

The formula also implies that the further our vehicle distances itself from Earth the less force it will have to overcome. 

### Drag 
We have been lucky that our planet come with an atmosphere that provides oxygen, regulates our planet's temperature, and protects us from solar radiation. 

Yet, when leaving Earth, it is the second obstacle that we have to overcome. 

Our atmosphere consists of gas and within this gas there are many different molecules. When travelling through our atmosphere our vehicle hits these molecules, and the faster our vehicle goes the more of these molecules it will hit at a certain time. These micro-hits will decelerate our vehicle, making it difficult to reach very fast speeds in our atmosphere. 

The force acting on our vehicle is calculated by the following formula:

$F_D = C_d*A*\dfrac{\rho * v^2}{2}$

It is dependent on 
- the density of the air, which will decrease with increased altitude. 
- the square of the speed with which our vehicle travels. 
- the area of our vehicle that faces in the direction of the speed. 
- and the drag coefficient $C_d$

Therefore, our rockets shall be designed in a way
- to reduce the front facing aera as much as possible. 
- and to feature an optimized aerodynamic shape to reduce the drag coefficient.

This is why most rockets, enclose all mechanisms, wires, and parts inside, feature smooth outside surfaces, and have a cone-shaped rocket tip. 

### Thrust
Now we know which forces will act on our vehicle. 
In order for the vehicle to lift-off, these forces must be overcome by the thrust force that the rocket engine creates. 

In the case of model rockets, solid rocket motor are used. These are comparable to the engine of a fireworks rocket. Once they are ignited, they burn until no full is left. 

#### Engine Classification
These engines are bought online and for every engine three characterisitics are usually given: thrust, burn time, and the thrust curve. 

The thrust indicates the average force the rocket engine will provide. Logically, this force shall be greater than the gravitational force that acts on the vehicle. 

The burn time indicates for how long the rocket motor will burn, which together with the thrust largely determines the altitude that can be reached with a certain engine. 

And finally, there is the thrust curve that represents the thrust over the burn time to gain an understanding on how the thrust of the engine will change over the burn duration. 

The area under the thrust curve is the total impulse. According to the total impulse solid rocket engines are classified from A all the way up to O.  The higher the letter in the alphabet the higher the total impulse will be. 

An A-class engine, for example, has a total impulse between 1.26 to 2.5 Ns.
There are multiple ways for a solid rocket engine to classify as A. 
An engine that has thrust of 2.5 Newton for 1 second for example has the same total impulse, as an engine that has thrust of 1 Newton and burns for 2.5 seconds. 

Still it is important which engine to chose, because with one of them the rocket might lift-off, while with the other, the gravitational force would be too high. 

#### Thrust to Weight Ratio
This is where the thrust to weight ratio (TTWR) comes into play. 

$TTWR = \dfrac{F_t}{F_g}$

It indicates the ratio between the gravitational force to the thrust of the rocket engine. 
If it is larger than one, the rocket is expected to lift off, and the higher the ratio is the faster the vehicle will accelerate. 

### Activity 1
Calculate the gravitational force that is acting on the Apollo lunar lander standing on the Moon. 

$m_{Lander} = 14,696 kg$
$m_{Moon}= 7.35*10^{22} kg$
$r_{Moon} = 1,737.4km$

### Activity 2
Select the class of the solid rocket engine that would be required for the lunar lander to be able to hoover above the ground. Assume a burn time of around 1 second. 

| Engine Class | Total impulse [Ns] |
| ------------ | ------------------ |
| M            | 5,120 - 10,240     |
| N            | 10,240 - 20,480    |
| O            | 20,480 - 40,960    |
| P            | 40,960 - 81920     |
## Level 2 - Passively vs actively stabilized flight
### Center of gravity
### Center of pressure
### Passive stability

<iframe width="560" height="315" src="https://www.youtube.com/embed/H0uI2ab52DE?si=BxVhyr2O4vzXRvdw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Fins
### Active stabilization
#### Thrust Vector Control
#### Other Systems