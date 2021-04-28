Setup Linux Mint
================

> Starting from the first time your machine boots after initial install.

# Linux Mint shortcuts

> Using the [Cinnamon Desktop Environment](https://en.wikipedia.org/wiki/Cinnamon_(desktop_environment))

- `win`                  open menu to search for things ("display", "software manager", "firefox")
- `ctrl` + `alt` + `t`   open a new terminal window
- `ctrl` + `alt` + `l`   lock the screen
- `win` + (any arrow)    snap current window to a side of the screen

# Open a terminal, sync package index, and install some packages

First thing is to resync the package index from sources specified in
`/etc/apt/sources.list` and files in `/etc/apt/sources.list.d`

```
$ sudo apt-get update
```

Install `git`, clone my base repo, then source the install.sh script

```
$ sudo apt-get install -y git
...

$ git clone https://github.com/kenjyco/base

$ cd base

$ source ./install.sh all
```

# Click the shield icon in the in the lower right area of the screen

> This is the Update Manager, so make sure you are connected to the internet

- Click "OK" on the first screen
- If "A new version of the Update Manager is available" appears, click "Apply
  the Update"
    - type your user's password
- When presented with the pre-selected list of package names to upgrade, click
  the "Install Updates" button near the top of the Update Manager window
    - If "This upgrade will trigger additional changes" appears, click "OK"
        - type your user's password again
    - (this will take a while the first time it runs)
    - If "Reboot required: You have installed updates that require a reboot to
      take effect, please reboot your system as soon as possible" appears,
      reboot the computer after adjusting more initial settings

Also note that **over time, there will be new versions of the Update Manager**.
Try to notice when you see a little red dot in the shield icon in the lower
right area of the screen (indicating an update is available)

# Adjust more Update Manager settings

- With the Update Manager open, click the "Edit" menu and select "Software
  Sources"
    - Type your password and click "Authenticate"

# Use the GUI to change some system settings

- Press the `win` key to pull up the Linux Mint menu
- Type "windows" and click on the result in the menu
    - Click on the "Behavior" tab
        - Change "Window focus mode" from "Click" to "Mouse" (which allows you
          to focus on a window to quickly type something or scroll, without
          bringing it to the forefront)
    - Click on the "Alt-Tab" tab
        - Change "Alt-Tab switcher style" from "Icons and thumbnails" to "Window
          preview (no icons)"

# Troubleshooting

### "Missing operating system" on boot?

Unplug the USB stick and hit `Ctrl` + `Alt` + `Delete`.

> There may be a BIOS setting enabled to try to boot from an external USB device
> if it's connected. If that device doesn't have a bootable partition, it will
> error out.


# TODO

- removing prompt in Update Manager for "do you want to switch to a local
  mirror"
- setup automatic downloading of updates (but not installing)
- removing setting to display `$HOME` directory contents on the desktop
- SSH server setup
