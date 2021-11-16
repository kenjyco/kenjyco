Setup Mac
=========

> Not including the obvious first step of running system update and installing
> homebrew via <https://brew.sh>

# Remote login with SSH

Open the Terminal app to run the following commands.

### Enable remote login

```
% sudo systemsetup -setremotelogin on
```

> Note: You can say "off" to disable it

### Double-check remotelogin status

```
% sudo systemsetup -getremotelogin
```

### Edit SSH config file

```
% sudo vim /etc/ssh/sshd_config
```

> Note: use `nano` if vim is not installed.

Find "rdAuth", uncomment the "PasswordAuthentication yes" line and change to no
(only allowed to login with SSH key)

```
PasswordAuthentication no
```

Add new "AllowUsers" line to specify the usernames that are allowed to login

```
# Space delimited list of users allowed to SSH in
AllowUsers ken
```

### Unload and load the SSH LaunchDaemeon

```
% sudo launchctl unload /System/Library/LaunchDaemons/ssh.plist

% sudo launchctl load -w /System/Library/LaunchDaemons/ssh.plist
```

### Create your SSH keypair if you haven't done so before

```
% ssh-keygen -C "my laptop"
```

> You can use any comment you want, but keep it short. Save the key to the
> default location when prompted and type a passphrase (don't leave the
> passphrase empty, even though it's allowed).

If you left all the defaults, new files will be created at `~/.ssh/id_rsa` and
`~/.ssh/id_rsa.pub`

### Make sure your `~/.ssh/authorized_keys` file exists

> If one doesn't exist, copy your public key (the .pub file when you generated
> an SSH keypair)

```
% cd ~/.ssh

% cat authorized_keys
ssh-rsa ALSFHSKLUHEL8asfdaf2w.... my laptop
```

If you got `cat: authorized_keys: No such file or directory`, create the file

```
% cp id_rsa.pub authorized_keys
```

### Copy your keypair to the `~/.ssh` directory on another computer

Use a USB stick or something to copy the files. Feel free to copy the
`authorized_keys` file too if you want to be able to SSH to the other computer
from the Mac as well.

### Make sure your `~/.ssh` directory has the correct permissions

```
% chmod 700 ~/.ssh
```

### Make sure files in your `~/.ssh` directory have the correct permissions

```
% chmod 600 ~/.ssh/*
```

# Check IP addresses

### Internal IP on local network

On wifi

```
% ipconfig getifaddr en0
```

On ethernet

```
% ipconfig getifaddr en1
```

List Hardware ports

> You may need to list hardware ports if you get no results when using `en0` or
> `en1` (i.e. when using a USB Ethernet adapter)

```
% networksetup -listallhardwareports
```

Checking on all hardware ports

```
% networksetup -listallhardwareports | grep Device | awk '{print $2}' | tr '\n' '\0' | xargs -0 -n1 ipconfig getifaddr
```

### External IP

```
% curl ifconfig.me
```

# Fixing xcode after OS upgrade

> For whatever reason, when you have a major system upgrade on Macs, there are
> almost always some issues...

If some command line tools you are used to running stop working immediately
after system upgrade, try re-installing xcode

```
% xcode-select --install
```

When the popup opens (The "xcode-select" command requires the
command line developer tools. Would you like to install the tools now?), click
"Install", then click "Agree"

After several minutes, you'll see "The software was installed".. click "Done"

# Re-install git with homebrew

> If after a system upgrade, the `repos-update` command does dumb stuff like
> delete files in a repo and stage them, you may need to re-install git
>
> First, run `git restore --staged .` in any repos where that occured.

```
% brew reinstall git

% brew link --overwrite git
```

# Installing Docker

> When there were only Macs with Intel chips, you could just use the `brew` or
> `brew cask` commands to install docker. Since [Apple started making their own
> chips](https://www.apple.com/newsroom/2020/11/apple-unleashes-m1) and
> eventually got them to work with Docker, you must manually go to the website
> and download the correct `Docker.dmg` for your chip

Visit <https://www.docker.com/products/docker-desktop> and click the button for
your kind of chip

- After downloading `Docker.dmg` open it
- Drag the Docker icon to Applications when prompted
- Use Spotlight Search (`command` + `space`) to search for the new Docker
  executable and open it
    - Click the "Open" button when asked "are you sure you want to open it"
    - Click "Ok" when "Docker Desktop needs privileged access" alert appears
    - Type your system password and click "Ok"
    - Click the box by "I accept the terms" on "Our Service Agreement has
      Changed", then click "Accept"

# Multiple users with access to homebrew

> Assumes homebrew has already been installed the default way (via their setup
> script, executed by your primary user).

- Open "System Preferences" and select "Users & Groups"
    - Click the lock and enter your password
    - Click the `+` sign
    - In the "New Account" dropdown, select "Group"
    - Enter `homebrew` as the Full Name and click "Create Group"
    - Check the box next to your user
- Open a Terminal, use the new group and update permissions

    ```
    % sudo chgrp -R homebrew $(brew --prefix)/*

    % sudo chmod -R g+w $(brew --prefix)/*
    ```

# The brew cask sequence

> To install GUI programs in the past with homebrew, you had to do something
> like `brew cask install iterm2` or `brew cask install vlc`.

After attempting to `brew cask install zettlr` on 2/23/21, the homebrew tool
auto-updated as usual, but at the end I received **`Error: Unknown command:
cask`**. Not a big deal, I was able to install with `brew install zettlr`

However, a little later I noticed that when I opened a new terminal window, I
was getting the following

```
compinit:503: no such file or directory: /usr/local/share/zsh/site-functions/_brew_cask
```

To fix:

```
% brew cleanup
```

# Upgrading `reattach-to-user-namespace` wrapper

If at some point you get a message similar to **warning:
reattach-to-user-namespace: unsupported new OS, trying as if it were 10.10**
when you start a new `tmux` session, try upgrading

```
% brew upgrade reattach-to-user-namespace
```

Then open a new terminal and try to start a new session with `tmux`

```
% tmux
```

When you call `reattach-to-user-namespace --version`, the output also shows
versions of OS X that are supported

```
% reattach-to-user-namespace --version
reattach-to-user-namespace version 2.9
    Supported OSes: OS X 10.5-11.0
```

# Startup sequences

Full list at <https://support.apple.com/en-us/HT201255>

- `Command` + `r`       startup the built-in recovery system

# Quirks SSH-ing to Macs

### Extra characters appearing when you type

You may need to set your `TERM` variable first

```
% TERM=xterm-256-color ssh somemac
```

### Unable to access installed commands when using `ssh -t`

Sometimes you just want to execute a command or sequence of commands on a remote
machine and exit immediately, which `ssh -t` allows you to do. However, for
programs installed with `brew` (into `/usr/local/bin`), you may get a "command
not found" error.

Update your `PATH` variable to include `/usr/local/bin`

```
% ssh somemac -t 'PATH="/usr/local/bin:$PATH"; some-command'
```
