# Engineering-Workplace-Optimizer
An Arduino based IoT system which was created to optimize cognitive skills by monitoring environmental health (Through the DHT11) and managing workflow using the Pomodoro Method.

System Hardware: MicroController: Arduino Uno 
Display: 16 x 2 LCD 
Sensors: DHT11 

1. Verified analog contrast control using a square trimmer potentiometer which can adjust brightness of text.
2. Setting up Data connection using LCD display
Successfully implemented a 4-bit parallel data bus between the Arduino and the LCD.
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  lcd.begin(16, 2);
  lcd.setCursor(0, 0);
  lcd.print("MONITOR V1.0");
  lcd.setCursor(0, 1);
  lcd.print("RDY");
}

void loop() {
} 
3. Environmental Monitroing System 
Integrated a DHT11 sensor to provide real-time environmental data acquisition. 
#include <LiquidCrystal.h>
#include <DHT.h>

#define DHTPIN 6
#define DHTTYPE DHT11

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
DHT dht(DHTPIN, DHTTYPE);

void setup() {
  lcd.begin(16, 2);
  dht.begin();
  lcd.setCursor(0, 0);
  lcd.print("MONITOR V2.0");
}

void loop() {
  float t = dht.readTemperature();

  lcd.setCursor(0, 1);
  if (isnan(t)) {
    lcd.print("SENSOR ERR");
  } else {
    lcd.print("TEMP: ");
    lcd.print(t);
    lcd.print(" C");
  }
  
  delay(2000); 
} 
4. Added a Pomodoro focus-timer to mitigate cognitive fatigue 
#include <LiquidCrystal.h>
#include <DHT.h>

#define DHTPIN 6
#define DHTTYPE DHT11
#define BTN 7
#define RED 8
#define GREEN 9

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
DHT dht(DHTPIN, DHTTYPE);

int timeLeft = 1500; // 25 minutes in seconds
bool running = false;

void setup() {
  lcd.begin(16, 2);
  dht.begin();
  pinMode(BTN, INPUT_PULLUP);
  pinMode(RED, OUTPUT);
  pinMode(GREEN, OUTPUT);
}

void loop() {
  float t = dht.readTemperature();
  
  if (digitalRead(BTN) == LOW) {
    running = !running;
    delay(200); // Debounce
  }

  lcd.setCursor(0, 0);
  lcd.print("TEMP: ");
  lcd.print(t);
  lcd.print("C  ");

  lcd.setCursor(0, 1);
  if (running) {
    digitalWrite(RED, HIGH);
    digitalWrite(GREEN, LOW);
    
    int mins = timeLeft / 60;
    int secs = timeLeft % 60;
    
    lcd.print("FOCUS: ");
    lcd.print(mins);
    lcd.print(":");
    if (secs < 10) lcd.print("0");
    lcd.print(secs);
    
    delay(1000);
    timeLeft--;
  } else {
    digitalWrite(RED, LOW);
    digitalWrite(GREEN, HIGH);
    lcd.print("STATUS: IDLE   ");
  }



How I made this: This system is built around an Arduino Uno which acts as the central controller for two distinct modules, environmental awareness and workflow management. I used a DHT11 sensor to pull live temperature data, which is then processed and sent to a 16x2 LCD display. To manage the workflow, I programmed a machine logic to switches from 'Idle' to 'Focus' via an push button trigger. When activated, the system initaties a countdown timer and switches a set of visual LED indicators (red for focus and yellow for rest). This system provides an easy to comprehend dashboard which keeps users aware of both their environment and how they are managing their time. 

Why I made this: I noticed that my focus when working on tasks usually fluctuates depending on my working environment. Heat, humidity, and poor time management seemed to drain my energy during long work sessions. I wanted to build a tool that didn't just tell time, but constantly monitored the ergonomics of my workspace. Since I used environmental data to structure work and rest loops, I aimed to create a system that reminds the user to stay productive while remaining aware of the physical conditions that might be causing cognitive fatigue. For me, this project was a first step into exploring how engineering can be used to optimize workplace ergonomics.  
