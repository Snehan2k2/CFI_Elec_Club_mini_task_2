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


