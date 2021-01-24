Setup Linux Mint
================

> Starting from the first time your machine boots after initial install.

# Linux Mint shortcuts

- `win`                  open menu to search for things ("display", "software manager", "firefox")
- `ctrl` + `alt` + `t`   open a new terminal window
- `ctrl` + `alt` + `l`   lock the screen
- `win` + (any arrow)    snap current window to a side of the screen

# Open a terminal, sync package index, and install some packages

First thing is to resync the packed index from sources specified in
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

# Click the sheild icon in the in the lower right area of the screen

> This is the Update Manager, so make sure you are connected to the internet

- Click "OK" on the first screen
- If "A new version of the Update Manager is available" appears, click "Apply
  the Update"
    - type your user's password
- When presented with the pre-selected list of package names to upgrade, click
  the "Install Updates" button near the top of thw Update Manager window
    - If "This upgrade will trigger additional changes" appears, click "OK"
        - type your user's password again
    - (this will take a while the first time it runs)
    - If "Reboot required: You have installed updates that require a reboot to
      take effect, please reboot your system as soon as possible" appears,

Also note that over time, there will be new versions of the Update Manager. Try
to notice when you see a little red dot in the sheild icon in the lower right
area of the screen (indicating an update is available)

# TODO

- removing prompt in Update Manager for "do you want to switch to a local
  mirror"
- setup automatic downloading of updates (but not installing)
- removing setting to display `$HOME` directory contents on the desktop
- SSH server setup
