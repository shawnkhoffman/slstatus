# slstatus - suckless status

- [slstatus - suckless status](#slstatus---suckless-status)
  - [Features](#features)
  - [Requirements](#requirements)
  - [Installation](#installation)
  - [Running slstatus](#running-slstatus)
  - [Configuration](#configuration)
  - [Upcoming](#upcoming)

slstatus is a suckless status monitor for window managers that use WM_NAME
(e.g. dwm) or stdin to fill the status bar.

## Features

- Battery percentage/state/time left
- CPU usage
- CPU frequency
- Custom shell commands
- Date and time
- Disk status (free storage, percentage, total storage and used storage)
- Available entropy
- Username/GID/UID
- Hostname
- IP address (IPv4 and IPv6)
- Kernel version
- Keyboard indicators
- Keymap
- Load average
- Network speeds (RX and TX)
- Number of files in a directory (hint: Maildir)
- Memory status (free memory, percentage, total memory and used memory)
- Swap status (free swap, percentage, total swap and used swap)
- Temperature
- Uptime
- Volume percentage
- WiFi signal percentage and ESSID

## Requirements

Currently slstatus works on FreeBSD, Linux and OpenBSD.
In order to build slstatus you need the Xlib header files.

## Installation

By default, slstatus is installed into the /usr/local namespace. If this does not match your local setup, edit config.mk accordingly.

Afterwards, enter the following command to build and install slstatus (if necessary as root):

    make clean install

## Running slstatus

Add the following line to your .xinitrc / .xprofile to start slstatus using startx:

    slstatus &

## Configuration

My config has several status items available and intended for laptops:

- WiFi signal percentage and ESSID.
- Network download/upload speed.
- CPU usage (percentage) & temperature.
- RAM usage (percentage).
- System volume percentage.
- Battery charge (percentage) & charging state (charging, fully-charged, and discharging).
- System date & time.

slstatus can be customized by modifying the [config.h](/config.h) file and (re)compiling the source code. This keeps it fast, secure and simple. It is recommended to use a text editor such as Vim, nano, or Emacs when you edit config.h (using another utility, e.g., an IDE, can cause issues with seeing glyphs, for example).

> **Note:** Do not modify the [config.def.h](/config.def.h) file. Instead, use this file as a state backup of the original working config in case you ever need to revert back to it.

The commented-out table provided in the config.h file shows the different possible items and is useful for getting information on their functions & parameters.

Below are the default status items that are configured in this build:

| Status item | Function format | Arguments |
| ----------- | --------------- | --------- |
| WiFi SSID   | wifi_essid      | **First argument:** `%s` (modulus operator). Also, an optional string (glyph) is used to provide a visual effect. <br><br>**Second argument:** Network device ID (e.g., `wlan0`). |
| WiFi Signal Strength (percentage) | wifi_perc | **First argument:** `%s` (modulus operator). <br><br>**Second argument:** Network device ID (e.g., `wlan0`). |
| Network download speed | netspeed_tx | **First argument:** `%s` (modulus operator). <br><br>**Second argument:** Network device ID (e.g., `wlan0`). |
| Network upload speed | netspeed_tx | **First argument:** `%s` (modulus operator). <br><br>**Second argument:** Network device ID (e.g., `wlan0`). |
| CPU usage (percent) | cpu_perc | **First argument:** `%s` (modulus operator). |
| CPU temperature | cpu_perc | **First argument:** `%s` (modulus operator). <br><br>This feature relies on CPU sensor data which you can get from running `sensors-detect` (requires the `lm_sensors` package). Be sure the correct adapter is provided in place of `coretemp-isa-0000`. |
| System volume (percent) | run_command | **First argument:** %4s (modulus operator) is expected here. |
| Battery charge (percent) | battery_perc | **First argument:** `%s` (modulus operator). <br><br>**Second argument:** Battery device ID (default is `BAT0`). |
| Battery charging state | battery_state | **First argument:** `%s` (modulus operator). <br><br>**Second argument:** Battery device ID (default is `BAT0`). |
| System date & time | datetime | **First argument:** `%s` (modulus operator). **Second argument:** Date & time format (default is `%a %b %d %r`). |

> By default, all configured features in this build are turned on. You will need to simply comment out (or remove) the features you don't want. See more below.

## Upcoming

A release (v1.0) will come soon... ;)
After a long phase of inactivity, development has been continued!

<sub>See more from suckless at [suckless.org](https://suckless.org/)</sub>