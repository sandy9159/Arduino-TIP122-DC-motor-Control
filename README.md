# Arduino-TIP122-DC-motor-Control

![image](https://user-images.githubusercontent.com/19898602/134295418-ebad0456-ec30-4504-b1cf-6a5d994225fd.png)


Hello makers in this post we’ll learn how we can control high rating 755 DC motor with arduino using TIP122

Whenever we need to run a DC motor in our arduino project,
we cannot connect it directly to the digital pins of arduino board because the maximum current rating of digital pin is 40mA.

and DC motor specially in our case 775 12V DC motor draws 0.45Amps if we connect it directly to arduino board you know what happen, it will burn your arduino board.

for such purpouse we are going to use TIP122 NPN Darlington transistor it can handle upto 5A 100V load.

so let see how to control DC motor using arduino and TIP122 NPN transistor

# TIP122

TIP122 is NPN Darlington power transistor it is suitable for low speed switching circuits.

It can handle 5A and 100V load , TIP122 have three terminal legs Base, collector and emitter.

The TIP120 is an NPN Power Darlington Transistor. It can be used with an Arduino to drive motors, turn lights on, and drive other high power gadgets.

The TIP120 acts as a power broker or gatekeeper between the Arduino realm and the high power realm composed of the PC fan and its battery pack. 

The Arduino can tell the TIP120 how much power to pass from the external battery pack to the PC fan but the Arduino does not share any of its power or share pins with the PC fan or its batteries. The TIP120 is the go in between.

![image](https://user-images.githubusercontent.com/19898602/134296324-f52261de-0d7b-40cc-bba5-ea02cb911bc9.png)


The TIP120 has three pins. One is called Base, which we will connect to any of the Arduino PWM pins. 

Through the Base pin, the Arduino can tell the TIP120 how much power to supply to the motor from the external battery pack. That's it. 

![image](https://user-images.githubusercontent.com/19898602/134296374-88f4e963-07fd-46a6-a7c1-e7ef77175631.png)


The TIP120 does the heavy lifting while Arduino sits back and gives orders through one of its PWM pins to the TIP120 Base pin telling it how much power to pass to the motor. 

The poor TIP120 has to then pass the requested power from the external power to the motor based on Arduino's request.

![image](https://user-images.githubusercontent.com/19898602/134295498-5c58162d-28cc-4572-98f3-ab5a566728e8.png)


# Circuit diagram for Arduino TIP122 DC motor Control

Here we have connected a switch between GND and arduino digital pin 3 and base of TIP122 transistor is connected in series with 500 ohm resistor and digital pin 12 .

to control DC motor when we press the switch, DC motor will turn on and after releasing the switch DC motor will turns off.


![image](https://user-images.githubusercontent.com/19898602/134295539-2547451a-63d2-4f64-a72f-6c3fcba65da1.png)

Before moving fuurther I would like to tell you something about PCB

Yes PCB are the heart of the electronics based project usually we hesitate to try custom PCB and opt to homemade solutions

like breadboard or Zero PCB earlier I also was in the same boat, I hesitate to try custom PCB my belief was they are much expensive.

but then I came to know about [JLCPCB.com](https://jlcpcb.com/IAT) and I was totally surprised how low price PCB's are they offering 

there PCB quality is best in market, now I always go with PCB for my project and [JLCPCB.com](https://jlcpcb.com/IAT) is my trusted 

PCB manufacturer, you can also try there PCB service for more details you can visit their website [JLCPCB.com](https://jlcpcb.com/IAT)
You can also try there new purple colour for PCB without any extra cost.
![image](https://user-images.githubusercontent.com/19898602/134336832-cb9953e9-02a6-4ff7-9d27-2caad10fe7c7.png)
![image](https://user-images.githubusercontent.com/19898602/130722577-c30b7b43-ea89-4847-9c6b-058f9fabeda3.png)![image](https://user-images.githubusercontent.com/19898602/130722585-b5268db1-5f17-428f-ba60-b823140f2a70.png)


# Arduino code

At the very binning of the code we declare some variable for pin identification

In void Setup we declare pin modes, pin 12 is output pin and Pin 3 is inputpull pin.

It is good to declare Input pin as input pullup because then we no need to attache any external pullup resistor to the switch.

In normal condition if switch is not pressed the pin 12 is high, when switch is pressed it connected to ground and became low via internal pullup resistor.

So in void loop we used “IF ELSE” function like if switch is pressed then arduino makes output pin high so base pin of transistor gets 5V and turn on the motor through transistor.

else keep the output pin LOW to keep motor turn off.


```javascript

int motpin = 12;
int button = 3;
void setup() {
  pinMode(motpin, OUTPUT);
  pinMode(button, INPUT_PULLUP); 

}

void loop() {
  if (!digitalRead(button)){
    digitalWrite(motpin,HIGH);
  }

  else{
    digitalWrite(motpin,LOW);
  }

}

```

![yt5s com-Arduino   TIP122 DC motor control _ 755 DC motor(720p)](https://user-images.githubusercontent.com/19898602/134296934-87696a0f-75ce-4577-b459-097ca7faee72.gif)

