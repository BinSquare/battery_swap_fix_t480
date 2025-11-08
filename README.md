# Battery Swap Fix (Linux) for Lenovo T480

Scripts to automatically set `charge_start_threshold` to reasonable values, so the batteries are charged and switched correctly. Values are based on personal testing on my own device, use your own judgement and values if you need it. 

This is forked from a T470 fix which has mentioned that this is supposedly fixed with newest firmware. I personally still use my own script and have not tested with the default firmware (no interest in doing so). You can follow along the discourse on this at https://gitlab.freedesktop.org/upower/upower/-/issues/62. 


## Background
There is a bug either in the Linux kernel or the lenovo power management, that when not charging, only one battery is used and never the extra battery. 

When the first battery is empty the laptop can simply crash, since the Linux kernel thinks there is still more power, but some battery controller simply kills the power to protect the battery.

By enabling `charge_start_threshold`, by using a number greater than 0, the battery is correctly switched when that threshold is reached. But when the battery capacity is higher, then the battery won't charge.

This project tries to mitigate this dilema, by automatically setting the `charge_start_threshold` values accordingly to the current AC power status.

## Installation

To install run `sudo ./install.sh`.

To uninstall run `sudo ./uninstall.sh`.

In both cases your system could need a restart, so `udev` can reload the event monitoring rules correctly.

## Tested Device:
- Lenovo T480.

# No promise of support

Life has gotten busy, please note that I will not be able to answer questions on demand.
