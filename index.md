# Human Following Robot
This portfolio follows my progress over the summer as I worked on numerous projects. It tracks the numerous challenges I had to overcome and notes the milestones I hit. I started my summer by putting together a retro tetris arcade console, which was a simple yet tedious task as it required much soddering. For my intensive project, I built and programmed a robot designed to follow people around like a pet.

<!--You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:-->
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
``` 

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Zoya C. | Mission San Jose High School | Electrical Engineering | Incoming Junior

<!---**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image]()
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone -->

# First Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/CaCazFBhYKs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

My intensive project is a robot on wheels that can follow you around. I'm relatively inexperienced in the robotics field, so I began my project by testing several parts and their corresponding programs for my first milestone in order to gain a greater understanding of them. I used the ARDUINO R3 circuitboard with jumpwires for all of these tests.

***LED LIGHTS:*** For my first test, I put together a simple circuit to test the LED lights in this set, along with the code to make the light flash.
- SCHEMATICS: ![Headstone Image] (logo.svg)
- CODE: 
```
//naming the pin the LED light is plugged into
const int ledPin = 9;

void setup()
{
  //initialize the digital pin as an output
  pinMode(ledPin,OUTPUT);
}

//the loop routine runs over and over again forever
void loop()
{
  digitalWrite(ledPin,HIGH);//turn the LED on 
  delay(500);               //wait for half a second (number corresponds miliseconds)
  digitalWrite(ledPin,LOW); //turn the LED off
  delay(500);               //wait for half a second
}
```
- What your plan is to complete your project

***BUZZER:*** The next project sought to find out how the buzzer worked. The setup of the two projects, as well as the coding, was very similar. The main differences could be found in the lack of a resistor (and obviously the component's function).
- SCHEMATICS: ![Headstone Image] (wiring_active_buzzer.webp)

- CODE:
```
//naming the pin the buzzer is plugged into (the pin doesn't necessarily need to be a specific name, as long as the code # corresponds to the circuit's pin #  being used)
const int buzzerPin = 8;

void setup()
{
  pinMode(buzzerPin, OUTPUT);
}

void loop()
{
    digitalWrite(buzzerPin, HIGH);
    delay(1000);
    digitalWrite(buzzerPin, LOW);
    delay(1000);                  //time doesn't have to be different from LED, just a suggestion since it's loud :)
  }
```

***WHEEL MOTOR:*** While having the same fundamentals as the previous projects, this was slightly more complicated as there were more componenents to the motor to put together. The motor itself had two wires that required a screwdrier in order to be plugged into the motor module.
- SCHEMATICS: ![Headstone Image] (wheel_motor.webp)
- CODE:
```
const int B_1A = 9;
const int B_1B = 10;

void setup()
{
  pinMode(B_1A, OUTPUT);
  pinMode(B_1B, OUTPUT);
}

void loop()
{
  //rotates motor clockwise
  digitalWrite(B_1A, HIGH);
  digitalWrite(B_1B, LOW);
  delay(2000);

  //stops motor
  digitalWrite(B_1A, LOW);
  digitalWrite(B_1B, LOW);
  delay(500);

  //rotates motor counterclockwise
  digitalWrite(B_1A, LOW);
  digitalWrite(B_1B, HIGH);
  delay(2000);

  //stops motor (again)
  digitalWrite(B_1A, LOW);
  digitalWrite(B_1B, LOW);
  delay(500);
}
```

***SERVO MOTOR:**** While the previous motor is designed for simpler functions like rotating a wheel, this motor could control the angle it rotated (from 0-180°) in order to control a servo arm. However, I did need to include the Servo.h library to run the code.
- SCHEMATICS: ![Headstone Image] (swinging_servo_bb.jpg)
- CODE:
```
#include <Servo.h>

Servo myservo;//create servo object to control a servo

void setup()
{
  myservo.attach(9);//attachs the servo on pin 15 to servo object
  myservo.write(0);//back to 0 degrees
  delay(1000);//wait for a second
}

void loop()
{
  for (int i = 0; i <= 180; i++)
  {
    myservo.write(i); //write the i angle to the servo
    delay(15); //delay 15ms
  }
  for (int i = 180; i >= 0; i--)
  {
    myservo.write(i); //write the i angle to the servo
    delay(15); //delay 15ms
  }
}
```

***IR OBSTACLE AVOIDANCE:*** This sensor detects obstacles by transmitting IR rays and receives them when a surface (of an object) reflects them back. If you opened the serial monitor, a 1 would correspond with no nearby object while a 0 would alert you of one. 

- SCHEMATICS:
- CODE:
```
int irObstaclePin = 2;

void setup() {
  Serial.begin(9600);
  pinMode(irObstaclePin, INPUT);
}

void loop() {
  Serial.println(digitalRead(irObstaclePin));
  delay(10);
}
```

***ULTRASONIC SENSOR:*** This works similar to the IR sensor, but instead uses ultrasonic frequencies in order to detect how far objects.

- SCHEMATICS:
- CODE:
```
const int echoPin = 3;
const int trigPin = 4;


void setup(){
  Serial.begin(9600);
  pinMode(echoPin, INPUT);
  pinMode(trigPin, OUTPUT);
  Serial.println("Ultrasonic sensor:");  
}

void loop(){
  float distance = readSensorData();
  Serial.print(distance);   
  Serial.println(" cm");
  delay(400);
}

float readSensorData(){
  digitalWrite(trigPin, LOW); 
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH); 
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);  
  float distance = pulseIn(echoPin, HIGH)/58.00;  //Equivalent to (340m/s*1us)/2
  return distance;
}
```
 

 # Starter Project
***DESCRIPTION:*** In preperation for the hardware aspects of my intensive projects, I warmed up by putting together a retro arcade console designed to play numerous games of tetris. It can be powered by either batteries or your laptop by connecting it via the USB socket. You then start a game by turning on the red power button and pressing the yellow button labeled with a square. The game is displayed on the dot matrix, and the pieces can be controlled by the four buttons labeled with arrows. While you play, the digital cube keeps track of your score, and the buzzer provides sound effects/music. The game can be ended with the button labeled X, pressing the power button, or disconnecting the power source. Every component was soddered on, and the non-electrical parts were screwed together.


***CHALLENGES:*** he main obstacle for this project was the amount of tedious soddering required. The dot matrix, digital tube, and power switch were relatively simpler. The challenge from these parts was that they had numerous parts to sodder--most of which were very close together. This meant having to meticulously sodder without accidentally connecting two holes together. Other parts, however, didn't fit into the circuitboard's holes as perfectly. As a result, I had to pay careful attention to how much sodder I added and how it was added. The wires, for example, had to be held while soddering because the wires were way too small incomparison to the holes and could also come apart and require retwisting. Additionally, the wires were much longer and would move around if not held. A slight concern was burning the circuitboard when adjusting sodder/desoddering, but this went away with time and practice. Putting together the outer parts was a straightforward task, but could sometimes be confusing since it was more difficult to tell if some screws were fully screwed.


***WHAT'S NEXT:*** Now that I've finished my starter project, I can look forward to working on my intensive project: building a human following robot. My immediate next steps are testing all the components of it, such as the sensors and motors, as well as gaining a better understanding of the ARDUINO coding software.


<!--# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.-->
