The detailed description of the project:
[Water level controller](https://github.com/Snehan2k2/Elec_club_Mini_Task_2/blob/master/Water%20level%20controller.md)

The pipeline of the project:

Aluminium wire => Analog pins on Arduino => Buzzer, LCD display, Motor

Here, the main module is playing with the microcontroller, Arduino.

**Checking the connections with Arduino:**

The sensor assembly consists of four aluminum wires arranged at 1/4, 1/2, 3/4 and full levels in the tank.
The dry ends of these wires are connected to analog input pins A1, A2, A3 and A4 of the Arduino respectively. A  fifth wire is positioned at the bottom of the tank.
Resistors R6 to R9 are pull down resistors. The dry end of this wire is connected to +5V DC.

Digital pin 7 of the Arduino controls the buzzer and digital pin 8 controls the motor. Transistor Q1 drives the buzzer and resistor R5 limits the base current of Q1. Transistor Q2 drives the relay. Resistor R3 limits the base current of Q2. D2 is a freewheeling diode. POT R2 is used to adjust the contrast of the LCD. Resistor R1 limits the current through the back light LED. Resistor R4 limits the current through the power ON LED.

Now, we check if all the connections are made properly and are properly wired to the microcontroller. If at all there are loose connections, they are taken care of and we move ahead. We also check for the functionality of the components, we have to check if any component is faulty or doesn't meet its requirements.

For ex: We check if the Arduino is working properly, by seeing if the inbuilt LED in Arduino is lit, when the microcontroller is put to power. Also, if the IC gets overheated, it means its internal components have been damaged and it has to be replaced.

**Troubleshooting the code:**

```c++
#include <LiquidCrystal.h>
int sump=A0;
int qut=A1;
int hlf=A2;
int thf=A3;
int ful=A4;
int motor=8;
int buz=7;
int s;
int q;
int h;
int t;
int f;
int i;     //motor status flag
int v=100; //comparison variable(needs some adjustment)
int b=0;   //buzzer flag
int m=0;   //motor flag
int c=0;   //sump flag

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup()
{

pinMode(qut,INPUT);
pinMode(hlf,INPUT);
pinMode(thf,INPUT);
pinMode(ful,INPUT);
pinMode(sump,INPUT);
pinMode(motor,OUTPUT);
pinMode(buz,OUTPUT);
lcd.begin(16, 2);
digitalWrite(buz,LOW);
}

void loop()
{

i=digitalRead(motor);
s=analogRead(sump);
q=analogRead(qut);
h=analogRead(hlf);
t=analogRead(thf);
f=analogRead(ful);
lcd.clear();
```
The variables required for the code are brought in and are initialised.

```c++

if(f>v && t>v && h>v && q>v )
{
lcd.setCursor(0,0);
lcd.print(char(219));
lcd.print(char(219));
lcd.print(char(219));
lcd.print(char(219));
lcd.setCursor(5,0);
lcd.print("FULL");
m=0;
b=0;
}

else
{
if(f<v && t>v && h>v && q>v)
{
lcd.setCursor(0,0);
lcd.print(char(219));
lcd.print(char(219));
lcd.print(char(219));
lcd.print("_");
lcd.setCursor(5,0);
lcd.print("3/4th");
b=0;
}
else
{
if(f<v && t<v && h>v && q>v)
{
lcd.setCursor(0,0);
lcd.print(char(219));
lcd.print(char(219));
lcd.print("_");
lcd.print("_");
lcd.setCursor(5,0);
lcd.print("HALF");
m=1;
b=0;
}
else
if(f<v && t<v && h<v && q>v)
{
lcd.setCursor(0,0);
lcd.print(char(219));
lcd.print("_");
lcd.print("_");
lcd.print("_");
lcd.setCursor(5,0);
lcd.print("1/4th");
b=0;
}
else
{
if(f<v && t<v && h<v && q<v)
{
lcd.setCursor(0,0);
lcd.print("_");
lcd.print("_");
lcd.print("_");
lcd.print("_");
lcd.setCursor(5,0);
lcd.print("LOW");
b=0;
}
else

{
digitalWrite(motor,LOW);
lcd.setCursor(0,0);
lcd.print("ERROR!");
b=1;
}
}}}
if(i==HIGH)
{
lcd.setCursor(0,1);
lcd.print("Motor ON");
}
else
{
lcd.setCursor(0,1);
lcd.print("Motor OFF");
}



if(s>v && m==1)
{
digitalWrite(motor,HIGH);
}
if(s<v)
{
digitalWrite(motor,LOW);
lcd.setCursor(11,0);
lcd.print("Low");
lcd.setCursor(11,1);
lcd.print("Sump");
c=1;
}
if(s>v)
{
c=0;
}

if(m==0)
{
digitalWrite(motor,LOW);
}

if(b==1 || c==1)
{
digitalWrite(buz,HIGH);
delay(500);
digitalWrite(buz,LOW);
}
else
{
digitalWrite(buz,LOW);
}
delay(100);
lcd.clear();
}
```

