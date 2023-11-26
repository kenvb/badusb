---
title: Home
layout: home
nav_order: 1
---
# BadUSB
Visit the Github pages version [here](https://kenvb.github.io/badusb/) (in case you're looking at the actual github code)
## What is a badUSB?

- A USB device posing as a HID (Human Interface Device)
- Pretends – mostly – to be a keyboard.
- Executes malicious code on unsuspecting users’ computer

Old, but excellent [talk from Black Hat](https://www.youtube.com/watch?v=nuruzFqMgIw){:target="_blank"}

## What are its limitations?

- Logged in as the user -> limited to the user’s access rights
- Keyboard layout
- Can easily be detected by the observant user

## That being said...

- New exploits are being found every day
- Privileged access escalation has to start somewhere
- Defense in Depth strategy and generally avoiding the use of USB devices is recommended.

# BadUSB workshop

In this workshop we shall be exfiltrating some data from local files on a Windows machine to Pastebin using a Digispark - ATtiny85 USB, a very inexpensive device which will turn into a badUSB for educational purposes. Just follow the instructions on the following pages.

## Required components
-  Digispark Attiny85 (cost: 2.5 - 6 euro. Bulk makes it cheaper)
-  The [Arduino IDE](https://www.arduino.cc/en/software){:target="_blank"}
-  The [Digistump drivers](https://github.com/digistump/DigistumpArduino/releases/download/1.6.7/Digistump.Drivers.zip){:target="_blank"}
-  A Windows 10/11 client or Virtual Machine where you have (local) admin rights
