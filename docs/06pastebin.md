---
layout: default
title: Final badUSB preparation
nav_order: 7
---
# Final badUSB preparation

For those of you who wondered what the difference was between the 2 scripts on the last page: we are preparing our code to have it transfered to our badUSB. If we want to make everything work, we will need to add our logindata as well, because without it, Pastebin won't accept our information. You might want to think about the consequences of this while doing the next steps!

 ![Attiny85](../images/badusb.png "Image of a badUSB")

We will program our code from new-pastebin5.ps1 using the ducky script, which in turn  generates the more difficult arduino code for us. Check the "Duckify your code" page if you forgot what you did before 😉
1. Go to the online code generator.
2. Convert powershell to ducky script
3. Convert from duckyscript to arduino
4. Upload it and observe your results

> Yes this will probably take some attempts to get it right.

## Some tips
- If your commands fail: maybe your strings are too big. Make them smaller or create bigger delays.
- A semi-colon is a way to execute multiple commands on one line, but perhaps you'll have to split commands up again.
- Check the Duckify docs to make your code cleaner, there's an easier way to create delays.
