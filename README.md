<h1>JWipe - Disk Sanitization</h1>



<h2>WORK GOAL AND PERFORMANCE </h2>
Our team developed a parking system that utilizes an IR receiver sensor and an ultrasonic sensor to detect the presence of a vehicle and provide authorized access only. With the system controlled by a remote control with an IR transmitter, it is user-friendly and easy to operate.
To begin, when a user approaches the parking space, they use the remote control to send a signal to the
IR receiver sensor. The system verifies the signal and unlocks the parking space, allowing the user to
park their vehicle. This serves as an additional security measure to prevent unauthorized access, as
only users with an authorized remote control can access the parking space.
Should an unauthorized user attempt to access the parking space, the ultrasonic sensor immediately detects the presence of the vehicle and triggers a danger alarm using a buzzer. This feature provides an
extra layer of security and alerts the user of any unauthorized access attempts.
Our parking system will be implemented using an Arduino UNO Wi-Fi Rev 2 microcontroller board,
base shield, and IR receiver sensor from Elegoo, and an ultrasonic sensor from Elegoo. The Grove
LCD Display should be included in the system to display the parking status and other important information.
The project should successfully create a secure and convenient parking system that offers an alert
when an unauthorized access attempt is made. The system can be customized according to specific
needs, making it a useful and practical solution for parking management.
<br />
<h2>PART LIST</h2>

- <b>We used the following components:
• Arduino UNO Wi-Fi Rev 2
• Base Shield
• Grove LCD Display
• Grove Buzzer
• IR Receiver Elegoo
• Ultrasonic Sensor Elegoo
Breadboard
• Wires </b> 

<h2>Languages Used</h2>

- <b>C++</b> 

<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Diskpart</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Schematics: <br/>
<img src="https://i.imgur.com/AtlEFKu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Assembly Drawing:  <br/>
<img src="https://i.imgur.com/56VDnd1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 <h2>CODE , OUTPUT AND PICTURE OF THE WORK:</h2>
- <b>Code</b>
#include <IRremote.h>
#include "rgb_lcd.h"
#include "SR04.h"
#define TRIG_PIN 2
#define ECHO_PIN 3
#define IR_PIN 5
#define BUZZER_PIN 3
SR04 sr04 = SR04(ECHO_PIN, TRIG_PIN);
IRrecv irrecv(IR_PIN);
decode_results results;
rgb_lcd lcd;
bool is_allowed = false;
unsigned long start_time = 0;
void setup() {
Serial.begin(9600);
irrecv.enableIRIn(); // enable IR receiver
lcd.begin(16, 2);
lcd.setRGB(255, 255, 255); // set background to white
noTone(BUZZER_PIN); // turn off the buzzer
}
void loop() {
long distance = sr04.Distance();
Serial.print(distance);
Serial.println(" cm");
if (distance <= 5) {
if (!is_allowed) {
lcd.setCursor(0, 0);
lcd.print("Hello, please");
lcd.setCursor(0, 1);
lcd.print("Press button");
lcd.setRGB(0, 191, 255); // set background to light blue
}
// Wait for IR signal
if (irrecv.decode(&results)) {
is_allowed = true;
start_time = millis();
lcd.setRGB(0, 255, 0); // set background to green
lcd.clear();
lcd.print("Allowed :)");
tone(BUZZER_PIN, 1000, 500); // make a sound of 1000 Hz for 500 milliseconds
irrecv.resume(); // receive the next IR signal
}
} else {
unsigned long elapsed_time = millis() - start_time;
if (elapsed_time > 6000) {
is_allowed = false;
lcd.setRGB(255, 0, 0); // set background to red
lcd.clear();
lcd.print("Not Allowed");
tone(BUZZER_PIN, 500, 9000); // make an alarm sound of 500 Hz for 9 seconds
delay(3000); // Wait 3 seconds before displaying "Hello, please Press any button" message
lcd.setRGB(0, 191, 255); // set background to light blue
lcd.clear();
lcd.setCursor(0, 0);
lcd.print("Hello, please");
lcd.setCursor(0, 1);
lcd.print("Press button");
noTone(BUZZER_PIN); // turn off the buzzer
}
}
delay(100);
}
Code report:
This code controls a parking system using an ultrasonic sensor, an IR receiver, and a buzzer. It
measures the distance between an object and the sensor and only allows access when the object is
within 5cm of the sensor. The user can then send an IR signal to the IR receiver to allow entry. If the
object is not allowed to enter, a danger alarm is triggered using the buzzer. The LCD display is used to
show status messages such as "Allowed" or "Not Allowed." The code uses the IRremote library for the
IR receiver and the SR04 library for the ultrasonic sensor. The buzzer is controlled using the tone() and
noTone() functions.

Initial Display: <br/>
<img src="https://i.imgur.com/5HvyPzZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Initial State: Waiting for User Input:
In this state, the parking system is waiting for the user to initiate the parking process. The ultrasonic
sensor is constantly monitoring the distance between the sensor and any nearby objects. When the distance is less than or equal to 5 cm, the LCD display shows a message that says "Hello, please press any
button" and the background color is set to light blue. This indicates to the user that they should use the
remote control to signal that they want to park their vehicle.<br />
<br />
Unauthorized Access Attempt:  <br/>
<img src="https://i.imgur.com/iaGbsOS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

In this state, the parking system detects that a vehicle has approached the parking space, but the user
has not pressed any buttons on the remote control. This means that the vehicle is not authorized to park
in the space. The LCD display shows a message that says "Not Allowed" and the background color is
set to red to indicate that the user should not attempt to park in the space. Additionally, an alarm sound
is played through the buzzer to further discourage unauthorized access.<br />
<br />
Authorized Access:  <br/>
<img src="https://i.imgur.com/VfatlaM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
In this state, the parking system detects that a vehicle has approached the parking space and the user
has signalled that they want to park by pressing a button on the remote control. The LCD display shows
a message that says "Allowed :)" and the background color is set to green to indicate that the user is
authorized to park in the space. Additionally, a confirmation sound is played through the buzzer to signal
that the user can proceed with parking their vehicle.<br />
<br />
<h2> Detailed Visuals </h2>
<img src="https://i.imgur.com/H6TqKcp.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/0LvR3jc.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5qdrHVr.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
<h2>Challenges </h2>
During the development of our project, we encountered several challenges that required us to
modify our initial ideas. One of the significant obstacles we faced was programming the IR
receiver. The receiver was receiving the same signals for all buttons, which made it challenging
to differentiate between them. This obstacle required us to rethink our approach and find a new
solution that worked effectively also it caused delays in our progress.
Another challenge we faced was wiring the project. We found that we needed to use pin 5V for
both the ultrasonic sensor and IP receiver, which posed a significant challenge. We were able to
overcome this challenge by using a breadboard to ensure proper connections.
Writing the appropriate code was another challenge we faced. We needed to create a code that
would effectively communicate between the different components of the project, which required
us to do significant research and testing to find the best solution.
Despite these challenges, we were able to design and build a functional garage using lego pieces.
We focused on putting the components in the best positions to ensure the best view for viewers.
Though we experienced setbacks, we were able to overcome them and successfully complete
the project
<br />

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
