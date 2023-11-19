---
title: Home
layout: home
nav_order: 1
---
# What is a badUSB?

- A USB device posing as a HID (Human Interface Device)
- Pretends – mostly – to be a keyboard.
- Executes malicious code on unsuspecting users’ computer

Old, but excellent [talk from Black Hat](https://www.youtube.com/watch?v=nuruzFqMgIw)

## What are its limitations?

- Logged in as the user -> limited to the user’s access rights
- Keyboard layout
- Can be easily detected by the observant user

## That being said...

- New exploits are being found every day
- Privileged access escalation has to start somewhere
- Defense in Depth strategy and generally avoiding the use of USB devices is recommended.

# BadUSB lab

In this lab we shall be exfiltrating some data from local files to Pastebin using a Digispark - ATtiny85 USB, a very inexpensive device which will turn into a badUSB for educational purposes.

## Required components
-  Digispark Attiny85
-  The Arduino IDE: https://www.arduino.cc/en/software
-  The Digistump drivers: https://github.com/digistump/DigistumpArduino/releases/download/1.6.7/Digistump.Drivers.zip
