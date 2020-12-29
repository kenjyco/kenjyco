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

### External IP

```
% curl ifconfig.me
```

# Fixing xcode after OS upgrade

> For whatever reason, when you have a major system upgrade on Macs, there are
> almost always some issues...

If some command line tools you are used to running stop working immediate after
system upgrade, try re-installing xcode

```
% xcode-select --install
```

When the popup opens (The "xcode-select" command requires the
command line developer tools. Would you like to install the tools now?), click
"Install", then click "Agree"

After several minutes, you'll see "The software was installed".. click "Done"
