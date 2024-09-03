int gasSensorPin = A0; // Analog pin for gas sensor
int ledPin = 13;       // Digital pin for status LED

void setup() {
  Serial.begin(9600);   // Initialize serial communication
  pinMode(ledPin, OUTPUT); // Set LED pin as output
}

void loop() {
  int sensorValue = analogRead(gasSensorPin); // Read analog value from gas sensor
  Serial.print("Gas Sensor Value: ");
  Serial.println(sensorValue);

  if (sensorValue > 200) {
    digitalWrite(ledPin, HIGH); // Turn on LED if air quality is poor
    Serial.println("Poor air quality detected!");
  } else {
    digitalWrite(ledPin, LOW); // Turn off LED if air quality is good
    Serial.println("Air quality is good.");
  }

  delay(1000); // Delay for readability, adjust as needed
}
