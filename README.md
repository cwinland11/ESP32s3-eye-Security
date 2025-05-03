# ESP32s3-eye-Security
A low-cost, hands-on security “toy” built around the ESP32-S3 Eye and Arduino Mega 2560. When motion is detected, a 15-second timer starts and the system listens for the spoken command “yes”. If the model (kept under 20 KB for microcontroller constraints) recognizes “yes” in time, it lights a green LED; otherwise it switches on a red LED.

Hardware
- ESP32-S3 Eye (camera + microphone + TensorFlow Lite Micro inference)
-  Arduino Mega 2560 (LED/buzzer control)
-  PIR motion sensor (triggered 15s listening window)
-  Green & red LEDs (confirmation/timeout)
-  (Optional) buzzer for audible alert

Software
-  ESP-IDF v4.4 on the ESP32-S3 Eye
-  Arduino IDE 1.8.x on the Mega 2560
-  TensorFlow Lite for Microcontrollers model (model_data.h)

Workflow
Idle & Arm: ESP32-S3 monitors PIR. Green LED is on.
Motion Detected: PIR rising edge, green LED off, start 15s timer.
Listen & Infer: Within 15 s, ESP32-S3 captures audio, runs .tflite model for “yes.”
Outcome:
“Yes” recognized, green LED on, send YES to Mega.
Timeout or other, red LED on (and buzzer), send TIMEOUT to Mega.
Reset: After indication, system returns to idle.

Goals
Embed and run a tiny (< 20 KB) TensorFlow Lite model on ESP32-S3

Use ESP-IDF for camera/mic input and model inference

Implement communication with Arduino Mega

Integrate simple motion-triggered logic and LED/buzzer outputs

Implement a notification on owner's phone when denied access/motion.

