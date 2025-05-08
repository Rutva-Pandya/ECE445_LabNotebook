# Waste Segregation System - Rutva Pandya's Lab Notebook
**ECE 445 - Senior Design, Spring 2025**  
**Team #55**

## Project Overview
This notebook documents my contributions to our Waste Segregation System project, with a primary focus on the design, development, and testing of the **Computer Vision Model**, as well as the **Vision** and **Processing Subsystems**. I also contributed to the PCB design, soldering, and hardware debugging, collaborating closely with Syed to bring the electrical subsystems online.

---

## Development Log

### Week of February 17, 2025
- Outlined vision subsystem scope with team: capture, classification, and communication pipeline.
- Explored options for camera hardware: Chose Raspberry Pi Camera V2 due to direct connectivity & integration to Raspberry Pi 4.
- Identified classification latency target: ≤1.5 seconds. Began reviewing embedded ML options compatible with Pi 4.

---

### Week of February 24, 2025
- Finalized subsystem responsibilities. Took full ownership of image capture and classification pipeline.
- Selected **Raspberry Pi Camera** initially for native compatibility and reduced power draw.
- Assisted Syed in setting up the first PCB schematic and began layout discussions in KiCAD.
- Evaluated TrashNet as the base dataset and noted missing "Non-Recyclables" class and limited variation in lighting.

---

### Week of March 3, 2025
- Cleaned and filtered **TrashNet** data (~2,500 images) for base model training.
- Designed custom dataset plan with samples sourced from the **Machine Shop** (plastic, metal, paper, non-recyclables).
- Defined preprocessing pipeline: resizing, grayscale conversion, and contrast normalization.
- Began training **MobileNetV2** with transfer learning on combined TrashNet + machine shop samples.
- Assisted Syed in testing voltage regulators and level shifting circuits. Verified 5V-to-3.3V logic conversions.

---

### Week of March 10, 2025
- Benchmarked three candidate models (MobileNetV2, EfficientNet-lite0, ResNet50 on TFLite):
  - **MobileNetV2** had the lowest average inference time on Pi 4 (~1.3s).
  - Accuracy on validation set: MobileNetV2 = **88%**, EfficientNet = 45.5%, ResNet = 83.4%.
  - Selected MobileNetV2 due to ideal tradeoff between accuracy and latency.
- Implemented confidence threshold filter (≥0.70) to reduce false positives.

---

### Week of March 17, 2025
- Spring Break: Worked on Raspberry Pi 4 software integration and preliminary firmware syncing.
- Configured TensorFlow Lite runtime and validated on-device inference with the Pi camera.
- Developed classification pipeline (capture → preprocess → inference → UART communication).

---

### Week of March 24, 2025
- Raspberry Pi Camera module failed during extended testing → decided to switch to **Logitech Brio** for image acquisition.
- Updated preprocessing pipeline to account for Brio’s RGB input and color correction under yellow lighting.
- Collected additional metal/Non-Recyclables test cases from the **Machine Shop** and retrained model.
- Helped Syed test the HX711 load cell interface and verify calibration threshold (~5g minimum sensitivity).

---

### Week of March 31, 2025
- Final model metrics:
  - Accuracy: **88%** on test set (n = 100)
  - Inference latency: **1.29s avg**, **1.5s max**
  - CPU utilization: **72% avg**, **78% peak**
- Integrated GPIO-based status LED control into the Pi processing script.


---

### Week of April 7, 2025
- Conducted 25 test runs on live waste items in lab lighting:
  - 2 misclassifications (plastic-metal confusion)
  - Mean latency: **1.31s**
- Assisted with integrating system state feedback LEDs (green, yellow, blue) and verifying transitions.
- Created a stepper motor bin-selection test case generator for mechanical subsystem.

---

### Week of April 14, 2025
- Tested model in low-light and yellow LED environments → observed ~6% drop in accuracy.
- Introduced histogram equalization during preprocessing → restored performance to 86%+.
- Helped debug emergency stop logic and confirmed shutdown response of **1.2s** for motors and camera script.

---

### Week of April 21, 2025
- Performed full stress test on mixed waste (n=50):
  - Classification + sorting cycle: **4.8s avg**
  - No jams or communication errors
- Conducted Mock Demo with TA & recorded feedback.

---

### Week of April 28, 2025

- Validated full Vision + Processing pipeline in real-time with system-wide performance logging.
- Worked on stress-testing project & getting started with Final Presentation & Report.

---

### Week of May 5, 2025
- Participated in final demonstration with Professor Oelze and TA Maanas.
- Explained model pipeline, camera transition, and why MobileNetV2 was chosen over EfficientNet.
- Supported final report and presentation:
  - Prepared visuals for processing pipeline and model benchmarks
  - Reviewed Verification section for Vision & Processing subsystems