# ESPHome-Nessie-Key

Goals of this project is to creat an ESPHome wiegand interpreter with minimal hardware. (e.g ESP8266 chip and optional voltage regulator) 

Features 
1. Function with nothing more than ESP8266 chip excluding power
2. Voltage regulator optional.
    1. No extra hardware needed to preform wiegand read & write.   
3. Simultaneously read and write on 2 wires.
4. Ability to preform physical wiegand loop back test. For troubleshooting wiegand transmit and receive.
5. Ability to trigger a replay of the last wiegand read through a “unicorn key”. 
6. No dependency of WiFi or Bluetooth.
7. Ability to remotely monitor and operate over MQTT
8. Ability to configure wifi via captive portal.
9. 


