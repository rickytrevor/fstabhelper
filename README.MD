# Why?
I created this script for 2 reasons, the first one is that most of the time I do not feel confortable manually editing the fstab file, the second one is that I was bored


# install 
to install the package you just need to run make install


# Usage
sudo fstabhelper /dev/(device) /mnt

## Compatibility
This script should work on all linux distributions running systemD (if you look at the source code you'll see that i use x-systemd.device-timeout, I don't know what happends in a non-systemd distro)
I've only tested this in my main rig (fedora35) and server (Rocky linux 8.5)
