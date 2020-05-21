**Debugging Wireless doorbell:** 

The detailed project description :
[Wireless doorbell](https://github.com/Snehan2k2/Elec_club_Mini_Task_2/blob/master/Wireless%20doorbell.md)

The pipeline of the project is:

Button => HT-12E Encoder IC => RF transmitter => RF receiver => HT-12D Decoder => Arduino => buzzer

So, basically there are two types of modules

1. Transmitter module
2. Receiver module

The button is connected to the 10th pin of HT-12E Encoder IC, and when the button is switched on, the enoder senses it and it transmits signals using the RF transmitter.

The transmitted signal is received by the RF receiver module, which is connected to the HT-12D Decoder, which in turn is connected to the Arduino's 2nd pin. The buzzer is connected to the Arduino's 11th pin, which operates when it receives signals from the transmitter.

**Transmitter module:**

We check if the transmitter part of the circuit is connected properly. We check if the RF transmitter module, resistor and button are connected to the circuit properly and are properly wired to the HT-12E encoder.

If at all there are loose connections, they are taken care of and we move ahead.

Now, we check for the functionality of the components. We have to check if any component bought is faulty or doesn't meet its requirements. For example, if the IC is overheated, it means it doesn't work anymore and that it has to replaced.

**Receiver module:**

We check if the receiver part of the circuit is connected properly. We check if the the RF receiver module, resistor and the Arduino board are connected to the HT-12D decoder. We also check if the buzzer is connected properly to the arduino board, and that they are connected to the right pin no.s.

To check if the Arduino board is working properly, we check if the in-built LED gets switched on, when the board is given power. Similarly, we check the functionality of other components.

**Troubleshooting the code:**
```cpp
int buz=11;
int sen=2;

void setup() 
{
  pinMode(buz,OUTPUT);
  pinMode(sen,INPUT);

  digitalWrite(buz,LOW);
  digitalWrite(sen,HIGH);
}

void loop() 
{
 while(digitalRead(sen)==HIGH);
 digitalWrite(buz,HIGH);
 while(digitalRead(sen)==LOW);
 digitalWrite(buz,LOW);
}
```
The code ensures that if the sensor is high, that is that the 
