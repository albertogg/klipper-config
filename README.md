# Klipper Config

Klipper configuration files.

## Supported software versions

This configuration is currently used with these versions:

- Klipper: `v0.13.0-718`
- Moonraker: `v0.10.0-31-gd5ee1712`
- Fluidd: `v1.37.3`

## Ender 3 Pro

Klipper configuration for the Ender 3 Pro with the following mods:

- Board: BIGTREETECH SKR 1.4 Turbo
- Stepper Motor Drivers: TMC2209 (sensorless homing)
- Probe: BlTouch V3 (5v)
- Extruder: BMG clone
- Host: Raspberry Pi 3B+
- Phaetus Dragonfly Hotend (BMS)


## Installation

Install Klipper, Moonraker, and Fluidd on the Raspberry Pi by following the
[KIAUH installation instructions](https://github.com/dw-0/kiauh).

### Flash the controller firmware

The initial Klipper firmware installation on the BIGTREETECH SKR 1.4 Turbo must
be performed with a microSD card.

1. SSH into the Raspberry Pi and configure the firmware build:

   ```shell
   cd ~/klipper
   make menuconfig
   ```

   Select these options:

   - Micro-controller Architecture: `LPC176x`
   - Processor model: `lpc1769 (120 MHz)`
   - Bootloader offset: `16KiB bootloader`
   - Communication interface: `USB`

2. Compile the firmware:

   ```shell
   make
   ```

3. Insert a FAT32-formatted microSD card into your computer. From the computer,
   copy the compiled firmware from the Raspberry Pi directly to the card,
   renaming it to `firmware.bin`:

   ```shell
   scp your-user@raspberrypi.local:~/klipper/out/klipper.bin \
     /path/to/mounted-microSD/firmware.bin
   ```

   Replace the SSH user, Raspberry Pi hostname, and microSD mount path as
   needed.

4. Power off the printer and disconnect its USB cable. Insert the microSD card
   into the SKR board, then power the printer on. The board flashes the firmware
   during startup and renames the file to `FIRMWARE.CUR` when successful.
5. Power the printer off, remove the microSD card, reconnect USB, and power it
   back on.
