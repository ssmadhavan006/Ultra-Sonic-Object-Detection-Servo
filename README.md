# 🚨 Ultrasonic Object Detection with Arduino + Servo

This project demonstrates how to build a simple object detection system using an **HC-SR04 ultrasonic sensor** and an **SG90 servo motor**. When an object comes within 20 cm, the servo motor reacts accordingly.

---

## 🧠 How It Works

- The **HC-SR04 ultrasonic sensor** continuously measures the distance to an object.
- If an object is detected within a threshold distance (e.g. **< 10 cm**), the **servo motor** rotates to respond.
- Otherwise, the servo remains at its default position.

---

## 🔌 Circuit Diagram

Below is the wiring schematic for this project:

![Ultrasonic Object Detection Circuit](./ultra_sonic_object_detection.png)

---

## 🔧 Components Used

More details in [`components.txt`](./components.text)

---

## Noteworthy techniques

| Technique | Why it’s interesting |
|-----------|---------------------|
| Continuous polling inside `loop()` &rarr; mirrors the browser [**event loop**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop) | Shows how MCU firmware uses the same non-blocking update model web devs rely on. |
| Linear range conversion with `map()` | Compresses the 10-bit ADC range (0-1023) to the servo’s 0-180 ° sweep in one line. |
| Timing distance with `pulseIn()` | Reads echo pulse width in µs, converts to cm using the speed-of-sound constant. |
| Single-supply power + common ground plane | Cuts servo jitter and false echoes without extra regulators. |

---

## Non-obvious tech & libs

* **Arduino Servo library** – drives the SG90 from a single PWM pin.  
* **TinkerCAD Circuits** schematic ([`ultra_sonic_object_detection.png`](./ultra_sonic_object_detection.png)) – quick virtual test-bed.  
* **USB CDC Serial Monitor** – lightweight telemetry channel for live distance read-outs.
* 
---
