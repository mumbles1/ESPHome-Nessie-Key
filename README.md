# ESPHome-Nessie-Key

Goals of this project is to creat an ESPHome wiegand interpreter with minimal hardware. (e.g ESP8266 chip and optional voltage regulator) 

Features 
1. Works with commercially available  wiegand readers & wiegand RF receivers
2. Works with commercially available  access control systems
3. Functions with nothing more than ESP8266 chip excluding power
*  Voltage regulator optional
* Voltage regulator optional
* No tri-state buffer required
* No Optocouplers required
* No diodes required
* No  resisters
* No extra hardware needed to preform wiegand read & write.
4. Voltage regulator optional
5. No tri-state buffer required
6. No Optocouplers required
7. No diodes required
8. No  resisters
9. No extra hardware needed to preform wiegand read & write.  
10. Simultaneously read and write on 2 wires. 
* This is actually achieved using 4 gpio pins. 
*  All 4 gpio pins are intentionally configured as input pins in YAML. This keeps all 4 gpio pins floating at idle, to prevent esp outputs from pulling the wiegand D0 & D1 high or low causing interruptions that block wiegand reads from both the esp and access control system.
* Esp Wiegand output is controlled via the lambda funtions to allow the output gpio’s to be switched from inputs to outputs on the fly. Overcoming the ESP limitations of gpio’s having to be set static to either inputs or outputs & pulled high or low.
11. Ability to preform physical wiegand loop back test. For troubleshooting esp wiegand transmit and receive.
12. Ability to trigger a replay of the last wiegand read with a “unicorn key”. (e.g. FC0 CD0 *not blank)
* Using a card or fob with a Facility code 0 and Card number 0 technically meets all the requirements as a functional card. But is not a card a manufacture sells.
* Commercially available card readers will pass FC0:CD0 card reads through wiegand D0/D1. But access control systems ignore a FC0:CD0 card read. Because all the access control system sees is the start bit and end bit without a card number. It doesn’t even show up in logs.
* The esp does read FC0:CD0 cards to trigger one of three option preselected in the web ui.
            1) Replay last card read
            2) Play manually entered 
                  FC/CD/Bit length 
            3) Play manually entered binary 
* Web ui settings can be changed directly from the web ui or via MQTT.
13. Not depend of WiFi or Bluetooth.
14. Ability to remotely monitor and operate over MQTT 
15. Web ui to see, analyze, monitor a
16. Ability to configure wifi via captive portal.
17. 
