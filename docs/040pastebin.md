---
layout: default
parent: Pastebin
title: Setup Pastebin
nav_order: 1
---
# Pastebin
[Famous website](https://pastebin.com/){:target="_blank"} for “easy copy and paste”
- It's used by a lot of malicious hackers in a lot of [data exfiltration situations](https://attack.mitre.org/techniques/T1567/003/){:target="_blank"} in companies.
- Obviously, many opensource equivalents exist, so an actual hacker can host their own version of Pastebin.

For our workshop, we will just use a free version right now.

Go to [pastebin](https://pastebin.com/){:target="_blank"} and create a free account.

## Get your API-key
On pastebin.com go to the API tab

Find your developer API Key, Never share this with anyone!

![Pastebin developer API Key](../images/developerapikey.png)


Create a new file named logindata.ps1 file with the code below  and copy paste your dev key into that file.

```powershell
$DevKey     =   "PUT-DEVKEY-HERE"
$UserKey    =   "PUT-USER-KEY-HERE"
```
You don't have a UserKey yet.
