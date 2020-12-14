Setup Windows 10 Pro
====================

> The Surface Pro 4 from eBay came loaded with Windows 10 Pro and an Admin user
> (with no password).

**DO NOT CONNECT TO THE INTERNET until local user accounts created!!**

# Windows shortcuts

- `win`             open menu to search for things ("this pc", "settings", "powershell", etc)
- `win` + `e`       open File Explorer (like Finder in Mac)
- `win` + `r`       open Run dialog (type something like "notepad" or "mspaint")
- `win` + `PrtScn`  save screenshot of everything you can see to a file

# Start Powershell as administrator

Press `win` key; search "powershell", then right-click "Windows Powershell" to
open as an administrator

- click "yes" when prompted "Do you want to allow this app to make changes to
  your device" (first time running as administrator only)

# Create regular user with admin rights from Powershell

```
> $Password = Read-Host -AsSecureString
**************

> New-LocalUser -Name ken -Description "Ken" -Password $Password

Name Enabled Description
---- ------- -----------
ken  True    Ken

> Add-LocalGroupMember -Group "Administrators" -Member ken

> Get-LocalGroupMember -Group "Administrators"

ObjectClass Name                          PrincipalSource
----------- ----                          ---------------
User        DESKTOP-USD47BN\admin         Local
User        DESKTOP-USD47BN\Administrator Local
User        DESKTOP-USD47BN\ken           Local

> exit
```

> See
> <https://techcommunity.microsoft.com/t5/itops-talk-blog/how-to-manage-local-users-and-groups-using-powershell/ba-p/733544>
> for more details.

# Login as new user and set password for default admin users

Note, when you first login, at the "choose privacy settings for your device"
screen, toggle everything to "no" and hit "accept"

```
> $Password = Read-Host -AsSecureString
**************

> $UserAccount = Get-LocalUser -Name "admin"

> $UserAccount | Set-LocalUser -Password $Password

> $UserAccount = Get-LocalUser -Name "Administrator"

> $UserAccount | Set-LocalUser -Password $Password
```

> See
> <https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.localaccounts/set-localuser?view=powershell-5.1>

# Check and modify some settings

Press `win` ken; search "settings" (app)

- scroll to the bottom on left panel to click "about"
- "windows specifications"
    - Windows 10 Pro
    - Version 1909
    - Installed on 3/18/2019
    - OS build 18363.592
- "related settings"
    - click "BitLocker settings"
    - ignore "waiting for activation"
    - click "Turn on BitLocker
    - click "save to a file" for "recovery key" (save to usb stick)

Press `win` ken; search "this pc"

- right-click "manage"

# Connect to internet and update

- run Windows Update and restart several times until it says "system is up to
  date"
- install updated version of Microsoft Edge Browser
- add Duckduckgo extension to Edge

# TODO

**Add sections on setting up Windows Subsystem for Linux (WSL2)**

- <https://docs.microsoft.com/en-us/windows/wsl/install-win10>
- <https://docs.microsoft.com/en-us/windows/wsl/install-manual>
- Then create SSH key and start cli/dev stuff
