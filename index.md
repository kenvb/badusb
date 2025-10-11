---
title: Home
layout: home
nav_order: 1
---
# BadUSB
Visit the Github pages version [here](https://kenvb.github.io/badusb/) (in case you're looking at the actual github code)
If you do want to look at the code behind, check out the [github repository](https://github.com/kenvb/badusb){:target="_blank"}
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

In this workshop we shall be exfiltrating some data from local files on a Windows machine to [Pastebin](https://pastebin.com/){:target="_blank"} or [github](https://github.com/){:target="_blank"}using a Digispark - ATtiny85 USB, a very inexpensive device which we will turn into a badUSB for educational purposes. Just follow the instructions on the following pages.

Remark: I added Github as an alternative because Pastebin, sadly, has some rate limiting going on when several students are poking the API. Limitations of the free version I guess.

 ![Attiny85](../badusb/images/attiny85.png "Image of an Attiny85")

## Required components
-  Digispark Attiny85 (cost: 2.5 - 6 euro. Bulk makes it cheaper)
-  The [Arduino IDE](https://www.arduino.cc/en/software){:target="_blank"}
-  The [Digistump drivers](https://github.com/digistump/DigistumpArduino/releases/download/1.6.7/Digistump.Drivers.zip){:target="_blank"}
-  A Windows 10/11 client or Virtual Machine where you have (local) admin rights

## Target audience
This workshop is aimed at everyone who wants to learn more about security or who wants to use this in some sort of security awareness workshop. Ideally the target audience:
- Has some **basic** scripting / coding experience (powershell or bash or python or ...).
- Isn't afraid of the terminal (basic usage like dir, cd and knows how to elevate to admin).
- Knows how to use a virtual machine in virtualbox or vmware, ... (if your computer is locked down by admins).
