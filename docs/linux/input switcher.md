---
title: "Input switcher"
---

Inspired by [marcelhoffs/input-switcher](https://github.com/marcelhoffs/input-switcher), I decided to create my own script for switching keyboard, mouse and monitor inputs with one button.

## Dependencies:
- Solaar: https://pwr-solaar.github.io/Solaar/
- ddcutil: https://www.ddcutil.com/

## The script
``` bash title="switch_input.sh"
#!/bin/bash
CAHNNEL=$1
MONITOR=$2

# Switch monitor input
ddcutil setvcp 60 0x1${MONITOR} -d 1 &
ddcutil setvcp 60 0x1${MONITOR} -d 2 &

# Switch keyboard and mouse inputs
solaar config "M720 Triathlon" change-host $CAHNNEL
solaar config "K850" change-host $CAHNNEL
exit 0
```

## Installation
```bash
chmod +x path/to/switch_input.sh

# needed to run the script without sudo
sudo chmod a+rw /dev/hidraw*
sudo chmod a+rw /dev/i2c-*
```

Then bind `path/to/switch_input.sh 1 1` as a shortcut via **Settings > Keyboard > View and Customize Shortcuts > Custom Shortcuts**

