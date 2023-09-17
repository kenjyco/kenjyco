Setup Windows 10 Pro
====================

> The Surface Pro 4 from eBay came loaded with Windows 10 Pro and an Admin user
> (with no password).

**DO NOT CONNECT TO THE INTERNET until local user accounts created!!**

# Windows shortcuts

- `win`                     open menu to search for things ("this pc", "settings", "powershell")
- `win` + `e`               open File Explorer (like Finder in Mac)
- `win` + `r`               open Run dialog (type something like "notepad" or "mspaint")
- `win` + `l`               lock screen
- `win` + `g`               toggle "game bar" visibility
- `win` + `PrtScn`          save screenshot of everything you can see to a file
- `win` + `Shift` + `s`     copy screenshot of selected area to clipboard
- `Alt` + `PrtScr`          copy screenshot of current window to clipboard
- `Ctrl` + `Shift` + `Esc`  open Task Manager (to check CPU/Memory/Disk/Network usage)

# Start Powershell as administrator

Press `win` key; search "powershell", then right-click "Windows Powershell" to
run as an administrator

- click "yes" when prompted "Do you want to allow this app to make changes to
  your device" (first time running as administrator only)

# Create regular user with admin rights from Powershell

> Each leading `>` below represents a Powershell prompt, which is waiting for
> you to type (paste) commands. Do not copy the prompt character (`>`) and do
> not copy the output lines below the commands.

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

Press `win` key; search "settings" (app) and open

- click the "System" button on the upper left
- scroll to the bottom on left panel to click "about"
- "windows specifications"
    - **Edition** Windows 10 Pro
    - **Version** 20H2
    - **Installed on** 7/2/2021
    - **OS build** 19042.1110
    - **Experience** Windows Feature Experience Pack 120.2212.3530.0
- "related settings"
    - click "BitLocker settings"
    - ignore "waiting for activation"
    - click "Turn on BitLocker
    - click "save to a file" for "recovery key" (save to usb stick)

Press `win` key; search "this pc"

- right-click "manage"

# Connect to internet and update

- run Windows Update and restart several times until it says "system is up to
  date"
- install updated version of Microsoft Edge Browser
- add Duckduckgo extension to Edge

# Disable password expiration for your local user

- Press `Win` + `r` (to pull up "Run") and open `lusrmgr.msc`
- In the "Local Users and Groups" window that opens, click "Users" on the left
- Right-click your user and select "Properties"
- Check the "Password never expires" box and click "Apply"
- Close the pop-up and the "Local Users and Groups" window

# Enable God Mode

> See <https://www.tomsguide.com/how-to/how-to-enable-god-mode-in-windows>

# Install WSL 2 (Windows Subsystem for Linux)

> It's recommended to run Windows Update to get the latest version of Windows
> before attempting these steps.

### If you have Windows 10 version 2004 and higher

.

# Install Git BASH

Visit <https://github.com/git-for-windows/git/releases/latest>, download the
`Git-{version}-64-bit.exe` file, then run the installer.

**Git BASH** provides a
[bash](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) emulation to run Git
from the command-line that behaves the same as the `git` command in Linux/Mac.
See <https://gitforwindows.org>

# TODO

**Add sections on setting up Windows Subsystem for Linux (WSL 2)**

- <https://docs.microsoft.com/en-us/windows/wsl/install-win10>
- <https://docs.microsoft.com/en-us/windows/wsl/install-manual>
- Then create SSH key and start cli/dev stuff
- <https://docs.docker.com/docker-for-windows/install>
    - Seems as though newer versions of Docker Desktop for Windows works with
      Windows 10 Home now (thanks to WSL 2 backend)
      <https://docs.docker.com/docker-for-windows/wsl>
    - <https://docs.docker.com/docker-for-windows/docker-toolbox> Docker Toolbox
      is now depricated (yay) and there are instructions to migrate to Docker
      Desktop and uninstall uninstall Docker Toolbox
- Then make sure `kind` (for kubernetes) can be installed
  <https://kind.sigs.k8s.io/docs/user/using-wsl2>
- Also checkout chocolatey (like homebrew, but for windows)
  <https://chocolatey.org/install>
