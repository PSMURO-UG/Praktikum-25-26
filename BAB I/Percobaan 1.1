#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(..., 20, 4);

const int buttonPin = 2;
const int potPin = A0;
const int redPin = 9;
const int greenPin = 10;
const int bluePin = 11;

#define PRESET_MODE 0
#define ADJUST_MODE 1
byte currentMode = PRESET_MODE;

byte colorState = 0;
byte colorChannel = 0;
int redVal = 0, greenVal = 0, blueVal = 0;

bool buttonPressed = false;
unsigned long lastPressTime = 0;
const int debounceTime = 50;
const int longPressTime = 1000;

struct PresetColor {
  int r, g, b;
  String name;
};

PresetColor presetColors[7] = {
  {255, 0, 0, "Red"},
  {255, 150, 0, "Yellow"},
  {0, 255, 0, "Green"},
  {0, 255, 255, "Cyan"},
  {0, 0, 255, "Blue"},
  {200, 0, 200, "Magenta"},
  {255, 255, 255, "White"}
};

void setup() {
  pinMode(buttonPin, INPUT_PULLUP);
  pinMode(redPin, OUTPUT);
  pinMode(greenPin, OUTPUT);
  pinMode(bluePin, OUTPUT);
  
  lcd.begin(20, 4);
  lcd.backlight();

  Serial.begin(9600);

  lcd.setCursor(0, 0);
  lcd.print("RGB Controller v2.0");
  lcd.setCursor(0, 1);
  lcd.print("Dual Mode System");
  lcd.setCursor(0, 2);
  lcd.print("Short: Cycle");
  lcd.setCursor(0, 3);
  lcd.print("Long: Mode Switch");

  Serial.println("============================");
  Serial.println("RGB Controller v2.0 Started");
  Serial.println("============================");
  Serial.println("Modes Available:");
  Serial.println("1. Preset Mode - 7 Colors");
  Serial.println("2. Adjust Mode - Custom RGB");
  Serial.println("Short Press: Cycle Colors/Channels");
  Serial.println("Long Press: Switch Modes");
  Serial.println("============================");
  
  delay(2000);
  lcd.clear();
}

void loop() {
  int potValue = analogRead(potPin);
  int buttonState = digitalRead(buttonPin);

  if (buttonState == LOW) {
    if (!buttonPressed) {
      buttonPressed = true;
      lastPressTime = millis();
    }
    else if (millis() - lastPressTime > longPressTime) {
      currentMode = !currentMode;
      lcd.clear();

      Serial.println("*** MODE CHANGED ***");
      if (currentMode == PRESET_MODE) {
        Serial.println("Switched to: PRESET MODE");
        Serial.println("7 preset colors available");
      } else {
        Serial.println("Switched to: ADJUST MODE");
        Serial.println("Custom RGB adjustment");
      }
      Serial.println("********************");
      
      while(digitalRead(buttonPin) == LOW);
      delay(debounceTime);
      buttonPressed = false;
      return;
    }
  }
  else if (buttonPressed) {
    if (currentMode == PRESET_MODE) {
      colorState = (colorState + 1) % 7;
      Serial.print("Preset Color Changed to: ");
      Serial.println(presetColors[colorState].name);
    } 
    else {
      colorChannel = (colorChannel + 1) % 3;
      String channels[] = {"RED", "GREEN", "BLUE"};
      Serial.print("Adjusting Channel: ");
      Serial.println(channels[colorChannel]);
    }
    buttonPressed = false;
    delay(debounceTime);
  }
  
  // Update display and LEDs based on current mode
  if (currentMode == PRESET_MODE) {
    updatePresetMode(potValue);
  } 
  else {
    updateAdjustMode(potValue);
  }
  
  delay(100);
}

void updatePresetMode(int potValue) {
  PresetColor current = presetColors[colorState];
  setColor(current.r, current.g, current.b);
  
  lcd.setCursor(0, 0);
  lcd.print("Mode: Preset        ");
  
  lcd.setCursor(0, 1);
  lcd.print("Color: ");
  lcd.print(current.name);
  lcd.print("           ");
  
  lcd.setCursor(0, 2);
  lcd.print("RGB: ");
  lcd.print(current.r);
  lcd.print(",");
  lcd.print(current.g);
  lcd.print(",");
  lcd.print(current.b);
  lcd.print("       ");
  
  lcd.setCursor(0, 3);
  lcd.print("Pot: ");
  lcd.print(potValue);
  lcd.print("            ");
  
  Serial.print("PRESET | Color: ");
  Serial.print(current.name);
  Serial.print(" | RGB(");
  Serial.print(current.r);
  Serial.print(",");
  Serial.print(current.g);
  Serial.print(",");
  Serial.print(current.b);
  Serial.print(") | Pot: ");
  Serial.println(potValue);
}

void updateAdjustMode(int potValue) {
  int val = map(potValue, 0, 1023, 0, 255);
  
  switch (colorChannel) {
    case 0: redVal = val; break;
    case 1: greenVal = val; break;
    case 2: blueVal = val; break;
  }
  
  setColor(redVal, greenVal, blueVal);
  
  lcd.setCursor(0, 0);
  lcd.print("Mode: Adjust        ");
  
  lcd.setCursor(0, 1);
  lcd.print("Adjusting: ");
  String channels[] = {"Red  ", "Green", "Blue "};
  lcd.print(channels[colorChannel]);
  lcd.print("    ");
  
  lcd.setCursor(0, 2);
  lcd.print("R:");
  if (redVal < 100) lcd.print(" ");
  if (redVal < 10) lcd.print(" ");
  lcd.print(redVal);
  lcd.print(" G:");
  if (greenVal < 100) lcd.print(" ");
  if (greenVal < 10) lcd.print(" ");
  lcd.print(greenVal);
  lcd.print(" B:");
  if (blueVal < 100) lcd.print(" ");
  if (blueVal < 10) lcd.print(" ");
  lcd.print(blueVal);
  
  lcd.setCursor(0, 3);
  lcd.print("Pot: ");
  lcd.print(potValue);
  lcd.print(" Val: ");
  lcd.print(val);
  lcd.print("     ");
  
  Serial.print("ADJUST | Channel: ");
  Serial.print(channels[colorChannel]);
  Serial.print(" | RGB(");
  Serial.print(redVal);
  Serial.print(",");
  Serial.print(greenVal);
  Serial.print(",");
  Serial.print(blueVal);
  Serial.print(") | Pot: ");
  Serial.print(potValue);
  Serial.print(" -> ");
  Serial.println(val);
}

void setColor(int r, int g, int b) {
  analogWrite(redPin, r);
  analogWrite(greenPin, g);
  analogWrite(bluePin, b);
}
