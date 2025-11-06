/*
 SMART DUSTBIN - FULLY COMPATIBLE CODE
 Designed for YOUR exact L293D motor driver pins
 Components: Ultrasonic Sensor, DC Motor, LED, Buzzer
*/

// ==================== 
// PIN DEFINITIONS - MATCHING YOUR EXACT SETUP
// ====================

// Ultrasonic Sensor Pins
const int trigPin = 9;    // Trigger pin connected to Digital Pin 9
const int echoPin = 10;   // Echo pin connected to Digital Pin 10

// L293D Motor Driver Pins (YOUR EXACT PINS)
const int motorInput1 = 7;    // Connected to L293D input1 (pin 2) - Motor control
const int motorInput2 = 6;    // Connected to L293D input2 (pin 6) - Motor control

// Indicator Pins
const int buzzerPin = 12;     // Buzzer connected to Digital Pin 12
const int ledPin = 11;        // LED connected to Digital Pin 11 (with 220Ω resistor)

// Dustbin Settings
const int activationDistance = 30;  // Dustbin activates when object within 30cm
const int openDuration = 3000;      // Keep dustbin open for 3 seconds (3000ms)

// Variables for sensor readings
long duration;    // Stores ultrasonic pulse duration
int distance;     // Stores calculated distance in cm

// ==================== 
// SETUP FUNCTION - RUNS ONCE AT START
// ====================
void setup() {
  // Initialize ultrasonic sensor pins
  pinMode(trigPin, OUTPUT);   // Trigger pin is OUTPUT (sends signal)
  pinMode(echoPin, INPUT);    // Echo pin is INPUT (receives signal)
  
  // Initialize motor control pins
  pinMode(motorInput1, OUTPUT);  // Motor control pin 1
  pinMode(motorInput2, OUTPUT);  // Motor control pin 2
  
  // Initialize indicator pins
  pinMode(ledPin, OUTPUT);       // LED pin
  pinMode(buzzerPin, OUTPUT);    // Buzzer pin
  
  // Ensure motor is STOPPED at startup
  digitalWrite(motorInput1, LOW);
  digitalWrite(motorInput2, LOW);
  
  // Start serial communication for debugging
  Serial.begin(9600);
  Serial.println("Smart Dustbin Started Successfully!");
  Serial.println("Waiting for objects...");
}

// ==================== 
// MAIN LOOP - RUNS REPEATEDLY
// ====================
void loop() {
  // Step 1: Measure distance using ultrasonic sensor
  distance = measureDistance();
  
  // Step 2: Print distance to Serial Monitor for debugging
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
  
  // Step 3: Check if object is within activation range
  if (distance < activationDistance && distance > 0) {
    // Object detected - OPEN the dustbin
    openDustbin();
  } else {
    // No object detected - CLOSE the dustbin
    closeDustbin();
  }
  
  // Small delay before next reading
  delay(100);
}

// ==================== 
// FUNCTION: MEASURE DISTANCE
// ====================
int measureDistance() {
  // Clear the trigger pin
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  
  // Send 10 microsecond pulse to trigger pin
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  // Read the echo pin - returns pulse duration in microseconds
  duration = pulseIn(echoPin, HIGH);
  
  // Calculate distance in cm
  // Speed of sound = 343 m/s = 0.0343 cm/microsecond
  // Divide by 2 because sound travels to object and back
  distance = duration * 0.0343 / 2;
  
  return distance;
}

// ==================== 
// FUNCTION: OPEN DUSTBIN
// ====================
void openDustbin() {
  Serial.println("OBJECT DETECTED - Opening dustbin...");
  
  // Activate motor to OPEN dustbin lid
  // Motor spins in one direction (HIGH-LOW pattern)
  digitalWrite(motorInput1, HIGH);
  digitalWrite(motorInput2, LOW);
  
  // Turn on visual indicator (LED)
  digitalWrite(ledPin, HIGH);
  
  // Activate audible indicator (Buzzer)
  tone(buzzerPin, 1000);  // 1000Hz tone
  
  // Keep dustbin open for specified duration
  delay(openDuration);
  
  // Stop motor but keep indicators on
  digitalWrite(motorInput1, LOW);
  digitalWrite(motorInput2, LOW);
  
  Serial.println("Dustbin is OPEN");
}

// ==================== 
// FUNCTION: CLOSE DUSTBIN  
// ====================
void closeDustbin() {
  // Ensure motor is STOPPED
  digitalWrite(motorInput1, LOW);
  digitalWrite(motorInput2, LOW);
  
  // Turn off visual indicator
  digitalWrite(ledPin, LOW);
  
  // Turn off audible indicator
  noTone(buzzerPin);
  
  // Optional: Uncomment line below for debugging
  // Serial.println("Dustbin is CLOSED");
}

/*
CONNECTION SUMMARY FOR YOUR REFERENCE:

ULTRASONIC SENSOR:
- VCC  → 5V
- GND → GND  
- Trig → Digital Pin 9
- Echo → Digital Pin 10

L293D MOTOR DRIVER (YOUR PINS):
- power1 (pin 1) → 5V
- power2 (pin 8) → 5V
- enable1&2 (pin 7) → 5V
- input1 (pin 2) → Arduino Digital Pin 7
- input2 (pin 6) → Arduino Digital Pin 6
- output1 (pin 3) → DC Motor Wire 1
- output2 (pin 5) → DC Motor Wire 2
- All ground pins → GND

INDICATORS:
- LED → Digital Pin 11 (with 220Ω resistor to GND)
- Buzzer → Digital Pin 12 to GND
*/
