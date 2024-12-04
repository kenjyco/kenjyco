Upgrade Mac
=========

These are the latest macOS versions:

- macOS 15 Sequoia, September 16, 2024
- macOS 14 Sonoma, September 26, 2023
- **macOS 13 Ventura**, October 25, 2022
- macOS 12 Monterey, October 25, 2021
- macOS 11 Big Sur, November 19, 2020

> See: <https://setapp.com/how-to/full-list-of-all-macos-versions>

As of today (12/3/2024), the [Homebrew](https://brew.sh) package manager
requires macOS 13 Ventura or higher to work properly.

If you have access to a used Mac computer, it is possible to download a
particular version of MacOS to install, thanks to the [OpenCore Legacy
Patcher](https://dortania.github.io/OpenCore-Legacy-Patcher) project. This
includes computers as old as models from 2008 that aren't officially supported
for newer versions of macOS.

> See: <https://dortania.github.io/OpenCore-Legacy-Patcher/INSTALLER.html>

Make sure you're running at least **OS X 10.11 El Capitan** or later. They also
recommend  you update your Mac to its latest native version before using
OpenCore Legacy Patcher to ensure you're on the highest firmware.

If needed, hold down **`command` + `r`** right after turning the computer on to
startup the built-in recovery system.

# Creating a macOS Installer

> <https://dortania.github.io/OpenCore-Legacy-Patcher/INSTALLER.html>
> <https://dortania.github.io/OpenCore-Legacy-Patcher/BUILD.html>

- Grab a 32GB USB drive (which will be wiped to create an installer disk)
- Visit <https://github.com/dortania/OpenCore-Legacy-Patcher/releases> to save
  the latest **OpenCore-Patcher-GUI.app.zip** file
- Unzip and open the app
    - Click the "Create macOS Installer" button
    - Then click the "Download macOS Installer" button
    - Select "macOS Ventura" and click the "Download" button
- After the download is finished, write it to the USB drive
    - **The entire USB drive will be erased**
    - Click the "Install macOS Ventura" button
    - Click the button for your connected USB drive
- Click "Build and Install OpenCore"

# Boot from your installer disk

> <https://dortania.github.io/OpenCore-Legacy-Patcher/BOOT.html>

- Hold down the `Option` key as you turn on your machine and **click the EFI
  Boot** icon (not the "Install macOS Ventura" icon)
- Then select the "Install macOS Ventura" icon on the next screen
    - Click the "Continue" button
    - Click the "Agree" button
    - Click the new "Agree" button
    - Select your "Macintosh HD" to install to and click the "Continue" button
There will probably be a couple reboots

# Post-installation

> <https://dortania.github.io/OpenCore-Legacy-Patcher/POST-INSTALL.html>

After you login to the updated system, you will likely be met with a pop-up.

Pop-up dialog:

```
OpenCore Legacy Patcher has detected that you
are booting OpenCore from an USB or External
drive.

If you would like to boot your Mac normally
without a USB drive plugged in, you can install
OpenCore to the internal hard drive.

Would you like to launch OpenCore Legacy
Patcher and install to disk?
```

- Click "OK"
- Click "Install to disk"
- Click the button for your internal disk
- Click the button for your EFI volume

Pop-up dialog:

```
Reboot to apply?

OpenCore has finished installing to disk.

You will need to reboot and hold the
Option key and select OpenCore/Boot
EFI's option.

Would you like to reboot?
```

- Click "Reboot"
- Click "Restart" (are you sure you want to restart your computer now?)
- Unplug your USB disk
- Hold down the Option key as the computer starts to boot
- Click the "EFI Boot" icon
- Click the "Macintosh HD" icon
- Select your user and login

# Re-install xcode command line developer tools

Open the Terminal app and run the following

```
xcode-select --install
```

If you get an error message saying that "command line tools are already
installed", you can delete them and try again.

```
sudo rm -rf /Library/Developer/CommandLineTools
xcode-select --install
```

- Click the "Install" button to install the command line developer tools
- Click the "Agree" button

# Update homebrew and reinstall packages

Once xcode command line developer tools have finished installing, update
homebrew

```
brew update
```

If the [kenjyco base](https://github.com/kenjyco/base) wrappers were setup, you
can use the following shell function

```
brew-reinstall-non-casks
```

If not, you can run

```
brew list -1 --formula | xargs brew reinstall
```

### Uninstall and re-install Homebrew (optional)

If you are getting any weird errors, you can always uninstall homebrew and then
install it again.

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"
```
> See: <https://github.com/homebrew/install#uninstall-homebrew> which was linked
> on <https://docs.brew.sh/FAQ#how-do-i-uninstall-homebrew>

After uninstall, there may be output at the end about undeleted directories.

```
The following possible Homebrew files were not deleted:

/usr/local/Frameworks/
/usr/local/Homebrew/
/usr/local/bin/
/usr/local/etc/
/usr/local/include/
/usr/local/lib/
/usr/local/opt/
/usr/local/sbin/
/usr/local/share/
/usr/local/var/
```

Manually remove them with the following command

```
sudo rm -rf /usr/local/{Frameworks,Homebrew,bin,etc,include,lib,opt/sbin/share/var}
```

Then run the install command

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> See: <https://brew.sh>

### Use the kenjyco base repo to install packages with homebrew (optional)

If you needed to uninstall and reinstall homebrew, you can follow along with the
install instructions

> See: <https://github.com/kenjyco/base/?tab=readme-ov-file#install>

```
cd ~/repos/base
```

> Assuming the base repo was already cloned

Then source the install.sh script

```
source ./install.sh extras
```
