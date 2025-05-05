// MegaYesNo.ino

#define GREEN_LED_PIN 3
#define RED_LED_PIN   5
#define BUZZER_PIN    6

void setup() {
  Serial.begin(115200);
  Serial1.begin(115200);  // from ESP32-S3
  pinMode(GREEN_LED_PIN, OUTPUT);
  pinMode(RED_LED_PIN, OUTPUT);
  pinMode(BUZZER_PIN, OUTPUT);
  digitalWrite(GREEN_LED_PIN, LOW);
  digitalWrite(RED_LED_PIN,   LOW);
  digitalWrite(BUZZER_PIN,    LOW);
}

void loop() {
  if (Serial1.available()) {
    String result = Serial1.readStringUntil('\n');
    result.trim();
    Serial.println("ESP3EYE>> " + result);

    // Clear previous state
    digitalWrite(GREEN_LED_PIN, LOW);
    digitalWrite(RED_LED_PIN,   LOW);
    digitalWrite(BUZZER_PIN,    LOW);

    if (result == "YES") {
      Serial.println("Confirmed: YES");
      digitalWrite(GREEN_LED_PIN, HIGH);
    } else {
      Serial.println("No response / Time out");
      digitalWrite(RED_LED_PIN, HIGH);
      digitalWrite(BUZZER_PIN,  HIGH);
    }
  }
}
