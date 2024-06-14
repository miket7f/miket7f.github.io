---
layout: page
title: Flight
permalink: flight
---
## This path is work in progress!
The material that we provide in the following levels is by now means complete but it might help you to learn about the subject yourself, while we are working on providing content for you! 

## Level 1 - Sensors
### Lecture
Sensors are our sensory organs of our flight computer. With the help of them we can determine our rocket's orientation, its acceleration, velocity, and position, as well as its altitude. 
Based on the input of our sensors, our rocket can make informed decisions about steering the engines, deployment mechanisms, or aborting the flight. Further, they help us to analyze our rocket flights by storing their data. 

We will discuss the four most vital ones for model rocketry: 
the gyroscope, the accelerometer, the barometer, and the voltmeter. 
At the end we will briefly talk about other sensors that could be beneficial for your projects. 
## Level 2 - Gyroscope
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

## Level 3 - Accelerometer
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

## Level 4 - BMI088 Implementation
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
## Level 5 - BMP388 Implementation
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

## Level 6 - Voltmeter
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

## Level 7 - Other Sensors
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
