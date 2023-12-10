### HP Elitebook 840 G7 Experience

# Table of Contents

| Section | Title |
| ------- | ----- |
| 01 | [Overview](#01) |
| 02 | [Pop!_OS Tweaking](#02) |

<a id="01"></a>
# Overview

Product details - https://support.hp.com/us-en/product/details/hp-elitebook-840-g7-notebook-pc/model/38462573?serialnumber=5CG1093SMR&sku=206F2US

Maintenance - https://youtu.be/qL4jRL1xNdc

<a id="02"></a>
# Pop!_OS Tweaking

## Extensions

Vitals - https://extensions.gnome.org/extension/1460/vitals/

## Issues

### Lid Switch Detection

Issue(s):
1. Lid is not detected as closed when I close the laptop.
2. When I hook up the laptop a monitor and switch to 'External Only' mode, the lid switch fires excessively between 'open' and 'closed' during suspend. This wakes the computer.
    - May have to reconfirm this through logging. Command is `journalctl --since '{YOUR_VALUE} {minutes/hours} ago' | grep -i ' lid '`

It's not worth enabling lid events if either of these do not work.

*\*Solution\** disable lid events. Changes made:

GNOME Tweaks installed with `sudo apt update && sudo apt install gnome-tweaks`. 'Suspend when laptop lid is closed' is set to 'off'.

The `/etc/systemd/logind.conf` file has original settings:

```
#HandleLidSwitch=suspend
#HandleLidSwitchExternalPower=suspend
#HandleLidSwitchDocked=ignore
```

Changed to:

```
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore
```

The `/etc/UPower/UPower.conf` file has original settings:

```
IgnoreLid=false
```

Changed to:

```
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
    for device in RP05 RP09; do
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

## `~/.bash_aliases`

```bash
alias vsc='flatpak run com.visualstudio.code' # assuming VS Code installed with Flatpak
```

