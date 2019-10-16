# Week 3 Labs
Msc Creative Computing
Physical Computing #3 1 w/ Phoenix Perry
By Stuart Leitch
October 14, 2019

## Lab 01 - Playing with fades
Build this circuit: https://www.arduino.cc/en/Tutorial/Fade but solder it into perfboard.

Two goals:
1) Solder for the first time
2) Explore the PWM pin

We built two models of this. First, we uploaded the code to the Arduino and built the circuit on a breadboard. Since we hadn't done any soldering before, we were playing it safe. No idea if we would be able to remove solder after it solidified.

The second goal of this exercise is to use a PWM pin, which essentially turns a digital pin into an analog pin by turning it on and off very fast with a modulated/changed ratio between on and off. 

PWM pins can have values between 0-255. It works flawlessly, as can be seen in the attached video of the soldered circuit.
The true analog pins have more values, but for many use cases 256 values is enough.

The soldering proved to be more difficult than expected. I did remember to "tin" the iron at first, and did my best to follow the guidelines of the video tutorial, but it was somewhat tedious getting the solder where I actually needed it. There was no small amount of re-melting and replacing. Solder would frequently cross "gullies" so we nearly ran out of space on our little bit of perf board. Very glad we prepared in advance by cutting it down to a smaller board.

Also very happy that the goggles stayed on my glasses. $100+ for prescription goggles is out of my low student budget. 

Click to view video.
[![PWM VIDEO](https://github.com/Toruitas/pcomp-wk3/blob/master/1_soldered_circuit.JPG)](https://youtu.be/wF0G4sqYSjE "PWM VIDEO")

The perfboard + soldered circuit:
![Perfboard Circuit](https://github.com/Toruitas/pcomp-wk3/blob/master/1_isolated_soldered_circuit.JPG)

## Lab 02 - Voltage Dividers

The only thing I could think during this was, what would a voltage divider be used for? Why would you want to drop voltage?

## Lab 03 - Making a dark detecting LED

[The Lab](https://makezine.com/projects/dark-detecting-led/)
[The phototransistor's datasheet](https://www.avnet.com/shop/emea/products/everlight/pt333-3c-3074457345634369228?&r=EMEA&CMP=AVNET-EMEA-PPC-Google-All-English-AVE14-SKU-1699305114-66248026957-042019|mkwid|skycZlOwT_dc|pcrid|339939286074|pkw|pt333-3c|pmt|p|slid||prd||pgrid|66248026957|ptaid|kwd-14750612769?aka_re=1)

Halloween is coming up. Everyone needs a light for their pumpkin! This lab revolves around making a set and forget light that turns on after dark, and turns back on after the sun rises again. 

Let's suspend disbelief and assume this pumpkin is like a potato and can supply an electrical current, and that it's enough to supply power to an Arduino ad infinitum. 

Random pumpkin fact - Belgium went to the World Pumpkin Championships 2019 and came away with a clean sweep of 1st, 2nd, and 3rd. Who could have seen that coming?

When powered by the magic pumpkin, this circuit doesn't even need a program to be running on it to accomplish the task.

### There were 2 tricky parts. 
1) the voltage divider - related to Lab #2, It's something I need to spend a little more time studying and experimenting with.
2) the phototransistor needs to be completely engulfed in darkness to redirect the electrons. Was tricky to block the bottom of the photoresistor in the middle of the board.
3) We realized this early - we had to remove the code from the prior lab from the Arduino. We did this by updating it with completely empty setup(){} and loop(){} methods and uploading it.

Key to keep in mind: how a transistor works. In Wikipedia terms:

NPN is one of the two types of bipolar transistors, consisting of a layer of P-doped semiconductor (the "base") between two N-doped layers. 

A small current entering the base is amplified to produce a large collector and emitter current. That is, when there is a positive potential difference measured from the base of an NPN transistor to its emitter (that is, when the base is high relative to the emitter), as well as a positive potential difference measured from the collector to the emitter, the transistor becomes active. 

In this "on" state, current flows from the collector to the emitter of the transistor. Most of the current is carried by electrons moving from emitter to collector as minority carriers in the P-type base region. 

To allow for greater current and faster operation, most bipolar transistors used today are NPN because electron mobility is higher than hole mobility. 

--

In my words. NPN works when a base current is provided. The higher the base current, the multiplicitively-higher the collector current. Stream 1 makes stream 2 go faster.

Current gain:
Beta = Ic/ Ib

### How this circuit works:

Light is the base input voltage for the phototransistor. When its base gets power, the photoresistor responds by creating a current between the collector (plugged into +) and the emitter plugged into the second transistor's base. The base of the second transistor (black NPN) activates with this current and pulls current from its collector (again connected to +) and out its emitter,which supplies current to the LED. Current is then grounded out the other side of the LED. 

Click to view video.
[![PHOTOTRANSISTOR VIDEO](https://github.com/Toruitas/pcomp-wk3/blob/master/2c_phototransistor.JPG)](https://youtu.be/9CULAY7hTHc "PHOTOTRANSISTOR VIDEO")

View 1 of the circuit:
![Phototransistor Circuit](https://github.com/Toruitas/pcomp-wk3/blob/master/2a_phototransistor.JPG)

View 2 of the circuit:
![Phototransistor Circuit](https://github.com/Toruitas/pcomp-wk3/blob/master/2b_phototransistor.JPG)