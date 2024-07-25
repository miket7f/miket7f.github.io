---
layout: page
title: Electronics Integration
permalink: elec-int
---
## This path is not supported yet!

Try another path or try to learn about this subject yourself,  
while we are working on providing content for you! 

## Level 1 - Stack Analysis

### Lecture
Congratulations on reaching the end of the **Electronics Circuits** section! You’ve journeyed through the fundamentals of electronics and explored how to build and design various circuits for flight computers. Now, let's bring everything together by diving into a detailed analysis of the Stack flight computer. This will help you understand how the theoretical concepts you've learned are applied in a real-world system.

#### CORE
![](/assets/images/a6700-0328%20-%20frame%20at%200m12s-2.jpg)

- **Stack CORE** manages the entire flight computer system. It features an XT60 connector for the battery, which is a three-cell LiPo with 500mAh capacity and a 25C rating.
- The PCB includes the **LM2596** voltage regulator. Remember, the LM2596 needs an activation pin connected to a switch. The input capacitor, inductor, diode, and output capacitor are carefully placed, with the inductor positioned away from control signals.
- The regulated 5V from the buck regulator is fed into a **3.3V linear regulator** (ASM1117-3.3), which is supported by two tantalum capacitors.
- The **ESP32-WROOM-32E** microcontroller, equipped with WiFi and Bluetooth, is the heart of the CORE board. It’s programmable via the Micro USB port and features a CH340 USB-to-UART driver along with an auto-reset circuit. There are two buttons for manual reset and boot control.
- Additional components include an RGB LED, a buzzer, and a voltmeter. 
- Finally, the connector through which Vbat, 5V, 3.3V, GND, and an I2C bus are transmitted between the different boards.

#### FUSION

![](/assets/images/a6700-0327%20-%20frame%20at%200m3s%20-%202.jpg)

- **Stack FUSION** features the **STM32F7RET6** microcontroller, with numerous capacitors for VDD and a VDDA filtering circuit.
- It includes buttons for boot and reset control, a serial wire debug interface for programming via an ST-Link V2, and a micro USB port as a backup.
- The board houses a crystal oscillator with its capacitors and several sensors: the **BMI088 gyroscope and accelerometer** and the **BMP388 barometer**, each with its own capacitors.
- Backup pins are provided for connecting sensors with external microcontrollers, and solder places for pull-up resistors for SPI protocol.
- ESD protection is implemented to safeguard the board from electrostatic discharge, which can cause damage if accumulated static electricity is discharged.

#### OUT

![](/assets/images/a6700-0330%20-%20frame%20at%200m5s%20-%202.jpg)

- **Stack OUT** features the **STM32G030K8T6** microcontroller, which lacks pins for a crystal oscillator. Instead, it uses a high-speed external oscillator for accurate timing, crucial for controlling servos.
- The board includes a serial wire debug connector, a reset button, and five servo connections with 1x3 right-angled male pin headers.
- It also houses an RGB LED, five high-current MOSFET pyro channels with indicator LEDs, and pluggable terminal blocks for easy connection and disconnection of heating wires and electric ignitors.
- Like the other boards, ESD protection is included to prevent damage from electrostatic discharge.

### Final Thoughts

As we conclude the **Electronics Circuits** section, you’ve not only learned about the individual components but also how they come together to form a functional flight computer. The Stack analysis showcases how theoretical knowledge translates into practical designs, offering a clear example of how these principles are applied in advanced systems.

**Next Steps**

In the upcoming modules, you will have the opportunity to:

- **Design and Build Your Own Circuits:** Apply your understanding to create and test your own circuit designs.
- **Explore Advanced Topics:** Dive deeper into specialized areas such as PCB design, integrated circuits, and more complex systems.
- **Work on Projects:** Begin hands-on projects to reinforce your learning and gain practical experience.

Your journey in electronics is far from over. With the foundational knowledge and practical insights you’ve gained, you’re well-equipped to tackle new challenges and innovations. Stay curious and continue experimenting to advance your skills further.

We’re excited to see what you’ll create next!