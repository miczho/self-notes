### The HP Elitebook 840 G7 Experience

# Table of Contents

| Section | Title |
| ------- | ----- |
| 01 | [Overview](#01) |
| 02 | [Pop!_OS 22.04 LTS Tweaking](#02) |
| 03 | [Fedora Workstation 38 Tweaking](#03) |

<a id="01"></a>
# Overview

Product details - https://support.hp.com/us-en/product/details/hp-elitebook-840-g7-notebook-pc/model/38462573?serialnumber=5CG1093SMR&sku=206F2US

Maintenance - https://youtu.be/qL4jRL1xNdc

<a id="02"></a>
# Pop!_OS 22.04 LTS Tweaking

## Issues

### Lid Switch Detection

Issue(s):
1. Lid is not detected as closed when I close the laptop.
2. When I hook up the laptop to a monitor and switch to 'External Only' mode, the lid switch fires excessively between 'open' and 'closed' during suspend. This wakes the computer.
    - May have to reconfirm this through logging. Command is `journalctl --since '{YOUR_VALUE} {minutes/hours} ago' | grep -i ' lid '`
    - *\*Update\** PROBABLY NOT TRUE

It's not worth enabling lid events if either of these do not work.

*\*Solution\** Disable lid events. Changes made:

GNOME Tweaks installed with `sudo apt update && sudo apt install gnome-tweaks`. 'Suspend when laptop lid is closed' is set to 'off'.

The `/etc/systemd/logind.conf` file has original settings:

```conf
#HandleLidSwitch=suspend
#HandleLidSwitchExternalPower=suspend
#HandleLidSwitchDocked=ignore
```

Changed to:

```conf
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore
```

The `/etc/UPower/UPower.conf` file has original settings:

```conf
IgnoreLid=false
```

Changed to:

```conf
IgnoreLid=true
```

### Unexpected Wakeup

Issue(s):
1. Laptop in suspend wakes by itself. Sometimes immediately, sometimes after 1+ hours.

It's suspected that one or more of the devices listed from `cat /proc/acpi/wakeup` is triggering this.

Supporting forum posts:
- [Wake up from suspend using wireless USB keyboard or mouse (for any Linux Distro)](https://askubuntu.com/questions/848698/wake-up-from-suspend-using-wireless-usb-keyboard-or-mouse-for-any-linux-distro)
- [Ubuntu wakes up after few seconds of sleep](https://askubuntu.com/questions/598236/ubuntu-wakes-up-after-few-seconds-of-sleep)
- [How do I prevent immediate wake up from suspend and/or hibernation?](https://askubuntu.com/questions/148481/how-do-i-prevent-immediate-wake-up-from-suspend-and-or-hibernation)

*\*Solution\** Add a custom script `/lib/systemd/system-sleep/device-wakeup-disable`:


```bash
#!/bin/sh

# /lib/systemd/system-sleep/device-wakeup-disable
#
# Avoids that system wakes up immediately after suspend or hibernate

case "$1" in
  pre)
    for device in XHC TXHC; do
      if grep -qE "^$device.*enabled" /proc/acpi/wakeup; then
        echo "Disabling wakeup on $device" 
        echo "$device" > /proc/acpi/wakeup
      fi
    done
    ;;
  *)
    ;;
esac
```

[Disabling wake-on-lan](https://askubuntu.com/a/1459436) in NetworkManager config

> You can disable Wake-on-LAN for all connections permanently by adding a dedicated configuration file : /etc/NetworkManager/conf.d/wake-on-lan.conf

Create the file:

```bash
sudo nano /etc/NetworkManager/conf.d/wake-on-lan.conf
```

Then paste the following into the file:

```conf
[connection]
ethernet.wake-on-lan = ignore
wifi.wake-on-wlan = ignore
```

Press `Ctrl+O` to save the changes and then press `Ctrl+X` to exit

### Apple AirPods Pro Connection Failure

Issue(s):
1. AirPods won't connect.

Airpods don't work on Bluetooth Low Energy and Dual-Mode so we have to force all devices to use Bluetooth BR/EDR (Classic Bluetooth).

Changes made to `/etc/bluetooth/main.conf`:

Original setting:

```conf
#ControllerMode = dual
```

Changed to:

```conf
ControllerMode = bredr
```

Once changes are made, run `sudo /etc/init.d/bluetooth restart` *WITH BLUETOOTH TURNED OFF*.

## Customizations

Vitals GNOME Extension - https://extensions.gnome.org/extension/1460/vitals/

### `~/.bash_aliases`

```bash
alias vsc='flatpak run com.visualstudio.code' # assuming VS Code installed with Flatpak
```

### Shortcuts

Lock: `Super+Esc`

*\*Custom\** Sleep: `Super+Shift+Esc`

Window next screen: `Super+Shift+{Left/Right}`

Window half: `Super+Ctrl+{Left/Right}`

*\*Custom\** Window full screen: `Super+Ctrl+Enter`

Workspaces: `Super+D`

Applications: `Super+A`

Launcher: `Super`

Copy/paste on terminal: `Ctrl+Shift+{C/V}`

Switch tabs on terminal: `Alt+{1/2/.../9/0}` or `Ctrl+{Page Up/Page Down}`

<a id="03"></a>
# Fedora Workstation 38 Tweaking

## Customizations

GNOME Extensions:
- Vitals - https://extensions.gnome.org/extension/1460/vitals/
- GSConnect - KDE Connect for GNOME (https://extensions.gnome.org/extension/1319/gsconnect/)
- Caffeine - https://extensions.gnome.org/extension/517/caffeine/

Red Hat Package Manager (RPM) Fusion - multimedia-related software, proprietary drivers (https://rpmfusion.org/Configuration)

Z Shell (Zsh) - https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH

Powerlevel10k - https://github.com/romkatv/powerlevel10k

### Z shell profile

```zsh
# ~/.zprofile

# Set PATH variable
export PATH="$PATH:/usr/local/texlive/2024/bin/x86_64-linux"
```

## General

Use `flatpak` for installing consumer apps, `dnf` for dev apps.

Suspend (Modern Standby/S0ix/S2idle) only works under airplane mode. Consider getting the wifi card replaced? Or wait until Fedora fixes.

`/lib/systemd/system-sleep/device-wakeup-disable` also added (see Pop!_OS).

# Misc

https://stackoverflow.com/questions/14637979
