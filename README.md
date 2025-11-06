01. EKALALE LOKAALE BSCCS/2025/30137
2. SUMAYA BIGENIMANA BSCCS/2025/32262
3. THIJIEN CHIKOT BSCCS/2025/30142
4. DENG MAKUCH BSCCS/2025/69596
5. SAVAN JOSEPH BSCCS/2025/30679
6. MAYEN LUAL BSCCS/2025/67976
7. PATRICK MUGABO NZABAKIZA BSCCS/2025/31135
8. PIOL DENG BSCCS/2025/69731
9. JARED KEMBOI BSCCS/2025/60850
10. MOHAMED HAJI BSCCS/2025/68435





PROJECT REPORT: SMART DUSTBIN SYSTEM

1. Introduction
This project involves designing and simulating an automated smart dustbin system using TinkerCAD.The system automatically opens when an object is detected within 30cm and closes after 3 seconds, providing hands-free operation.

2. Components Used

· Arduino Uno R3 (Microcontroller)
· HC-SR04 Ultrasonic Sensor (Distance detection)
· L293D Motor Driver (Motor control)
· DC Motor (Lid mechanism)
· LED (Visual indicator)
· 220Ω Resistor (Current limiting)
· Buzzer (Audible alert)
· Breadboard (Circuit assembly)
· Jumper Wires (Connections)

3. Circuit Connections

3.1 Power Connections

· Arduino 5V → Breadboard positive rail
· Arduino GND → Breadboard negative rail

3.2 Component Wiring

· Ultrasonic Sensor: VCC→5V, GND→GND, Trig→Pin 9, Echo→Pin 10
· L293D Motor Driver: power1→5V, power2→5V, enable1&2→5V, input1→Pin 7, input2→Pin 6, output1→Motor Wire1, output2→Motor Wire2, all ground pins→GND
· LED: Anode→Pin 11 with 220Ω resistor, Cathode→GND
· Buzzer: Positive→Pin 12, Negative→GND

4. Working Principle
The ultrasonic sensor continuously measures distance to nearby objects.When an object is detected within 30cm, the system:

· Activates the DC motor to open the dustbin lid
· Turns on the LED for visual indication
· Sounds the buzzer for audible feedback
· Maintains this state for 3 seconds before automatically closing

5. Key Features

· Automatic hands-free operation
· Visual and audible user feedback
· Adjustable detection range (30cm)
· Configurable open duration (3 seconds)
· Safe motor control using L293D driver

6. Applications

· Home automation systems
· Public sanitation facilities
· Healthcare environments
· Smart city infrastructure

7. Conclusion
The smart dustbin system was successfully designed and simulated in TinkerCAD.The prototype demonstrates effective automated operation using ultrasonic sensing and motor control, providing a practical solution for hygienic waste disposal. Future enhancements could include weight sensors, fill-level monitoring, and wireless connectivity.

Submitted by: [Your Name]
Date:[Current Date]
