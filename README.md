# thinkpad-x1-g7-suspend-issues-elementary-6-odin
Thinkpad X1 g6 can show some issues regarding to suspend / restore session when using Elementatry OS 6 Odin.
Below are some topics that I've solved with some research.

# Suspend On shows blank screen
When suspension recovers it only shows a blank screen, and sometimes it blinks the screen. Cannot see login screen but can switch to terminal and login.

I've discovered that it was related to something with LightDM. For this one I've followed the instructions that sets up again the .Xauthority file and fix dpkgs.

```
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm restart
```
- Ctrl+Alt+F1 to switch to terminal.
- Login in terminal.

`sudo apt-get update`

- Restart the system.
- On GRUB, select to run linux in recovery mode.
- on recovery mode, select repair broken dpkg packages.
- Restart the system in normal mode.

Everything should work as expected now.

# Wakes up from suspension
Another behavior with suspension is that it wakes up by itself after a while. I've discovered that it was related to USB devices that keeps alive ([as bluetooth or WiFi](https://askubuntu.com/questions/1133919/ubuntu-18-04-2-immediately-wakes-up-from-suspend)).

Also, X1 gen7 has a BIOS option that can be enabled/disbled regarding to when the machine should wake up when USB/AC Power is connected. Disable it.
Another option to change in the BIOS is the suspend optimization for Linux OS (usually is set to Windows).

# Sources
- [Blank screen after login ubuntu 16.04](https://stackoverflow.com/a/51910183/4963247)
- [configure ubuntu to unsuspend when connected to power](https://superuser.com/questions/1706844/configure-ubuntu-to-unsuspend-when-connected-to-power)
