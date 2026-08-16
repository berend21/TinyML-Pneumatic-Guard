# Project: TinyML-Pneumatic-Guard
On-Device Acoustic AI for Real-Time Leak Detection & Energy Optimization
🛠 Project Overview
This project demonstrates the Smart Retrofitting of a legacy industrial air compressor. By using Local AI (TinyML), the system identifies energy-wasting air leaks and operational anomalies directly at the source, without requiring cloud connectivity.

# 🌟 Key Features
- Edge Intelligence: On-device neural network (Acoustic Classification) trained via Edge Impulse.
- Privacy & Security: 100% local processing; no audio data ever leaves the device.
- Industrial Integration: Real-time data bridging via MQTT (HiveMQ) into Ignition SCADA.
- Sustainable ROI: Correlates energy consumption spikes with detected leaks to calculate real-time financial waste.
# 🏗 The Tech Stack
- Hardware:
* Legacy Air Compressor (Test Bench)
* Raspberry Pi (Edge Gateway) / ESP32 (Sensor Node)
* Analog/I2S MEMS Microphone
- AI/ML:
Edge Impulse: DSP (Digital Signal Processing) and Mel-frequency cepstral coefficients (MFCC) feature extraction.
TensorFlow Lite for Microcontrollers: Local inference.
Communication:
MQTT (HiveMQ): Pub/Sub messaging protocol.
Visualization:
Ignition (Inductive Automation): Industrial dashboard for OEE and anomaly alerts.
# 🚀 Workflow
Data Acquisition: Captured acoustic samples of the compressor in three states: Idle, Normal Pumping, and Leaking (Pressure Drop).
Training: Developed a Convolutional Neural Network (CNN) in Edge Impulse to recognize the specific "hiss" frequency of the leaking valve.
Deployment: Exported the model as a C++ library and ran it on the Raspberry Pi using the Edge Impulse Linux Runner.
Integration:
The Python "Bridge" script monitors the AI output.
Publishes status to factory/workshop/compressor/health.
Ignition subscribes to the topic and triggers a "Maintenance Required" alert if a leak is detected while the motor is off.
