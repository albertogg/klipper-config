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

### Prerequisites
This configuration uses modern Klipper syntax (e.g., `default_parameter_X`).
If you encounter the error `Option 'default_parameter_x' is not valid in section 'gcode_macro pause'`,
please update your Klipper firmware to version 0.11.0 or newer.
