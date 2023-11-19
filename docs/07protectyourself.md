---
layout: default
title: How to protect yourself?
nav_order: 7
---
# How not to fall victim to these badUSB devices?

- Don’t accept (weird) usb devices or insert them if you don’t know their origins.
- Use an [USB Condom](https://www.zdnet.com/article/flying-this-weekend-this-6-usb-condom-will-protect-your-data-from-suspicious-outlets/)
- [USB dust caps](https://www.amazon.com/Usb-Port-Caps/s?k=Usb+Port+Caps) or [protector caps](https://www.amazon.com/Blocker-Non-Removable-Protector-Moisture-Information/dp/B0B9MY9KZC?th=1) also do the trick, but only when your devices are unattended for very short periods.
- Threathening people with violence when they insert foreign usb devices in your computer is an option but generally frowned upon by HR (yes this is a joke, don’t use violence!)

# How can we detect badUSB abuse?

- USB forensics is… [special](https://www.youtube.com/watch?v=b4KyGhh75Qc).
- Sure, there are some [tools](https://www.nirsoft.net/utils/usb_devices_view.html) out there.
- More interesting is doing command line [logging](https://docs.splunk.com/Documentation/UBA/5.2.0/GetDataIn/AddPowerShell#:~:text=To%20enable%20module%20logging%3A,on%20Module%20Logging%20to%20enabled.) which can be done in [multiple](https://adamtheautomator.com/powershell-logging-2/) ways.
-   It might surprise you that windows doesn’t really do that out-of-the-box
- Things like enabling [constrained language mode](https://devblogs.microsoft.com/powershell/powershell-constrained-language-mode/) also help

Bottom line: defense in depth is key, always.
