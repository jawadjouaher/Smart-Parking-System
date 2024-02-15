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


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Diskpart</b>

<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Diskpart</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
