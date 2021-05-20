# NodeMCU files for online attendance system
NodeMCU code files for Online attendance system
Step 1:
1. Add the ESP boards to the Arduino IDE.
2. Add the RFID library from Sketch--Include Library--Manages Libraries--search for (RFID)--then Install it.
3. After having the RFID-module wired to the nodeMCU like this:
 
`SDA --- D8`

`SCK --- D5`

`MOSI --- D7`

`MISO --- D6`

`IRQ --- Not connected`

`GND --- GND`

`RST --- D3`

`3.3V --- 3.3V`

Connect it to the computer using a Micro USB.

4. Open the RFID_NodeMCU code and enter your WiFi setting(Name, Password) and your computer IP(you can know it from the command line by typing "ipconfig" then check ipv4), after that select the nodeMCU board from Tools--boards with the correct Port COM, and then upload it.

6. Open the serial monitor and set the baud rate to 115200 to check the connection status and the nodeMCU IP, save the IP(to put it in the server file "httpd.conf").
Step 2:
1. Download the WampServer or xampp and install it.
2. Run it.
3. If you're using WAMPServer 2.1:
Click on wamp icon: Apache--httpd.conf--Add the nodeMCU IP to the permit list ( Allow from "nodeMCU IP")or try(Allow from all) next to this line: Allow from 127.0.0.1, then save it.
while If you're using WAMPServer 3.0.6:
Click on wamp icon: Apache--httpd-vhosts.conf--simply replace “Require local” with “Require all granted“ or "Require ip 192.168.xx.xx"(nodeMCU IP), then save it.
4. Click on wamp icon: Restart all services.
5. Click on wamp icon: www directory, then copy the website folder(login system folder) into it.
6. Click on wamp icon: localhost--login system--install.php(It should give you a success message, if not check the PHPMyAdmin password and username from (C:\wamp\apps\phpmyadmin3.3.9\config.inc.php) then put the password in (connectDB.php and install.php) pages.
7. Go to localhost/loginsystem/AddCard.php to add the users.
8. Then localhost/loginsystem/view.php to check the log.
It should appear on the serial monitor these messages:
for a new card or an available card:
200
successful
"the cardID"
and should the two LEDs blink 
for a login:
200
login
"the cardID"
and should the red LED turn on
for a logout:
200
logout
"the cardID"
and should the blue LED turn on
## Note:
You need to edit three variable values:
1. Wifi Name
2. Wifi Password
3. IP address of your server(IP address of your computer is also the same)
4. Add IP address again in Get data section of the code
5. All the note instructions are commented inside the code file for easy understanding.
If you don't have extra LEDs then just comment out the lines from starting(Initialising LED pins) till the end wherever you come across LED word in Code
