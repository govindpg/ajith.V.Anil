
int led = 13;
int red= 12;
int green = 11;  
int sensor = 2; 
int smoke = A0;
int buzzer = 9;
int state = LOW;
int val = 0;
int tres =400; 
void setup() {
pinMode(led, OUTPUT);    pinMode(sensor, INPUT);
pinMode(smoke, INPUT);
pinMode(red, OUTPUT);
pinMode(green, OUTPUT);
pinMode(buzzer, OUTPUT);
    Serial.begin(9600); 
    } 
void loop(){ 
    int analogSensor=
    analogRead(smoke);
    Serial.print("Pin A0: ");
  Serial.println(analogSensor);
    val = digitalRead(sensor);
    if (val == HIGH) { 
        digitalWrite(led, HIGH);         delay(100); 
         if (state == LOW) 
        { 
  Serial.println("Motion detected!"); 
            state = HIGH; 
             }
         } 
    else { digitalWrite(led, LOW);
        delay(200); 
        if (state == HIGH){ Serial.println("Motion stopped!"); state = LOW; 
            }
      if (analogSensor > tres)
  {
    digitalWrite(red, HIGH);
    digitalWrite(green, LOW);
    tone(buzzer, 1000, 200);
  }
  else
  {
    digitalWrite(red, LOW);
    digitalWrite(green, HIGH);
    noTone(buzzer);
  }
  delay(100); 
             }
         }
