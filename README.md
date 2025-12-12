# ESPHome-Nessie-Key


<img width="1024" height="1024" alt="Mystical Lock and Creatures Emblem" src="https://github.com/user-attachments/assets/122e432a-39fd-4fd0-a7b3-29fc5fc3a5cd" />
Goals of this project is to creat an ESPHome wiegand interpreter with minimal hardware. (e.g M5 NanoC6 and optional voltage regulator) 

Features 
1. Works with commercially available  wiegand readers & wiegand RF receivers
2. Works with commercially available  access control systems (e.g tested on Doorking 1835 & 1838, Liftmaster EL25 & EL2000 & KPR2000, Linear Access AM3 Plus, 3x Logic Infinias Intelli-M , Uhppote, HID Asto series, Mercury LP seriese)
3. Functions with nothing more than M5 NanoC6 excluding power
* Voltage regulator optional
* No tri-state buffer required
* No Optocouplers required
* No diodes required
* No  resisters
* No extra hardware needed to preform wiegand read & write.

4. Simultaneously read and write on 2 wires. 
* Esp Wiegand output is controlled via the lambda functions to allow the output gpio’s to be switched from inputs to outputs on the fly. Overcoming the ESPHome limitations of gpio’s having to be set static to either inputs or outputs & pulled high or low.
11. Ability to preform physical wiegand loop back test. For troubleshooting esp wiegand transmit and receive.
12. Ability to trigger a replay of the last wiegand read with a “unicorn key”. (e.g. FC0 CD0 *not blank)
* Using a card or fob with a Facility code 0 and Card number 0 technically meets all the requirements as a functional card. But is not a card a manufacture sells.
* Commercially available card readers will pass FC0:CD0 card reads through wiegand D0/D1. But access control systems ignore a FC0:CD0 card read. Because all the access control system sees is the start bit and end bit without a card number. It doesn’t even show up in logs. But keep in mind it does trigger the LED on reader.
* The esp does read FC0:CD0 cards to trigger one of three option preselected in the web ui.
            1) Replay last card read
            2) Play manually entered 
                  FC/CD/Bit length 
            3) Play manually entered binary 
* Web ui settings can be changed directly from the web ui or via MQTT.
13. Not depend of WiFi or Bluetooth.
14. Ability to remotely monitor and operate over MQTT 
15. Web ui to see, analyze, monitor, calculate & display wiegand conversions (e.g Flipper hex, raw hex, full hex, fc/cd, full fc/cd etc.)
16. Ability to configure wifi via captive portal.
17. Ability to connect via AP mode
18. Abilility to Scan wiegand
              1) Wiegand Keypad codes
              2) Can set a starting facility code
              3) Can set a starting Card number

Ideas to adding
1. ESPNow integration
2. Isolated wiegand input for standalone reader. To use without direct connection to access control system.
3. De Bruijn (N=2, K=2 (base)) based on Wiegand test frames. Maybe using Lyndon Words and/or de Bruijn graph?
            3a. Pick a window size (e.g., 16 bits, or the full payload length)
            3b. Generate a De Bruijn sequence over alphabet {0,1}
            3c. Slide a fixed-size window across the sequence
            3d. Wrap each window into a proper Wiegand frame:
                        3d1. Add leading/trailing parity bits
                        3d2. Output using correct timing (e.g., 50–100 µs pulses, ~1 ms spacing)
4. exhaustive bit‑pattern stress testing using De Bruijn based pulses with wiegand bit timing (4,8,16,26,27,28,29,31,32,33,34,35,36,37,39,40,48,50,56,64,126 & reverse)
            4a. Isolate all overlaping patterns in 26–29, 31–37 that are duplicated inside 4, 8, 16, 48, 50, 56, 64, 126
            Note:  4, 8, 16, 48, 50, 56, 64, 126 by default have minimal or no overlaping pulses
6. RFID output
7. Add Physical keypad interceptor & replay
