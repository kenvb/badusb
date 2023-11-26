---
layout: default
title: Verification
nav_order: 3
---
# Verification
To verify everything is setup correctly and that our little Attiny85 Arduino is working, we'll create 2  little sketches and run their code.

## Blink code

This sketch makes the led on your Arduino blink.

Copy paste the code below and upload it to your Attiny85. 

```arduino
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
![Code being copy pasted in the IDE](../images/uploadcode.png)

Keep in mind that you have to replug your Attiny85 whenever you upload new code. You can do this as soon as you see the text below appear.

![Plug in the device information message](../images/pluginthedevice.png)

Replugging the Attiny85 after uploading the code shouldn't be needed, but for some of the next exercises it's advisable if you don't see the expected results. As this devices emulates a keyboard, if the user of the computer is doing other things at the same time, it might jumble up the keystrokes your computer registers. Don't be afraid to wait a couple of seconds!

## Hello World
This sketch will just start typing out "Hello world" wherever your cursor is, if it's in a location where it can type of course (notepad, search bar of your browser, ...)

Copy paste the code below
```arduino
//#define LAYOUT_FRENCH_BELGIAN
#include <DigiKeyboard.h>
void setup() {
  DigiKeyboard.delay(5000);
  // Will start printing wherever your keyboard cursor is located.
  DigiKeyboard.print("Hello World");
}
void loop() {
  // Nothing here
}
```

![Code being copy pasted in the IDE](../images/codehelloworld.png)

### Keyboard Layout

Azerty users will probably notice that "Hello World" is typed as "Hello Zorld". By removing the double slashes in front of ```#define LAYOUT_FRENCH_BELGIAN```, you can tell it to use the Azerty layout.

Arduino uses a Qwerty layout by default and we need to tell it explicitely if we want to use another one. Digispark has a Keyboard Layout Library with different layouts. If you want to find out which ones are available: you can look these up by loading in the keyboards sketch under "examples"

![Go to examples under file](../images/keyboardlayout1.png)

Feel free to toy around with this built in example to test out Keyboard Layouts

![A list of the keyboard layouts available in the Digispark package](../images/keyboardlayout2.png)
