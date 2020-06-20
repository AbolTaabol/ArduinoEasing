/* # Simple easing lighting library for Arduino

Types of easing:
  - Linear
	- Quadratic
	- Cubic

- Arduino inaccesible when the code is running. 

To-do:
- Migrate to millis(), RTC
- Add ability to choose time duration only.
- Change PWM resolution. 
- Add interrupt.
*/

/*
* Easing functions based on Robert Penner's work,
* for more info see Easing.h or Easing.cpp
*/

#include <Easing.h>

int ledPin = 6; //LED on pin 6 (You can replace it with any PWM pin);
int dur=255; //Steps you want. Defined the maximum PWM value which is usually 0-255
int delay_time=15; //Total time is dur * delay_time

void setup(){

  pinMode(ledPin, OUTPUT);

}

void loop(){
  
  for (int pos=0; pos<dur; pos++){
   analogWrite(ledPin, (Easing::easeInOutCubic(pos, dur)));
   delay(delay_time); //wait for the led to light up
  }

  delay(1000);

  for (int pos=dur; pos>0; pos++){
    analogWrite(ledPin,(Easing::easeInOutCubic(pos, dur)));
    delay(delay_time); //wait for the led to light up
  }
  
  delay(1000);
}

