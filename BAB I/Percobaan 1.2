#include <Servo.h>

const int ldrPin = A0;       
const int potPin = A1;       
const int enaPin = 6;       
const int in1Pin = 7;        
const int in2Pin = 8;         
const int servoPin = 3;     

const int LIGHT_THRESHOLD = 500;  
const int MIN_FAN_SPEED = 80;    
const int DAY_FAN_SPEED = 100;    
const int RACK_EXTENDED = 90;    
const int RACK_RETRACTED = 0;     

bool isDayTime = false;
bool lastDayState = false;
Servo rackServo;

void setup() {
  pinMode(ldrPin, INPUT);
  pinMode(potPin, INPUT);
  pinMode(enaPin, OUTPUT);
  pinMode(in1Pin, OUTPUT);
  pinMode(in2Pin, OUTPUT);
  
  rackServo.attach(servoPin);
  rackServo.write(RACK_RETRACTED);
  
  stopFan();
  
  Serial.begin(9600);
  Serial.println("================ Sistem Pengering Pakaian ================");
  Serial.println("Siang: Rak diperpanjang ke matahari, kipas pelan");
  Serial.println("Night: Rak ditarik kembali, kecepatan kipas dapat diatur");
  Serial.println("====================================================");
  delay(1000);
}

void loop() {
  int lightLevel = analogRead(ldrPin);
  int speedControl = analogRead(potPin);
  
  isDayTime = (lightLevel > LIGHT_THRESHOLD);
  
  if (isDayTime != lastDayState) {
    handleModeChange();
    lastDayState = isDayTime;
  }
  
  if (isDayTime) {
    dayMode();
  } else {
    nightMode(speedControl);
  }
  
  printDryingStatus(lightLevel, speedControl);
  
  delay(100);
}

void handleModeChange() {
  if (isDayTime) {
    Serial.println("*** SWITCHING KE MODE SIANG ***");
    Serial.println("    - Memperpanjang rak baju ke sinar matahari");
    Serial.println("    - Mengaktivasikan sirkulasi kipas yang pelan");
    
    smoothServoMove(RACK_EXTENDED);
    
  } else {
    Serial.println("*** SWITCHING KE MODE MALAM ***");
    Serial.println("    - Menarik kembali rak baju dari luar");
    Serial.println("    - Kecepatan kipas dapat diatur dengan potensiometer");
    
    smoothServoMove(RACK_RETRACTED);
  }
}

void dayMode() {
  runFanForward(DAY_FAN_SPEED);
}

void nightMode(int speedControl) {
  int fanSpeed = map(speedControl, 0, 1023, MIN_FAN_SPEED, 255);
  runFanForward(fanSpeed);
}

void smoothServoMove(int targetPosition) {
  int currentPos = rackServo.read();
  int step = (targetPosition > currentPos) ? 2 : -2;
  
  while (abs(currentPos - targetPosition) > 1) {
    currentPos += step;
    if ((step > 0 && currentPos > targetPosition) || (step < 0 && currentPos < targetPosition)) {
      currentPos = targetPosition;
    }
    rackServo.write(currentPos);
    delay(20); // Smooth movement
  }
}

void runFanForward(int speed) {
  digitalWrite(in1Pin, HIGH);
  digitalWrite(in2Pin, LOW);
  analogWrite(enaPin, speed);
}

void stopFan() {
  digitalWrite(in1Pin, LOW);
  digitalWrite(in2Pin, LOW);
  analogWrite(enaPin, 0);
}

void printDryingStatus(int light, int pot) {
  Serial.print("[");
  Serial.print(isDayTime ? "SIANG" : "MALAM");
  Serial.print("] Cahaya: ");
  Serial.print(light);
  Serial.print(" | Mode: ");
  Serial.print(isDayTime ? "SOLAR" : "KIPAS");
  Serial.print(" | Rak: ");
  Serial.print(isDayTime ? "TERBUKA" : "TERTUTUP");
  Serial.print(" | Servo: ");
  Serial.print(rackServo.read());
  Serial.print("°");
  Serial.print(" | Potensio: ");
  Serial.print(pot);
  Serial.print(" | Kecepatan Kipas: ");
  
  if (isDayTime) {
    Serial.println(DAY_FAN_SPEED);
  } else {
    int nightFanSpeed = map(pot, 0, 1023, MIN_FAN_SPEED, 255);
    Serial.println(nightFanSpeed);
  }
}
