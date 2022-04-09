# Smart-Dustbin
Smart Dustbin
Smart Dustbin for Smart City



Objectives


This project is to design and build a prototype for an
automatic open dustbin that can automatically open the lid
when it detects the people who want to throw out their
trash.
So this can be done by implementing IoT based waste
management using smart dustbin.


Motivation



Over main motivation behind this project is the ongoing campaign Swachh Bharat Abhiyan
(Clean India Movement) launched on October 02, 2014 at Rajghat , New Delhi, by the Prime
Minister of India Narendra Modi which is India's largest ever cleanliness drive to clean the
streets, roads and infrastructure of the country's 4,041 statutory cities and towns.
Cleanliness and hygiene are one of the most important things cherished by all human
beings in the society.
In order to have a clean environment , we must reduce the improper waste disposal
methods in unclean places and make them tidy and neat by proper waste management.
Dustbins are often very unhygienic & filthy since it is filled with wastes of different kind
and it spreads foul smell around it because of open containers. Our motivation for the
project came from the fact that we should design a dustbin which makes it easier for people
to throw garbage.
An automated dustbin eliminates the process of throwing garbage by going to a foul
smelling and filthy dustbin by automating the process of opening and closing the lid of the
dustbin using some simple electric components.
By making the process of throwing the garbage a little easier , our design of this simple
dustbin provides a fun way to dispose off your garbage.
Psychological research has also shown that positive reinforcement can go a long way in
developing a good habit. By adding a screen we can display a positive message as simple as a
Thank You. This will encourage people to use the dustbin more often which will help the cause
of Swachh Bharat. It is especially a good way to develop the habit of proper garbage disposal
among young children early on in their lives.


Introduction


Most of the cities, towns and villages in India are not well designed to facilitate
the suitable garbage collection methods. Common Public dustbins are filling over
with the garbage and no one is concerned to clear them up as and when they get
completely packed with overflowing garbage.
Keeping in view of this big problem, it will be a good suggestion to do something
to deal with this unmanaged waste and from this, the concept of ‘Smart Dustbin’
came out.
In this project, We have designed a simple system called Smart Dustbin using
Arduino, Ultrasonic Sensor and Servo Motor, where the lid of the dustbin will
automatically open itself upon detection of human hand.


Methodology &
Work Description


The automation of the smart dustbin is achieved through the use of a simple Arduino
Uno microcontroller. It is an affordable piece of equipment which can be bought online
for a price of INR 400 on almost all major online retailers like Amazon, Flipkart etc.
However to accomplish this project we have also used some basic electrical components in
addition to the microcontroller.
These include a breadboard, Potentiometer, Servo motor, an ultrasonic sensor, an LCD
display, a suitable power supply and of course a lot of connecting wires.
All of these components can be made to interact with each other using the Arduino Uno
Microcontroller with the help of a program called Arduino IDE.
Arduino IDE is a development environment created by the company that manufactures
Arduino microcontrollers.
It is based on C++ programming language and its syntax is easy and intuitive to learn.
Now, the actual code and working of the components is not explained in this slide .
Those come in a later slide. Here only a brief non technical explaination of the
project is given . First all components have to be connected to the Arduino
microcontroller. This is achieved through a device called breadboard . It is an
electronic device that helps connect multiple devices together in a small and
compact space.
The rest of the components used are Servo motor, Ultrasonic sensor , LCD display
jumper wire. Once all the components have been connected using breadboad and
jumper wire(circuit diagram in a later slide), they can be connected to the Arduino
Uno using suitable wiring. Once they are connected all the components can be
programmed using Arduino IDE.(Actual code used is mentioned in later slides).
Using the Arduino IDE the components are porgrammed to work in synchronization. The
Ultrasonic sensor senses an object in front of it and send a signal back to the processor .
When the signal is received, the servo motor is activated . It is attached to the lid of the
dustbin using a thread. It lifts up the lid by pulling on the thread and now the garbage can
be thrown in the dustbin. The LCD screen displays "Dustbin Open" Once the person moves
away from the ultrasonic sensor, it again sends a signal back to the processor which in turn
instructs the servo motor the close the lid by loosening the thread.
After the lid is closed a message is displayed on the LCD Screen below the Ultrasonic sensor
saying" Dustbin Closed".
Arduino Uno Microcontroller. Its a microcontroller which can
be used to control multiple electric components to perform
desired functions. It can be programmed using a software
called Arduino IDE.
The HC-SR04 ultrasonic sensor uses SONAR to determine the
distance of an object just like the bats do. It offers excellent
non-contact range detection with high accuracy and stable
readings in an easy-to-use package from 2 cm to 400 cm or 1”
to 13 feet.The operation is not affected by sunlight or black
material, although acoustically, soft materials like cloth can be
difficult to detect. It comes complete with ultrasonic
transmitter and receiver module.



Tools & Technology


A Servo Motor is a small device that has an output shaft. This
shaft can be positioned to specific angular positions by
sending the servo a coded signal. As long as the coded signal
exists on the input line, the servo will maintain the angular
position of the shaft. If the coded signal changes, the angular
position of the shaft changes.
This is jumper wire. It is used to connect different electronic
devices to each other. A breadboard is often used with jumper
wire for easier connection among the components.
A breadboard is a widely used tool to design and test circuit. You do not need
to solder wires and components to make a circuit while using a bread board. It
is easier to mount components & reuse them. Since, components are not
soldered you can change your circuit design at any point without any hassle. It
consist of an array of conductive metal clips encased in a box made of white
ABS plastic, where each clip is insulated with another clips. There are a
number of holes on the plastic box, arranged in a particular fashion. A typical
bread board layout consists of two types of region also called strips. Bus strips
and socket strips. Bus strips are usually used to provide power supply to the
circuit. It consists of two columns, one for power voltage and other for ground.
The resistor is a passive electrical component to create resistance in the flow
of electric current. In almost all electrical networks and electronic circuits
they can be found. The resistance is measured in ohms.
An LCD is an electronic display module that uses liquid crystal to
produce a visible image. The 16×4 LCD display is a very basic
module commonly used in DIYs and circuits. The 16×4 translates
of a display 16 characters per line in 4 such lines. In this LCD each
character is displayed in a 5×7 pixel matrix.
A potentiometer is a simple knob that provides a variable
resistance, which we can read into the Arduino board as an analog
value. In this example, that value controls the rate at which an
LED blinks. We connect three wires to the Arduino board.
An arduino buzzer is also called a piezo buzzer. It is basically a
tiny speaker that you can connect directly to an Arduino. You can
make it sound a tone at a frequency you set. The buzzer produces
sound based on reverse of the piezoelectric effect.



Implementation Details


#include <LiquidCrystal.h>
#include<Servo.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
Servo servo;
int trig=10;
int echo=9;
void setup() {
lcd.begin(16, 2);
Serial.begin(9600);
servo.attach(7);
servo.write(0);
pinMode(trig,OUTPUT);
pinMode(echo,INPUT);
lcd.setCursor(4, 0);
lcd.print("WELCOME");
delay(2000);
lcd.clear();
lcd.setCursor(3, 0);
lcd.print("Project By:");
lcd.setCursor(3,1);
lcd.print("Project by Sage Students");
delay(4000);
lcd.clear();
lcd.setCursor(1, 0);
lcd.print("Smart Dustbin");
delay(2000);
}
void loop()
{
digitalWrite(trig,LOW);
delayMicroseconds(5);
digitalWrite(trig,HIGH);
delayMicroseconds(10);
digitalWrite(trig,LOW);
int a =pulseIn(echo,HIGH);
int distance = a*0.0343/2;
Serial.println(distance);
if ( distance<50)
{
servo.write(90);
lcd.clear();
lcd.setCursor(1, 0);
lcd.print("Dustbin opened");
delay(500);
}
else
{
lcd.clear();
lcd.setCursor(1, 0);
lcd.print("Dustbin closed");
delay(500);
servo.write(0);
}}
Conclusion & Future Scope
Conclusion overall , the project has achieved its objectives , a prototype of the
smart dustbin was successfully created. This idea can be extended further by
modification of the dustbin to serve additional purposes using additional
components. This concept of a dustbin will encourage more efficient garbage
disposal on behalf of the people . It will also solve the problem of cleanliness
around dustbins in public spaces by eliminating the need of opening the dustbin
manually and littering of garbage around it. A level monitor(GSM) can also be
used to monitor the amount of garbage inside the dustbin. Miniature Solar
Panels can also be used to provide sustainable power to the components of the
dustbin.
Thus, the Smart Dustbin promotes and empowers the idea of Smart City Initiative and
Swachh Bharat Abhiyan.
Thank You
