# Waste Segregation System - Syed Ahmed Raza's Lab Notebook
**ECE 445 - Senior Design, Spring 2025**
**Team #55**

## Project Overview
This notebook documents my contributions to our Waste Segregation System project, focusing primarily on PCB design, microcontroller programming, and system integration.

## Development Log

### Week of February 17, 2025
- Had design review meeting with Professor Oelze and TA Maanas
- Created preliminary block diagram showing power, vision, and mechanical subsystems
- Started researching voltage regulators for 12V to 5V conversion

### Week of February 24, 2025
- Finalized high-level subsystem division with team members
- Began schematic design in KiCAD for PCB
- Calculated power requirements for stepper and servo motors

### Week of March 3, 2025
- Completed initial PCB schematic with power distribution and microcontroller connections
- Tested 2.2kΩ/4.7kΩ resistive voltage divider for 5V to 3.3V conversion

### Week of March 10, 2025
- Assembled breadboard prototype of control system
- Demonstrated some functionality to the Professor and TA
- Started writing firmware for the ATmega2560 microcontroller to control motors
- Submitted PCB order to JLCPCB

### Week of March 17, 2025
- Spring Break - Continued development of microcontroller code
- Developed preliminary UART communication protocol between Pi and microcontroller

### Week of March 24, 2025
- Received the first PCB and identified trace width issues for power lines
- Implemented HX711 load cell interface with calculated calibration factor of 671363.12
- Tested load cell sensitivity with a 5g threshold for waste detection

### Week of March 31, 2025
- Revised PCB design with improved power traces and additional filtering capacitors
- Implemented emergency stop functionality in firmware
- Developed and tested servo motor control code

### Week of April 7, 2025
- Submitted PCB order to JLCPCB
- Created a stepper motor positioning algorithm for bin rotation
- Integrated status LED indicators for system state monitoring

### Week of April 14, 2025
- Assembled complete system with revised PCB
- Synchronized communication between the Raspberry Pi and the microcontroller
- Implemented error handling and recovery procedures in firmware

### Week of April 21, 2025
- Conducted mock demo with TA Maanas
- Fine-tuned timing parameters for servo and stepper motors
- Verified emergency stop response time of 1.2 seconds

### Week of April 28, 2025
- Performed final demonstration with Professor Oelze and TA Maanas
- Compiled testing data for final report

### Week of May 5, 2025
- Presented project to Professor Oelze and TA Maanas
