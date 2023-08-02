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

# Electrical Discharge Machining
Electrical Discharge Machining (EDM), also known as spark machining, is a non-traditional machining process that leverages the principle of rapid, controlled electrical discharges to remove material from a workpiece. In EDM, a series of electric sparks jumps across a gap between an electrode and the workpiece, submerged in a dielectric fluid. The thermal energy generated from these sparks is so intense that it vaporizes or melts the material on the workpiece surface in a controlled manner. The expelled molten material then solidifies into small debris particles and is flushed away by the continuously replaced dielectric fluid. By carefully controlling the frequency and energy of these sparks, EDM can achieve highly accurate and intricate shapes even in hard, difficult-to-machine materials.

Joule heating is a fundamental principle at the heart of Electrical Discharge Machining (EDM). It's the process by which the passage of an electric current through a conductor produces heat. In EDM, the high-frequency electrical discharges occur between the electrode and the workpiece, creating a channel of plasma—this plasma has resistance. As the current passes through this plasma channel, the resistance leads to heat generation. This extreme heat (which can reach temperatures as high as 8000-12000°C) is what vaporizes or melts the material from the workpiece in a very localized area, allowing for the precise machining that EDM is known for.

### Energy Consumption as a Function of Cylindrical Tool Diameter

The energy required to boil the material along a specific EDM tool path is given as the equation bellow. This assumes that material is removed as soon as it is vaporized.



