---
layout: default
title: How to protect yourself?
nav_order: 8
---
# How not to fall victim to these badUSB devices?

- Don’t accept (weird) usb devices or insert them if you don’t know their origins.
- Use an [USB Condom](https://www.zdnet.com/article/flying-this-weekend-this-6-usb-condom-will-protect-your-data-from-suspicious-outlets/){:target="_blank"} or [USB dust caps](https://www.amazon.com/Usb-Port-Caps/s?k=Usb+Port+Caps){:target="_blank"} or [protector caps](https://www.amazon.com/Blocker-Non-Removable-Protector-Moisture-Information/dp/B0B9MY9KZC?th=1){:target="_blank"}, but these things only really help when you leave your devices unattended for VERY short amounts of time.
- Threathening people with violence when they insert foreign usb devices in your computer is an option but generally frowned upon by HR (yes this is a joke, don’t use violence!)

## but let's assume that one day someone IS able to plug-in a badUSB in your computer..

- Don't keep passwords in txt-files on your pc. Use one of the many password managers out there! (bitwarden, keepass, lastpass, protonpass, ...)
- Only use your admin account for those times you actually need it.
- Multi-factor authentication is absolutely helpful as malicious actors need more than just your password!

# How can we detect badUSB abuse?

- USB forensics is… [special](https://www.youtube.com/watch?v=b4KyGhh75Qc){:target="_blank"} and so we shouldn't always trust its data.
- Sure, there are some [tools](https://www.nirsoft.net/utils/usb_devices_view.html){:target="_blank"} out there.
- More interesting is doing command line [logging](https://docs.splunk.com/Documentation/UBA/5.2.0/GetDataIn/AddPowerShell#:~:text=To%20enable%20module%20logging%3A,on%20Module%20Logging%20to%20enabled.){:target="_blank"} which can be done in [multiple](https://adamtheautomator.com/powershell-logging-2/){:target="_blank"} ways.
-   It might surprise you that windows doesn’t really do that out-of-the-box
- Things like enabling [constrained language mode](https://devblogs.microsoft.com/powershell/powershell-constrained-language-mode/){:target="_blank"} also help

Bottom line: defense in depth is key, always.
