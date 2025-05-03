# ESP32s3-eye-Security
A low-cost, hands-on security “toy” built around the ESP32-S3 Eye and Arduino Mega 2560. When motion is detected, a 15-second timer starts and the system listens for the spoken command “yes”. If the model (kept under 20 KB for microcontroller constraints) recognizes “yes” in time, it lights a green LED; otherwise it switches on a red LED.
