# FREQUENCY-ANALYSER

Web Based Frequency Analyzer using FFT 

This project is a fork of [Webspector](https://github.com/donnersm/Webspector), originally written by Mark Donners.

![Spectrum Analyzer](https://raw.githubusercontent.com/MISTERNEGATIVE21/FREQUENCY-ANALYSER/master/instructables.webp)

The Electronic Engineer:
- Website: [www.theelectronicengineer.nl](www.theelectronicengineer.nl)
- Email: Mark.Donners@judoles.nl

## Description

This project is a web-based 8-64 channel spectrum analyzer designed for the ESP32. It requires only 4 external components. Using the switch, you can select the number of bands to display on the web interface (8, 16, 24, 32, or 64). Upon the first boot, the WiFi manager prompts for your WiFi credentials. If it doesn't, you can force the manager to start by holding the mode button while rebooting.

### Needed Components:
- ESP32 (obviously)
- A switch connected to pin GPIO15(D15) and ground to create a mode button
- Two identical resistors, each between 1K and 50K, connected in series
- Connect one resistor between pin GPIO36 (up) and ground; the other resistor to +3.3V and GPIO36. This creates an offset to your input signal to protect the ESP32
- Connect a 220nF capacitor to GPIO36. The other end of the capacitor is your audio line in

## Functionality

The program operates on both cores: 
- Core 1 runs the main loop and performs the FFT analyses
- Core 0 manages the web interface. Running on different cores ensures that if one freezes, the other remains responsive.

### Important Note
Both functionalities could run on a single core, but by separating them, disturbances to the WiFi signal won't freeze the entire program.

### Getting Started
The HTTP server is initiated, and the webserver task runs on core 0.

## What's New

- Fixed new libraries and dependencies for this repository
- Added an image from Instructables to the README

If you have suggestions or improvements for this project, feel free to contribute or open an issue!

