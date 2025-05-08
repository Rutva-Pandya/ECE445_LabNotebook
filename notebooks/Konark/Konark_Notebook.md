# Waste Segregation System – Konark Dhingreja's Lab Notebook

**ECE 445 – Senior Design, Spring 2025**  
**Team #55**

## Project Overview

This notebook documents my contributions to our Waste Segregation System project, with a focus on the **Power Subsystem Design** and **Motor Selection & Integration**. I was responsible for calculating power requirements, designing and testing the 12V to 5V regulator circuit, and selecting/tuning the motors used for waste sorting. I also verified timing behavior, power stability, and integrated motor control with system feedback indicators.

## Development Log

### Week of February 17, 2025
- Participated in design review with Prof. Oelze and TA Maanas.  
- Finalized project scope: a vision-based smart bin that classifies trash into recyclable and non-recyclable categories.  
- Assigned to power and mechanical subsystems.  
- Calculated power budget (stepper + servo + Pi): estimated max draw = ~2.5–3.0 A.  
- Decided on 12V, 5A supply with 12V rail for motors and regulated 5V logic line.  
- Sketched power block diagram with labeled paths for regulation and control logic.

### Week of February 24, 2025
- Tested LM7805 voltage regulator circuit using 470μF, 10μF, 0.1μF, and 22pF capacitors.  
- Output held steady at 5.02V with load up to 1.2A.  
- Researched motor options. Initially chose Nema 11 (18 N·cm torque).  
- Estimated load torque from bin: m · g · r ≈ 0.5 kg · 9.8 m/s² · 0.03 m ≈ 0.15 Nm


### Week of March 3, 2025
- Found Nema 11 insufficient — lacked margin for jammed bin rotation.  
- Upgraded to Nema 17 (45 N·cm holding torque), confirmed compatibility with L298N driver.  
- Evaluated voltage level shifting options between ATmega2560 (5V) and Raspberry Pi (3.3V).  
- Initially tested resistive divider (2.2kΩ / 4.7kΩ), then adopted TXB0101DBVR for bidirectional translation.  
- Finalized power subsystem schematic; annotated components and voltage paths.

### Week of March 10, 2025
- Validated Nema 17 motor response under simulated load.  
- Integrated DS3218 servo motor — tested PWM mapping:  
- 0° = 0.5 ms  
- 90° = 1.5 ms  
- 120° = 2.0 ms  
- Breadboarded power chain, added kill switch across motor rail.  
- Verified Pi ↔ ATmega UART via TXB0101 @ 9600 baud.

### Week of March 17, 2025 *(Spring Break)*
- Measured LM7805 surface temp under continuous 1.1A load → ~58°C, within spec.  
- Simulated combined servo + stepper draw, confirmed no brownout.  
- Observed servo peak current draw: ~0.75A, stepper: ~1.3A.  
- Verified clean 3.3V and 5V levels at TXB0101 output.

### Week of March 24, 2025
- Received first PCB, soldered in LM7805 + decoupling caps.  
- Measured barrel jack input: 12.09V, regulated output: 5.01V.  
- Initial servo mount collided with bin wall. Flagged for reorientation.  
- Installed 1kg load cell; tested analog reading drift over multiple trials.  
- Laser ToF sensor not yet integrated due to interfacing delays.

### Week of March 31, 2025
- Revised power trace width on PCB (motor trace was too thin).  
- Kill switch tested: motors halted within 1.2s of activation.  
- Recorded oscilloscope capture of PWM waveforms.  
- Voltage ripple under surge (both motors active): <0.18V, acceptable.

### Week of April 7, 2025
- Final PCB submitted with improved copper fill and labels.  
- Installed indicator LEDs:  
- Green = Ready  
- Yellow = Sorting  
- Blue = Jam  
- Confirmed GPIO toggling from ATmega2560 with logic probe.  
- Implemented debounce logic for jam state transitions.

### Week of April 14, 2025
- Reoriented servo mounting bracket to prevent mechanical obstruction.  
- Verified 120° push motion succeeded for 500g object.  
- Conducted bin cycle tests: stepper rotation completed in <3s, servo push in ~1.1s.  
- Verified system synchronization with load and timing thresholds.  
- Retested TXB0101 output limits: all voltages remained within spec.

### Week of April 21, 2025
- Mock demo: passed all subsystem checks.  
- Verified Requirements 6–8, 14–16 using multimeter + stopwatch.  
- Power stability was maintained over 10 back-to-back sorting cycles.  
- Added test point labels to schematic and finalized submission drawings.

### Week of April 28, 2025
- Final TA demo: all subsystems performed as expected.  
- Emergency stop response verified under loaded operation.  
- Compiled voltage/current readings:  
- Servo: 0.75A  
- Stepper: 1.2–1.4A  
- Vreg: 5.00V ±0.02V  
- Documented circuit test results in final report.

### Week of May 5, 2025
- Signed off the lab notebook and submitted all documentation.  
- Participated in the final project presentation.  
- Answered questions related to power architecture, regulator design, and motor verification.
