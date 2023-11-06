# FREQUENCY-ANALYSER
Web Based Frequency Analyzer using FFT 
Certainly! To enhance this ESP32-based web interface for a spectrum analyzer, here are some improvements and additional features you might consider:

This is a fork of WEBINSPECTOR written by Mark Donners

The Electronic Engineer.
www.theelectronicengineer.nl
email: Mark.Donners@judoles.nl

Web bases 8-64 channel spectrum analyzer for ESP32
![Spectrum Analyzer]([https://github.com/MISTERNEGATIVE21/FREQUENCY-ANALYSER/instruct.webp])
This project uses a ESP32 DEVKIT V1 and only 4 external components.
Using the switch, you can select the number of bands you want to display on the webinterface 8,16,24,32 or 64
Uppon first boot, the wifi manager will kick in asking your WIFI credentials. If it doens't, you can force the 
manager to start by holding the mode button while rebooting.

Needed components:
ESP32 ( obviously )
Connected a switch to pin GPIO15(D15) and ground to create a mode button
Two identical resistor. can be any value between 1K and 50K als long as you use 2 of the same
Connect 1 resistor between pin GPIO36 (up) and ground. Connect the other resistor to +3.3V and GPIO36 
This will create an offset to your input signal to protect the esp32
Connect a capacitor of 220nF to GPIO36. The other end of the capacitor is your audio line in


The program is running on both cores. Core 1 is used for the main loop and does the FFT analyses
Core 0 is used for the webinterface. Both could run on 1 core but whenever the WIFI signal is disturbed,
for example by putting hand over the ESP32, the program would freeze...and the userinterface is not monitored.
Therefore, the webserver is on a different core. If it freezes up, the user interface will still work.
 
HTTP server started
Webserver task is  running on core 0

Whats New : -
fixed new libraries and dependencies for this repo added pic from instrutables
