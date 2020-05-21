The detailed description of the project:
[Water level controller](https://github.com/Snehan2k2/Elec_club_Mini_Task_2/blob/master/Water%20level%20controller.md)

The pipeline of the project:

Aluminium wire => Analog pins on Arduino => Buzzer, LCD display, Motor

Here, the main module is playing with the microcontroller, Arduino.

**Checking the connections with Arduino:**

The sensor assembly consists of four aluminum wires arranged at 1/4, 1/2, 3/4 and full levels in the tank.
The dry ends of these wires are connected to analog input pins A1, A2, A3 and A4 of the Arduino respectively. A  fifth wire is positioned at the bottom of the tank.
Resistors R6 to R9 are pull down resistors.The dry end of this wire is connected to +5V DC.

Digital pin 7 of the Arduino controls the buzzer and digital pin 8 controls the motor. Transistor Q1 drives the buzzer and resistor R5 limits the base current of Q1. Transistor Q2 drives the relay. Resistor R3 limits the base current of Q2. D2 is a freewheeling diode. POT R2 is used to adjust the contrast of the LCD. resistor R1 limits the current through the back light LED. Resistor R4 limits the current through the power ON LED.

Now, we check if all the connections are made properly and are properly wired to the microcontroller. If at all there are loose connections, they are taken care of and we move ahead. We also check for the functionality of the components, we have to check if any component is faulty or doesn't meet its requirements.

For ex: We check if the Arduino is working properly, by seeing if the inbuilt LED in Arduino is lit, when the microcontroller is put to power. Also, if the IC gets overheated, it means its internal components have been damaged and it has to be replaced.

