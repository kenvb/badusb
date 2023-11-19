---
layout: default
title: Verification
nav_order: 3
---
# Verification
To verify everything is setup correctly and that our little Attiny85 Arduino is working, we'll create 2  little sketches and run their code.

## Blink code

This sketch makes the led on your Arduino blink.

Copy paste the code below
```
// Original code: https://codebender.cc/sketch:8285#Digispark%20Blink.ino
void setup()
{
	//Set Pins 0 and 1 as outputs.
	//Some Digisparks have a built-in LED on pin 0, while some have it on
	//pin 1. This way, we can all Digisparks.
	pinMode(0, OUTPUT);
	pinMode(1, OUTPUT);
}
void loop()
{
	//Set the LED pins to HIGH. This gives power to the LED and turns it on
	digitalWrite(0, HIGH);
	digitalWrite(1, HIGH);
	//Wait for a second
	delay(1000);
	//Set the LED pins to LOW. This turns it off
	digitalWrite(0, LOW);
	digitalWrite(1, LOW);
	//Wait for a second
	delay(1000);
}
```
## Hello World
This sketch will just start typing out "Hello world" wherever your cursor is, if it's in a location where it can type of course (notepad, search bar of your browser, ...)

Copy paste the code below
```
//#define LAYOUT_FRENCH_BELGIAN
#include “DigiKeyboard.h”
void setup() {
  DigiKeyboard.delay(5000);
  // Will start printing wherever your keyboard cursor is located.
  DigiKeyboard.print("Hello World");
}
void loop() {
  // Nothing here
}
```
