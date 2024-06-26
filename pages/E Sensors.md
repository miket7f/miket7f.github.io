---
layout: page
title: Flight
permalink: flight
---
## This path is work in progress!
The material that we provide in the following levels is by now means complete but it might help you to learn about the subject yourself, while we are working on providing content for you! 

## Level 1 -  Gyroscope
<iframe width="560" height="315" src="https://www.youtube.com/embed/dm8qmzwrdJI?si=rGth4ZI4xDmzJ54Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Sensors are the sensory organs of our flight computer. With the help of them, we can determine our rocket's orientation, its acceleration, velocity, and position, as well as its altitude. 
Based on the input of our sensors, our rocket can make informed decisions about steering the engines, deployment mechanisms or aborting the flight. Further, they help us to analyze our rocket flights by storing their data. 

We will discuss the four most vital ones for model rocketry: the gyroscope, the accelerometer, the barometer, and the voltmeter. After we finish the gyroscope and accelerometer, we will look at the implementation of an inertial measurement unit IMU. After we are done with the barometer, we will look at its implementation. At the end, we will briefly talk about other sensors that could benefit your projects. 

The first and most vital sensor for advanced-model rockets is the gyroscope. It is the main sensor with which we can determine the orientation of our vehicle. At this level, we will learn about its function principle, how we can determine orientation based on its data, and the parameters we have to watch out for when acquiring our sensor.

##### Function Principle
The gyroscope determines the angular rate based on the Coriolis effect. The Coriolis effect dictates that when a mass is in motion within a rotating reference frame, a force arises perpendicular to both the mass's direction of motion and the rotation axis of the frame. This force, known as the Coriolis force, induces a distinct displacement or deflection in the moving mass. 

The gyroscope has an oscillating mass inside that moves along a predefined axis. Now, if this component is rotated, we have a rotating frame of reference, which results in a displacement of the mass that is caused by the Coriolis force. The faster the rotation, the stronger the Coriolis force and the greater the displacement. This displacement changes the capacitance between two plates, and this capacitance change is measured and then translated into a rotation change - the angular rate. 

##### Determining Orientation
For determining the rocket's orientation, we need a total of three gyroscopes, each along a different axis in the coordinate system. One that measures angular rate around the pitch, one 
around the yaw, and one around the roll axis. 

To now determine the orientation of the vehicle, we take this orientation change, multiply it by the elapsed time, and add it to the previous orientation value. We integrate the angular rate to get an absolute orientation. However, this only works if we rotate the rocket about one axis. As we have three-dimensional orientations, we have to use a 3D rotation representation, such as Euler angles or Quaternions. These concepts are further discussed in the software path.

##### Parameters
Next, we will focus more on the gyroscope itself. 
When we look at a gyroscope's datasheet, it often indicates the following properties of the gyroscope, which we should understand. 

First, the operating range gives the maximum angular rate the gyroscope can measure. An operating range from +-2000°/s means that it can't record any faster angular rates than that. 

A second property of the gyroscope is its resolution given in bits. A 16-bit gyroscope would divide the entire angular rate range into 2^16 values. Resolution shall not be confused with accuracy. A higher resolution does not necessarily result in higher accuracy. It simply suggests that the gyroscope outputs more digits to work with. But, whether or not the value is correct depends on the accuracy. 

Accuracy ratings are mostly not given directly in a gyroscope datasheet, as they depend on multiple factors. Instead, the datasheet provides several parameters that indirectly represent the gyroscope's accuracy. 

One is the temperature-coefficient offset (TCO), which describes how the measured angular rate changes with temperature. A TCO of ±0.015 °/s/K means that for each degree Kelvin (or Celsius) increase in temperature, the gyroscope's measured angular rate can become inaccurate by ±0.015 °/s. As the temperature changes, the bias or zero-rate output of the gyroscope can drift, leading to inaccuracies in the angular rate measurement.

The second factor is the zero-rate offset, which describes the static error of a gyroscope. Most gyroscopes come with an offset in angular rate from the factory. An offset of ±1°/s means that the gyroscope's reading can be off by 1°/s from the actual angular rate even when stationary. This offset is constant, and we can calibrate the gyroscope to compensate for when determining orientation.

Next is the noise density. It is a measure of the random noise in the gyroscope's output. The smaller the noise density, the smaller the angular rates we can detect. A value of 0.014 °/s/√Hz means that the gyroscope has a noise level of 0.014 °/s for each square root of the bandwidth in Hertz. This low noise density allows for more precise detection of small angular rate changes, improving the overall accuracy of the measurements.

So, the gyroscope's accuracy mainly depends on the zero offset, the TCO, and the noise density. 

Gyroscopes often feature bus connections like SPI or I2C to interface them with a microcontroller. Additionally, they frequently feature interrupt pins that indicate to the microcontroller when new data is ready. An interrupt for new readings of the angular rate is especially important because the microcontroller needs to integrate the real-time data as soon as possible.

Remember, the microcontroller calculates the change in orientation by multiplying the angular rate change by the elapsed time. If the elapsed time is incorrect, the determined angle will become inaccurate. Therefore, timely data integration is crucial for maintaining accurate orientation tracking.

Another property of a gyroscope is its ODR output data rate. It states the number of data sets the sensor outputs per second in Hz. 

A disadvantage of the orientation determined by the gyroscope is that it isn't a direct measurement but the integral of the angular rate. Therefore,  a slight error in the angular rate results in an offset in the orientation. If the slight error in angular rate is single-sided, the orientation result deviates from the real orientation over time. 

##### Calibration
A zero offset and the TCO alone would, therefore, cause the orientation readings to become inaccurate in no time. Consequently, we have to calibrate gyroscopes before use. While calibrating, the gyroscope sits still, and the angular rates are measured and averaged. In ideal circumstances, the angular rate should be zero if the gyroscope is static. We subtract the measured average from the angular rate. If we conduct the test again, the gyroscope's angular rate reading in a static condition will be approximately zero. Unfortunately, it is not possible to eliminate drift. Depending on the gyroscope's characteristics, there is a limit to how far we can go with calibration. With good calibration, we can achieve orientation accuracy of several minutes. 

#### Summary
Gyroscopes measure angular rate using the Coriolis effect. They feature an internal oscillating mass. As this mass is in motion, a rotation causes the Coriolis force to displace it. This displacement changes the capacitance of two plates, which is measured and translated into the angular rate.

We use three gyroscopes to measure the rocket's orientation, each measuring angular rate along a different axis (pitch, yaw, and roll). The angular rates are integrated over time to calculate the total change in orientation, often represented using Euler angles or Quaternions.

**Key Parameters**:
- **Operating Range**: The maximum angular rate the gyroscope can measure.
- **Resolution**: The division of the angular rate range into discrete values, typically given in bits.
- **Temperature-Coefficient Offset (TCO)**: The change in measured angular rate with temperature variations.
- **Zero-Rate Offset**: The static error in angular rate measurement when the gyroscope is stationary.
- **Noise Density**: The level of random noise in the gyroscope's output, affecting the detection of small angular rate changes.
- **Output Data Rate (ODR)**: The number of data sets the gyroscope outputs per second.

We must calibrate gyroscopes to account for zero offsets and TCO. During calibration, the gyroscope measures and averages angular rates while stationary, and this average is subtracted from future readings to improve accuracy.

## Level 2 - Accelerometer
<iframe width="560" height="315" src="https://www.youtube.com/embed/eT_AuN07kJs?si=Z81385Q_rrmwtbun" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>+
### Lecture
Another way though for rockets not as important way to determine orientation is by the means of an accelerometer. It measures the total acceleration acting on the sensors internal mass.

At this level, we will also learn about its function principle, how we can determine orientation based on its data, and the parameters we have to watch out for when acquiring our sensor.

##### Function Principle
Every mass has a moment of inertia. Its moment of inertia resists a change in speed, similarly to how a capacitor resists a change in voltage or an inductor resists a change in current. If a mass is accelerated or decelerated, the mass experiences a force in the opposite direction - the inertia force. Let's assume we hang a ball on a string inside this mass. An external acceleration on the mass, would cause a deflection of the ball against the direction of the acceleration. 

An accelerometer takes advantage of this exact principle. Within the component, a mass can freely move along one axis. In the case of accelerations, its moment of inertia resists change, and the inertia force displaces the mass from the center. Again, the accelerometer measures the displacement by the capacitance, and then the displacement is converted to acceleration. 

##### Determining Orientation
We have to use a 3-axis accelerometer to determine the vehicle's orientation. Now, if the rocket sits at the launchpad, the only acceleration that is present is Earth's gravitational acceleration. If the object is perfectly upright, we can measure the gravitational acceleration along a single axis. However, if it is not perfectly upright, the sensor will detect components of the total gravitational acceleration along its axes. We can determine the rocket's orientation by knowing the ratios between those components.

The problem with the accelerometer arises while powered ascent. The rocket engine provides thrust higher than the gravitational force to accelerate the vehicle and to make it lift off. The gravitational acceleration always points downwards to Earth's center from the rocket's COG. The acceleration by the engine's thrust, on the other hand, is in line with the rocket engine that sits inside the thrust vector control mount. Consequently, the resulting acceleration of the two becomes highly unpredictable, as it depends on the orientation of the vehicle, the thrust of the engine, and the angle of the thrust vector control system. As the total orientation isn't pointing to the Earth's center anymore, we can't determine the orientation based on these measurements in flight. Further, even if we could, the accelerations are also caused by vibrations during rocket flight. 

You may wonder why drones can use an accelerometer for determining orientation. But that is simple. When drones hover, they experience minimal acceleration, and even when moving, their accelerations remain relatively low. 

##### Parameters
Accelerometer's datasheets feature the same kinds of parameters as the ones of gyroscopes.
There's the operating range, which is this time given in g. A rating of +-3g would represent an acceleration measurement range of approximately three times Earth's gravitational acceleration - around 3x9.81m/s^2. The resolution is also given in bits and splits the operating range into values. 

The accuracy also heavily depends on the zero offset in mg/K, the TCO in mg/°/K, and the noise density in μg/√Hz.

We also interface Accelerometers with protocols such as I2C and SPI. Further, they also feature interrupt pins and have an output data rating.

#### Summary
Accelerometers measure acceleration by utilizing the principle of inertia. A mass inside the accelerometer, when accelerated or decelerated, experiences a force due to its inertia. This force displaces the mass, which is then measured via capacitance changes. The displacement is converted into acceleration data.

By analyzing the ratios of gravitational components along different axes, the rocket's orientation relative to the Earth's center can be inferred. However, during powered ascent, unpredictable accelerations due to engine thrust and vibration make orientation determination challenging.

The parameters listed in accelerometer datasheets are quite similar to those found in gyroscopes. However, the operating range for accelerometers is specified in g-forces, representing multiples of Earth's gravitational acceleration.

## Level 3 - BMI088 Implementation
<iframe width="560" height="315" src="https://www.youtube.com/embed/Ke1CmTQ54lY?si=PhJY7yjby85cw2to" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Both ways of determining orientation come with their own sacrifice. 
Gyroscopes tend to drift over time due to their indirect nature, while accelerometers are prone to vibrations and are difficult to use while powered ascent. 

Drones are able to use accelerometers to determine orientation as they do not have those high accelerations that are present in rocket flight. However, they still use both types of sensors and fuse them in order to get the most accurate results. They use the accelerometer data to correct the gyroscope drift, while filtering out the noise from the accelerometers. The two sensors perfectly complement each other for drone applications. 

At this level, we will look at such a sensor packet or IMU (inertial measurement unit) - the BMI088 from Bosch and its implementation. 

##### The Sensor
The BMI088 is a 6DOF sensor. DOF refers to the number of measured axes and stands for six degrees of freedom. The BMI088 features a tri-axial gyroscope and a tri-axial accelerometer. 

Both have a digital resolution of 16-bit. The accelerometer can output data in steps of  0.09mg, while the gyroscope gives its readings in steps of 0.004°/s. 

We can select the operating ranges for both the accelerometer and the gyroscope. The accelerometer's setting ranges from +-3g up to +-24g. We predominantly chose a lower g setting, as we do not expect high accelerations. The gyroscope's setting ranges from +-125°/s to +-2000°/s, with our usual choice being +-500°/s. It's important to consider that increasing the operating range reduces the sensor's resolution.

The zero offset for the accelerometer is +-20mg, and for the gyroscope it is +-1°/s.
The TCO is +-20mg for the accelerometer and +-0.015°/s/K for the gyroscope.
The noise density is 175 μg/√Hz for the accelerometer and 0.014 °/s/√Hz for the gyroscope. 
We can also adjust the output data rate of the BMI088 and select anything between 12.5Hz to 2kHz. 

The BMI088 allows for SPI and I2C interface and features a total of four interrupt pins. 

Its high resolution, low noise, wide operating range, and flexibility in output data rate make it capable of providing precise and reliable motion data for accurately determining orientation. 

##### Datasheet
To implement the BMI088, we have to turn to its datasheet. Don't be overwhelmed by the information such a document provides. We do not have to understand all 62 pages to integrate a sensor like this. Often, the maximum ratings, the pin-out, and the configuration diagram are enough to implement the sensors. 

If we turn to page 52, we can see which functions are taken on by which pins. Pin one, for example, is the second interrupt pin of the accelerometer. Pin 3 is one of the supply voltage pins, and so on. On page 53, we see typical connection diagrams for the sensors. As you can see, we can connect the BMI088 by SPI or I2C. I usually like to connect sensors by SPI due to the faster communication speeds. 

##### Power Supply
To hook up the BMI088, we connect +3.3V to all VDD and the VDDIO pin. Further, we attach the GND and GNDIO to 0V or GND.

We should connect NC to the ground to omit floating pins, as recommended. To provide stable input voltage for the IC, we should add two 100nF capacitors as close as possible to the VDD pins of the BMI088. 

For my designs, I like to add two bigger 10uF capacitors to compensate for the ripple voltage of our power supply. 

The PS pin (protocol select pin) is needed to indicate via which bus protocol our microcontroller wants to communicate with the sensor. By pulling it low, we select SPI. By pulling it high, we chose I2C.

##### SPI Connection
You already understand the SPI interface, so it should be straightforward to connect the sensor to the interface:
- SCK to SCK, 
- MOSI to sensor data in (SDI)

Even though the accelerometer and the gyroscope sit in a combined housing, we could use both individually. There are even two distinct sensor data out pins (SDO1 and SDO2) on the sensor. Yet, as only one of them can communicate at a time, it is perfectly reasonable to connect them to the same MISO. 

To tell the sensor whether our microcontroller wants to address the accelerometer or the gyroscope, we add two different chip-select pins. 

##### Interrupts
The BMI088 sensor offers several operating modes and features two interrupt pins each for the accelerometer and gyroscope:

Each sensor can be configured to use one of its interrupt pins to signal when new data is ready. For instance, one pin could indicate accelerometer data readiness, while the other pin signals gyroscope data readiness. This setup allows the microcontroller to read each sensor's data independently, based on their individual speeds.

Alternatively, both sensors can be synchronized so that a single interrupt pin indicates when both accelerometer and gyroscope data are ready. This synchronization ensures that the microcontroller receives data from both sensors simultaneously.

Another operational mode of the BMI088 is FIFO (First In, First Out). In FIFO mode, the sensor accumulates accelerometer and gyroscope data into a buffer along with timestamps. This storage method allows the microcontroller to access many time-stamped data sets at once without the need for continuous polling them individually. An interrupt can be set up to signal when the FIFO buffer reaches capacity or nears capacity.

Typically, we use the separate data-ready interrupt mode with two interrupts—one for each sensor—especially as real-time gyroscope data is critical. The main advantage of having access to four interrupt pins is that we can choose either one of the two interrupts for both sensors that suit our wiring best. 

#### Summary
The BMI088 is a 6 degrees of freedom (DOF) inertial measurement unit (IMU) that integrates a three-axis accelerometer and a three-axis gyroscope into a single package. The BMI088's accelerometer and gyroscope come with high resolution, low noise, wide operating range, selectable data rates, and support SPI and I2C interfaces. 

When connecting the BMI088 sensor, it's essential to supply 3.3V to the VDD and VDDIO pins, connect the GND pins to the ground, and include decoupling capacitors to ensure a stable power supply.

To select the communication interface, the protocol select (PS) pin is pulled low for SPI mode. For SPI communication, connections include SCK (clock), MOSI (master out slave in), MISO (master in slave out), and two chip-select (CS) pins.

The BMI088 features up to four interrupt pins (two for the accelerometer and two for the gyroscope) that signal data readiness or FIFO buffer status. Using these interrupts, data synchronization between the accelerometer and gyroscope can be managed efficiently, potentially reducing the need for multiple interrupt signals.

## Level 4 - Barometer
<iframe width="560" height="315" src="https://www.youtube.com/embed/iGVSC9UGHMM?si=ZD2nQCJX8Usuga47" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
When launching a rocket, we also want to know the altitude it reaches. One method for determining altitude in model rockets and drones involves using a barometer. A barometer measures both air pressure and air temperature to calculate altitude effectively. The use of a barometer is also the classic way in which drones determine their height. 

At this level, we will learn about the Barometer's function principle, altitude determination, and parameters. 

#### Function Principle
As altitude increases, the atmospheric pressure decreases. This relationship is due to the weight of the air above a given point in the atmosphere. The higher you go in altitude, the less air there is above you, resulting in lower atmospheric pressure. Therefore, we can use barometric pressure as an indirect measure of altitude.

Further, assuming all other factors remain constant, a gain in temperature results in an atmospheric pressure increase. This relationship is because warmer air molecules have higher kinetic energy, causing them to move more vigorously and exert more force per unit area on surfaces.

By knowing both characteristics of the air, it is possible to determine an approximate altitude by the barometric pressure equation. 

The barometer measures the air pressure by a membrane inside the IC that deforms under applied pressure. Through the deformation of the membrane, the resistance of the membrane changes. The single resistances of the single strain gauges are connected in a diamond-shaped configuration, which is in balance without deformation. As soon as the membrane is deformed, the resistance imbalance creates an electrically measurable derivation. This derivation is converted into pressure readings. 

The barometer IC needs to have direct access to the surrounding air. Hence, it is typically placed near an air inlet of the rocket for accurate pressure measurements.

In reality, these measurements are additionally influenced by air humidity (as humidity changes air density), diurnal pressure variations, and high and low-pressure zones that occur because of weather conditions. The absolute altitude readings are, therefore, only within a few tens of meters. However, if the environmental conditions remain relatively constant during test operations, a relative accuracy, which is more important to determine the reached altitude, can be accurate in the cm range. 

These changes in environmental conditions and the resulting inaccuracies can't be changed by the highest precision barometric pressure sensor. 

#### Parameters
Typical parameters that will be given when selecting a barometer are:
- the operation range, which gives you the pressure range in hPa your barometer will be able to measure. Air pressure ranges from 1013 hPa at sea level to 56hPa at 65km altitude. 
- the absolute pressure accuracy gives the pressure derivation from the actual pressure at sea level. It is most important if we want to determine the absolute altitude of any point. 
- the relative pressure accuracy outlines the inaccuracy for applications in which we want to determine the pressure change. It is most important to determine altitude during model rocket flight. 
- the noise in pressure gives the amplitude of random fluctuations in our measurement. 
- the temperature coefficient offset (TCO) clarifies the change in measured pressure based on the increased or decreased heat of the sensor. 
- the long-term stability (12 months) indicates the change in measured pressure over an extensive period. We can think of this measurement to be a long-term drift. 
- The sampling rate is the same as the output data rate on the IMUs. 

#### Summary
Barometers play a critical role in altitude determination. They measure the air pressure using a deformable membrane that alters electrical resistance with pressure changes, providing pressure readings. Further, they read the temperature of the environment. Based on those two characteristics, they can estimate the altitude by the barometric pressure equation. 

Key parameters for barometers include pressure range, absolute and relative accuracy, noise levels, temperature coefficient offset, and long-term stability. 

Environmental factors like humidity, diurnal pressure changes, and weather conditions can affect accuracy. However, these are not as detrimental for relative accuracy as for absolute accuracy. 

## Level 5 - BMP388 Implementation
<iframe width="560" height="315" src="https://www.youtube.com/embed/UZY3L5ofSPc?si=NSnP7XRaQG7A7roo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Now, at this level, let's look at a specific example of a barometer - the BMP388 from Bosch. By doing so, we will explore its properties and implement it in a circuit. 
#### Properties
The BMP388 incorporates a pressure and temperature sensor. When looking at its datasheet, we can evaluate the sensor's properties. 

It has an operation range from 300 to 1250 hPa, which is more than enough to cover our altitude range. Its absolute pressure accuracy is +-0.5hPa, which we could translate to a meter above sea level measurement with an accuracy of +-4m. The relative pressure accuracy is +-0.08hPa, which translates to an altitude measurement relative to a setpoint with an accuracy of +-0.66m. The setpoint will almost always be at the level of the launchpad, which makes the relative accuracy most important to determine the altitude or change in elevation. 

The BMP388 has a noise in pressure at the lowest bandwidth and highest resolution of only 0.03Pa. 
Its TCO is +-0.75Pa/K, and its long-term values over 12 months are still within +-0.33hPa - all of that with a maximum sampling rate of 200 Hz. 

The BMP388 allows for the classic 4-wire SPI and a remarkable SPI interface that only needs three wires. Further, it features an I2C interface and an interrupt pin. 
#### Oversampling and IIR
The BMP388 can run different oversampling modes (from none to 32 times oversampling) and can apply an IIR (infinite impulse response) filter (ranging again from none to 32).   

Oversampling improves the accuracy and resolution of measurements by sampling the input signal more frequently and then averaging these samples. The oversampling rate is adjustable. The higher the oversampling rate, the higher the power consumption, and the higher the resolution. However, as more samples are combined in a single measurement, the output data rate decreases with increasing oversampling. 

The IIR filter helps to smoothen the output data by reducing short-term fluctuations and noise, providing a more stable reading. The filter coefficient can also be set from zero to 32 and determines the strength of the filtering, with higher coefficients providing more smoothing. A stronger IIR filtering provides smoother data but may also introduce a slight lag in response to rapid changes in pressure or temperature.

We can set both the oversampling and the IIR individually for the pressure and the temperature sensor. 

#### Power Supply
The sensor is supplied with regulated 3.3V and is equipped with bypass capacitors on the power inputs to make the power supply more stable. Their capacitance is recommended to be 100nF, and the type should be of an SMD ceramic capacitor. 

#### SPI Connection and Interrupt 
The BMP388 will be implemented using the four-wire SPI interface, similar to the BMI088:
- **SCK to SCK**
- **MOSI to SDI**
- **MISO to SDO**
- **GPIO to CS**

Additionally, another GPIO pin will be connected to the interrupt pin to indicate when new data is ready.

#### Summary
The BMP388 integrates pressure and temperature sensing capabilities into a single package. 
It offers high accuracy for both absolute and relative pressure measurements, features low noise and maintains excellent long-term stability. It supports 4-wire SPI, optimized 3-wire SPI, and I2C interfaces, along with an interrupt pin for efficient data handling.

During implementation, it's essential to provide a regulated 3.3V power supply and incorporate 100nF SMD ceramic capacitors to ensure stable power delivery. Communication with the sensor is typically achieved using 4-wire SPI (SCK, MOSI, MISO, CS) for data exchange, with an additional GPIO pin used to signal interrupts when new data is available.

Additionally, the BMP388 allows adjustment of oversampling rates and configuration of an infinite impulse response (IIR) filter to enhance measurement accuracy. Oversampling improves resolution by averaging multiple measurements, while the IIR filter reduces noise and stabilizes sensor output.

## Level 6 - Voltmeter
<iframe width="560" height="315" src="https://www.youtube.com/embed/UZY3L5ofSPc?si=NSnP7XRaQG7A7roo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
Another practical sensor for model rocketry is the voltmeter. The voltmeter is intended to measure the battery's voltage level to ensure a sufficient power supply.

There are many ways in which we can measure the voltage of our LiPo battery. There are dedicated battery monitoring ICs available that protect against overvoltage, undervoltage, overcurrent, short-circuits, and even overtemperature. There are even battery fuel gauge ICs that do not only determine the battery's voltage but also its stored capacity. However, a simpler method for roughly determining the battery's voltage level involves using a voltage divider in conjunction with an ADC. We will look at this method at this level.

#### Voltage Divider with ADC
All of the three microcontrollers we previously discussed have their analog input pins. Most often, they work with an integrated analog-to-digital converter. However, the analog input pins of our microcontrollers only function in a range of 0 to 3.3V. If we were to apply a higher voltage to the pins, they would undergo permanent damage. Our 3-celled LiPo battery has a voltage range of 11.1V to 12.6V, magnitudes too high for the ADC to measure. 

However, there is a way to indirectly measure the battery's voltage level without damaging the ADC, done by a voltage divider. A voltage divider is a circuit consisting of two resistors put in series. To this divider, the battery voltage is applied. Now, we can calculate the equivalent serial resistance and divide the entire voltage by this value. What we get is the flowing current. By multiplying the current with the resistances, we get the voltage drop across the two resistors. The voltage drop across the resistors varies with the current, which again varies with the applied voltage. By selecting the correct resistor value, we can create a voltage of 0 to 3.3V for the input range of 0 to 12.6V across the bottom resistor to which we connect the ADC. 

#### Implementation of ADC Voltmeter
So, let's devise our first ADC voltmeter.
First, we have to determine the input voltage range that we want to be able to measure. Ideally, we would use a more extensive operating range and could go with 0-13.3V.

Then, we have to think about the lower voltage range that should be present at our ADC. In the case of our microcontrollers, our ADCs withstand around 3.3V. So, let's go with a lower voltage range of 0-1.88V. So, the battery voltage of 13.3V corresponds to the ADC-measured voltage of 1.88V. 

The next step is to select one resistor, based on which we can calculate the second resistor. It is crucial to know that the higher the resistance value we chose, the lower the continuous current consumption. A good value for the upper resistor could be 20kOhm, for example. 

We can calculate the voltage across the second resistor by determining the current times the second resistor. 
$V_{ADC}=\dfrac{V_{BAT}*R_2}{R_1 + R_2}$

Then, we can insert our maximum values, which are 13.3V for Vbat and 1.88V for the VADC, and the value for our first resistor. 
$1.88V*20000Ω = 13.3V*R_2 - 1.88V*R_2$

After that, we only have to extract R2 to one side and evaluate its resistance. 
$R_2 =\dfrac{1.88V*20000Ω}{13.3V-1.88V}=3292Ω$

Now, we have an ideal resistor value with which we can select an appropriate one. The next closest available is a 3.3kΩ resistor. 
By calculating the network again with this resistor, we conclude that 13.3V corresponds to 1.8836V. 
As you know, the value of the measured voltage range is given in a number. For a 12-bit ADC, a value of 4095 would correspond to the voltage level of 3.3V.

What battery voltage would correspond to 3.3V at the ADC? 
Let's determine the current by 3.3V/3300Ω=0.001A 
Then, multiplied by the equivalent resistance, we would 23.3kΩ * 0.001A = 23.3V. 
So, 3.3V at the ADC corresponds to a battery voltage of 23.3V.

Therefore, we can calculate the battery voltage by dividing the numeric number x by the maximum number 4095. We know that the maximum number corresponds to 23.3V and that the relationship between X and the maximum number is linear. 

$V_{BAT} = \dfrac{n_{ADC}}{4095}*23.3V$

However, keep in mind that both resistors are not ideal and do have a slight offset of their ideal resistance. Consequently, we have to calibrate our resistor divider before the first use. 
To do so, we measure the battery voltage of the LiPo with a multimeter and compare the measured voltage with the voltage our voltmeter estimated.

$f_{COR} = \dfrac{V_{ACTUAL}}{V_{VOLTMETER}}$

We can calculate the deviation of the two values and receive a factor, with which we will multiply our results in the software. 

$V_{BAT} = \dfrac{n_{ADC}}{4095}*23.3V*f_{COR}$

#### Summary
We can indirectly measure the battery's voltage through our microcontroller's IC by utilizing a voltage divider circuit. To do so, we must carefully select the voltage divider's resistors to stay within the ADC voltage ratings. The maximum voltage of the battery should not exceed the maximum ADC voltage rating at the pin. 

After we have selected the resistors, our microcontroller's ADC pin measures a voltage. This voltage is translated to a numeric value, which we translate back to the battery's voltage through the divider circuit. At first, this calculation will be off by a certain amount as the resistor values might be off slightly. Therefore, we have to calibrate the formula and account for the offset. 

Just like that, we have created a simple battery voltage gauge. 
If you require more accurate readings of the battery's charging state, there are specialized fuel gauge or battery management ICs with which you can do so. 

## Level 7 - Other Sensors
<iframe width="560" height="315" src="https://www.youtube.com/embed/YSCpfo2fhkw?si=foiJwllgt3x36UVM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
### Lecture
While we discussed the four most vital sensors that most advanced model rockets will need (the gyroscope, accelerometer, barometer, and voltmeter), there are many more that you may require on your own project or flight computer. 

Two more sensors that can be especially useful are the magnetometer -another sensor for determining the rocket's orientation and the GNSS receiver - a GPS module to determine the rocket's position in 3D space. We will briefly explore these sensors in a little more depth and note a few more sensors that might be helpful in your projects.

#### Magnetometer
A magnetometer is the third way to determine the rocket's orientation. A magnetometer measures the magnetic field that is present in its environment. As you know, Earth has a strong magnetic field that is measurable. We can think of the Earth as a bar magnet with magnetic field lines that range from the magnetic North to the magnetic South pole. The magnetometer can measure these magnetic field lines and their direction. Based on these measurements, it can estimate its orientation. You can think of a magnetometer to be similar to a compass. 

We use a 3DOF (Degrees of Freedom) magnetometer to determine orientation. We can think of it as having three compasses around three different axes. Through that, we know exactly where the magnetic field is coming from. As the magnetic poles do not suddenly change, we can determine the vehicle's orientation based on these measurements. 

However, the problem with a magnetometer is that other magnetic fields can render the magnetometer's measurements useless, just as the accelerometer becomes useless when thrust is present. The biggest concern why we haven't yet incorporated a magnetometer into our designs is that our voltage regulation circuit features an inductor. This inductor creates a strong magnetic field, which would impede the magnetometer. 

Yet, if you carefully consider the magnetometer implementation in your PCB design, your project might benefit from adding this type of sensor! 

#### GNSS Receiver 
nother crucial sensor is the GNSS receiver. 
GNSS stands for Global Navigation Satellite System. 
As the name suggests, this system allows users on Earth to determine their position in 3D dimensional space on Earth. This location is done by a satellite constellation that usually sits in GEO (geostationary orbit). The GEO orbit is notable as the satellites in this orbit are in sync with the Earth's rotation, which means that they always cover the same regions. 

For it to work, the device that wants to determine its position has to connect to at least four satellites. The satellites know their own location and feature exact timing. These satellites can now send their location and time data to the device that wants to determine its location. The device also can keep track of the current time and calculate the elapsed time between when data was sent and when it was received. Based on this time difference, it can calculate the distance to the satellite, as the device knows the speed at which the information travels. Now, one distance alone does not determine the position in 3D space. The device can only determine where it sits in 3D space by repeating this process with two more satellites. 

We can visualize a sphere around each of the satellites with a radius equal to the measured distance. The point where the spheres from the three satellites intersect is the position of the device. While three satellites are theoretically sufficient for determining position, as previously noted, the device itself must accurately maintain its current time. For precise timing information, a fourth satellite transmits the current time.

GNSS satellites all feature nuclear clocks with tremendous accuracy, which is why the device itself must be provided with accurate timing data. With an even larger number of satellites, it can increase the accuracy further. With this system, accuracies of half a meter can be achieved in 3D space. 

When we want to integrate this system into our flight computer, we have to select the receiver that communicates with these satellites and calculate its position. 

One aspect we must consider when selecting such a receiver is what satellite constellations it can receive. There are many GNSS constellations including the United States’ GPS (Global Positioning System), Europe’s Galileo, China’s Beidou, Russia’s GLONASS, India’s IRNSS, and Japan’s QZSS. Each position system has better coverage in one area and worse in another. If we were to launch in the US, the GPS might be superior, while if we were to launch in Europe, we probably would want to receive Galileo. There are GNSS receivers that can receive multiple constellations. 

If you want to integrate GNSS into your project, you might want to look at the GNSS receivers from UBLOX, such as the NEO-M9N. For implementing them, Sparkfun's breakout board schematics might help you.

#### More Sensors
There are so many sensors that could be useful for model rocketry applications that we will not discuss in this course. 

Still, for you to get an idea of which sensors there are, I will list a few more that might suit your projects. 
- Ultrasonic sensors that determine distance based on the elapsed time that an ultrasonic sound wave needs to travel. Similar to the echolocation bats use. These distance measurements might help you to determine relative altitude to the ground, or you could use them for obstacle avoidance. 
- Humidity, temperature, and air quality sensors to determine the state of the atmosphere. 
- Ultraviolet sensors for determining UV radiation, which you could use to assess Ozone layer depletion or radiation levels to protect humans from sunburns. 
- A weight cell for measuring the rocket's real-time thrust to adjust the stabilization algorithm.
- Photoresistor to monitor the trigger of heating wires and engine ignition.  
- Strain gauges positioned on the rocket to gauge mechanical stress.
- Or seismometer to evaluate vibrations during flight. 
- And much, much more! 

Most of the sensors come with SPI or I2C or are even analog devices, which you can read out by hooking them up to one of the ADC channels. 

The implementation principle is the same for all of them. 
You determine which property you want to measure, source a part that can do what you need, and implement it on your PCB according to its datasheet. 
#### Summary
So, let's summarize this section:
The three most vital sensors that almost every rocket will need are the gyroscope, the accelerometer, and the barometer. 

The gyroscope measures the angular rate, which we can then translate into the rocket's orientation by integrating and feeding it into an orientation representation model like Euler Angels or Quaternions. Its measurements are accurate over short times and aren't influenced by vibrations or other outside circumstances. However, they tend to drift over time. We calibrate them to minimize the drift. Yet, after some time, every gyroscope will be off to a certain degree.

The accelerometer, unfortunately, cannot be used during model rocket flights, as the total thrust does not point to the Earth's center but is hard to predict. Remember, it depends on the Earth's gravitational acceleration, the thrust curve, the deceleration due to the air resistance, and the TVC mount's angle. However, we can use the accelerometer to provide the gyroscope with a setpoint while sitting stationary at the launchpad. In that case, only the gravitational acceleration is present, and orientation can be measured easily and without drift. Further, we can use the accelerometer's data after the burnout of the rocket engine. During flight, accelerometers are also heavily influenced by vibrations. 

The third essential sensor is the barometer, which measures pressure and temperature to determine the altitude based on the barometric pressure equation. With increasing altitude, the pressure decreases, and with increasing temperature, the pressure increases too. Its relative accuracy can be high. However, its absolute accuracy depends on a few more factors, such as humidity, diurnal pressure fluctuations, and low and high-pressure zones based on weather situations. 

Another sensor that can be useful is a voltmeter. We can implement such a sensor by using a resistor divider and one of the ADC channels on the microcontroller. With it, we can determine the battery voltage and notify the user if not enough voltage is present. 

There are still more sensors that might be highly useful, such as a magnetometer to determine the rocket's orientation based on Earth's magnetic field, a GNSS receiver to evaluate the vehicle's position by using the positioning satellite systems, and many, many more. 

Most sensors typically connect using SPI or I2C protocols, while some can also be read out using analog methods. Many also feature interrupt pins by which they can indicate to the microcontroller that new data is ready. The sensor's datasheet is the most important document when implementing a sensor. It states the sensor's characteristics and often provides a diagram of how to properly implement the sensor. 
