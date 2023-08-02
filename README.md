# Powercore-V1-Manual
Theory and operation of the Powercore V1 EDM PSU
![Cover Image](https://github.com/Rack-Robotics/Powercore-V1-Manual/blob/main/Powercore%20V1%20Cover%20Image.png)

# Warning
HIGH VOLTAGE
The Powercore is not a toy. It is a serious machine tool that carries with it similar risks to other machine tools. Improper use may lead to destruction of property, injury, and death.

By using the Powercore EDM Power Supply, you agree to indemnify and hold harmless Rack Robotics, Inc., its affiliates, employees, and agents from any claims, damages, liabilities, losses, or expenses arising out of or related to your use or misuse of the Powercore. This includes, but is not limited to, any third-party claims, death, personal injury, property damage, or infringement of intellectual property rights.
You agree to defend Rack Robotics, Inc. against any such claims and bear the costs associated with legal representation, settlements, judgments, or other expenses incurred by Rack Robotics, Inc. as a result of your actions or use of the Powercore. This indemnification obligation will survive the termination or cessation of your use of the Powercore. 

It is important to use the Powercore in a responsible and lawful manner, following all instructions, guidelines, and safety precautions outlined in the manual.

The end user is solely responsible for all usage and outcomes associated with the Powercore EDM Power Supply. By using the Powercore, you accept all risks and liabilities that may arise from its use. The Powercore is a high voltage power supply, and as such, it poses a potentially deadly hazard. Rack Robotics, the manufacturer, cannot be held liable for any damages, losses, or injuries resulting from the use or misuse of the Powercore. It is crucial to carefully follow the provided instructions, adhere to safety guidelines, and exercise extreme caution during operation. Any unauthorized modifications may void the warranty and significantly increase the risk of malfunctions or life-threatening situations. Rack Robotics shall not be held responsible for any loss, damage, or injury resulting from the use of this product. Use the Powercore in strict accordance with applicable laws and regulations, and exercise the utmost diligence to minimize potential risks.

[Rack Robotics on YouTube](https://www.youtube.com/@rackrobo)

## Do Not Short the Powercore! 
To ensure the longevity and safe operation of your Powercore V1, it is essential to avoid short circuit events that can cause significant damage to its internal components, particularly the power MOSFET. A short circuit can occur when the positive and negative terminals of the device are connected with low or no resistance, causing a large current flow which can lead to overheating and subsequent damage.

*Never leave the Powercore V1 unattended while in use. If a short circuit occurs, it's important to promptly disconnect the device to prevent further damage!*

## Electrical Discharge Machining
Electrical Discharge Machining (EDM), also known as spark machining, is a non-traditional machining process that leverages the principle of rapid, controlled electrical discharges to remove material from a workpiece. In EDM, a series of electric sparks jumps across a gap between an electrode and the workpiece, submerged in a dielectric fluid. The thermal energy generated from these sparks is so intense that it vaporizes or melts the material on the workpiece surface in a controlled manner. The expelled molten material then solidifies into small debris particles and is flushed away by the continuously replaced dielectric fluid. By carefully controlling the frequency and energy of these sparks, EDM can achieve highly accurate and intricate shapes even in hard, difficult-to-machine materials.

Joule heating is a fundamental principle at the heart of Electrical Discharge Machining (EDM). It's the process by which the passage of an electric current through a conductor produces heat. In EDM, the high-frequency electrical discharges occur between the electrode and the workpiece, creating a channel of plasma—this plasma has resistance. As the current passes through this plasma channel, the resistance leads to heat generation. This extreme heat (which can reach temperatures as high as 8000-12000°C) is what vaporizes or melts the material from the workpiece in a very localized area, allowing for the precise machining that EDM is known for.

In EDM, the tool (often made from brass or copper) serves as the cathode, or the negative electrode, while the workpiece acts as the anode, or the positive electrode. This setup is established to facilitate the flow of electrons from the tool to the workpiece during the machining process.

When voltage is applied, it creates an intense electric field between the tool and the workpiece. Once the dielectric strength of the fluid is exceeded, it breaks down, and a spark discharge is initiated. Electrons rapidly flow from the cathode (the brass tool) to the anode (the workpiece). This flow of electrons generates a plasma channel and produces extreme heat, which leads to the melting and/or vaporization of the workpiece material at the point of discharge.

The choice of using brass for the tool (cathode) is due to its good electrical conductivity and relatively lower wear rate, meaning the tool retains its shape for longer, allowing more accurate and efficient machining. On the other hand, the workpiece, acting as the anode, is the target of the material removal process, where the generated heat from the spark causes localized melting or vaporization, thus aiding in achieving the desired shape or feature.

## Powercore V1 Hardware and Electronics

The Rack Robotics's Powercore is a transistor EDM power supply unit. The Powercore creates, maintains, and monitors electrical sparks in an EDM machine. It is designed to be affordable and hackable. The Powercore has several features to achive its purpose: 

    On-Board Raspberry Pi Pico  -   A drop-in Raspberry Pi Pico module is used as an on-board microcontroller, allowing for maximum flexibility. 
                                    Micropython come pre-flashed on-board. Do not attempt to program microcontroller while machining, or while 
                                    powered on.
    
    Transistor Control          -   A high-voltage & high-current power MOSFET (IRF135S203) controls when sparks can form. The MOSFET is
                                    primarily controlled via PWM. The logic of the high-voltage MOSFET is inverted. Meaning that when the 
                                    MOSFET pin state is low, current can pass. When the MOSFET pin state is high, current can not pass. 
                                    This is because of the low-voltage AOD508 MOSFET used to drive the high-voltage MOSFET.

    Adjustable Frequency        -   The minimum frequency between sparks is controlled digitally via PWM. Recommended operating frequency is 2 KHz.
                                    Higher frequencies can generate more waste heat than lower frequencies, potentially damaging the switching MOSFET.

    Adjustable Duty cycle       -   The maximum duration of sparks is controlled digitally via PWM.

    Current Monitoring          -   Current is monitored via an analog sensor (ACS712_x20A) within a range of +-20 amps. During capacitor dscharge, this maxes out 
                                    the current sensor, causing a peak that resembles a digital peak. 

    Thermal Monitoring          -   An onboard thermister monitors the temperature of the power resistor and MOSFET, helping to preventing overheating.

    Short Circuit Alert         -   (Work in Progress!) Digital feedback is provided during the event of a short by the "short alert" port (3.3 v normal, 0 v during short).

    Analog Feedback             -   Analog feedback from the ACS712x20A current sensor is provided by the "current" port (1.667 v - 0.333 v)
                                    This system adjusts the reported voltage with a sensitivity of ~0.0667 volts / amp. The baseline voltage 
                                    of the system is the voltage reported when no current is flowing through the system. The voltage is approximately 
                                    ~1.667 v volts. When current increases, the voltage reported will decrease at a rate of 
                                    ~0.667 volts per amp. A reading of 0.333 volts indicates >= 20 amps. During capacitor dscharge, this maxes out 
                                    the current sensor, causing a peak that resembles a digital peak.

For information about the Powercore V1 hardware/electronics or firmware, examine the repositories below. 

[Powercore V1 Hardware Repo](https://github.com/Rack-Robotics/Powercore-V1-Hardware)

[Powercore V1 Firmware Repo](https://github.com/Rack-Robotics/Powercore-V1-Firmware)

### Energy Consumption as a Function of Cylindrical Tool Diameter
The higher the melting or boiling point of the metal, the more energy is required to remove material from the workpiece. Machining speed in EDM is influenced by the energy required to reach the melting or boiling point of the material being worked. As previously explained, materials with lower melting or boiling points, such as zinc and aluminum, require less energy to reach these temperatures, allowing the EDM process to proceed more quickly. This means the machining speed when working with these materials is generally faster. Conversely, materials with higher melting or boiling points, like titanium and steel, require more energy to heat, hence the process takes longer. Consequently, the machining speed when working with these materials is slower. 

The energy required to remove the material along a specific EDM tool path is given as the equation bellow. This assumes that material is removed as soon as it is vaporized.

### $E = (πr^2 + 2rd)hρ(CT_b + E_f + E_v)$

$E$ - energy ($J$) 

$r$ - radius of tool ($m$) 

d - distance of path ($m$)

$h$ - height of work ($m$

$ρ$ - density of material ($Kg/m^3$)

$C$ - specific heat capacity of material ($J/KgK$) 

$T_b$ - Boiling point of material ($K$)

$E_f$ - Enthalpy of Fusion ($J/Kg$)

$E_v$ - Boiling point of material ($J/Kg$)

| Electrode Diameter | Cross Sectional Area | Material Removed from 30 mm Thick Work after 100 mm Long Pass | Energy Required for Zinc 388 J/kgK, 1180 K | Energy Required for Aluminum 897 J/kgK, 2740 K | Energy Required for Titanium 523 J/KgK, 3560 K | Energy Required for A2 Tool Steel 460 J/kgK, 3134 K |
| --- | --- | --- | --- | --- | --- | --- |
| 3 | 7.07 mm^2 | 9212 mm^3 | 22.6 KJ | 54.8 KJ | 71 KJ | 94.8 KJ |
| 1.5 | 1.77 mm^2 | 4553 mm^3 | 11.2 KJ | 27.1 KJ | 35.1 KJ | 46.9 KJ |
| 1 | 0.79 mm^2 | 3024 mm^3 | 7.5 KJ | 17.1 KJ | 23.3 KJ | 31.1 KJ |
| 0.5 | 0.20 mm^2 | 1506 mm^3 |  3.7  KJ |  9.0 KJ | 11.6 KJ | 15.5 KJ |
| 0.3 | 0.07 mm^2 |  902 mm^3 |  2.2 KJ |  5.4 KJ |  6.7 KJ | 9.3 KJ |
| 0.2 | 0.03 mm^2 |  601 mm^3 |  1.5  KJ |  3.6 KJ |  4.6  KJ | 6.2 KJ |
| 0.1 | 0.008 mm^2 |  300 mm^3 |  0.73 KJ |  1.8 KJ |  2.3  KJ | 3.1 KJ |
