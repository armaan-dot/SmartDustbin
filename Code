#include <Servo.h>

const int trigPin = 9;      // Ultrasonic sensor trigger pin
const int echoPin = 10;     // Ultrasonic sensor echo pin
const int servoPin = 6;     // Servo motor control pin


Servo myServo;
long duration; //variables 
int distance; //variables 

const int openDistance = 45;  // Distance threshold in cm to open the lid
const int openAngle = 90;     // Servo angle to open lid
const int closeAngle = 0;     // Servo angle to close lid

void setup() {
  Serial.begin(9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  
  myServo.attach(servoPin);
  myServo.write(closeAngle);  // Start with lid closed
}

void loop() {
  // Clear the trigPin by setting it LOW:
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  
  // Trigger the sensor by setting the trigPin HIGH for 10 microseconds:
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  // Read the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echoPin, HIGH);
  
  // Calculate the distance:
  distance = duration * 0.0347 / 2; //using echo distance
  
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
  
  // Check if distance is less than threshold to open the lid
  if (distance > 0 && distance <= openDistance) {
    myServo.write(openAngle);  // Open the lid
  } else {
    myServo.write(closeAngle); // Close the lid
  }
  
  delay(200); // Small delay for stability
}

