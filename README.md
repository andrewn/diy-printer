## Install

1. Follow the [Getting Started](https://www.balena.io/os/docs/raspberrypi3/getting-started/) istructions for your platform, until you get to "Running your first Container"
2. `balena push <your-host-name>.local`
3. `sirius-client` will be installed

### Wiring

### Printer

**DST** must be connected to ground
Pi GND, Printer GND, Power supply -ve must all be connected

### Disable console output on the serial port

1. `balena ssh <your-host-name>.local`
2. `vi /mnt/boot/cmdline.txt`
3. `ESC` -> `:` -> `i` to edit text
4. Delete: `console=serial0,115200`
   So from:
   dwc_otg.lpm_enable=0 console=tty1 console=serial0,115200 rootfstype=ext4 rootwait
   To:
   dwc_otg.lpm_enable=0 console=tty1 rootfstype=ext4 rootwait
5. `ESC` -> `:` -> `x` to save and exit
6. If on a Pi3, carry on from step 2 below, else `reboot`

### On a Pi 3

1. `balena ssh <your-host-name>.local`
2. `vi /mnt/boot/config.txt`
3. `ESC` -> `Shift` + `G` to skip to end of file
4. `ESC` -> `:` -> `i` to edit text
5. Add `dtoverlay=pi3-miniuart-bt` on a new line at the end
6. `ESC` -> `:` -> `x` to save and exit
7. `reboot` to restart the pi
