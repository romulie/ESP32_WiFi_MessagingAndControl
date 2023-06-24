Remote LEDs/Loads Control and Message sending via local WiFi network.
Uses WiFi Manager to connect to any WiFi network using Name and Password on Access Point configuration page 
(Possibly can be used from global Web if your router is configured properly or you use static IP).
 
 A simple web server that lets you control LEDs (or turn on/off loads) via the web and WiFi and send messages (up to 38 chars for LCD 16*2, English only)
 This version uses WiFi manager in order to be able to connect to any WiFi network if the password is known:
 ESP32 creates AccessPoint with name "ESP32_Config" (param. ssid_AP, see below). When connected to this AP using
 password "12345678" (param. password_AP, see below) you can automatically visit a page 192.168.4.1 where you can submit credentials
 of the wifi nwtwork to connect to. After that the ESP32 connects to this wifi network and shows it's ip-address in it.
 The IP-address is then shown on the LCD-screen. IP address and MAC address of your WiFi Shield (once connected) are sent to the Serial monitor also.
 
 From there, you can open that address in a web browser to turn on and off the LED (or loads) on pin(s) defined below
 and send messages which are then displayed on the LCD screen.
 Buzzer plays short melody once a minute if incoming message is not read.
 Using push-button you can reset the received message, disable melody and turn-off the backlight of the LCD screen
 You can see the status of the LEDs/loads and the status of the message (read or not and for how long) on the web-page as well.

 If the IP address of your shield is yourAddress:
 http://yourAddress/L=1 turns the LED/load on
 http://yourAddress/L=0 turns it off

 This example is written for a network using WPA2 encryption. For insecure
 WEP or WPA, change the Wifi.begin() call and use Wifi.setMinSecurity() accordingly.

 Circuit:
 ESP32WROOM;
 LED(load) attached to pin 13;
 Push-button attached to pin 12 (should have pull-up);
 I2C LCD 16*2 attached to pins 21(SDA) and 22(SCL) (I2C of ESP32), VCC and GND
 Piezo buzzer is attached to pin 19(+) and GND via 100 Ohm resistor

created for arduino 25 Nov 2012 by Tom Igoe and modified Jun 2023 by romulie
ported for sparkfun esp32  31.01.2017 by Jan Hendrik Berlin
