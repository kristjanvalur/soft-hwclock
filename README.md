# fake-hwclock

## description

Many simple systems, such as the Raspberry PI, don't have hardware clocks.
When they boot, they start with their system clock set at some fixed date, e.g. 2000/01/01 00:00:00
a fake-hwclock sets the initial time to some known value from before the last reboot.

Some systems have packages for this available, while others don't.  This repository consists of
shell scripts and service files for _systemd_ based systems to achieve this, and has been
tested on a Raspberry Pi running CeentOS 7

## features

Sets the time to a "recent" timestamp early in the boot to avoid timestamps
far in the past when booting, prior to getting a proper timestamp from the network.

- Restores the system clock from file during early boot
- Saves the clock into a file at shutdown
- Regularly saves the current time into the data file, in case of improper shutdown.
- shell based to avoid platform and binary dependencies.

## installation:

1. copy these files into `/opt/fake-hwclock/`
2. install the services:
```sh /opt/fake-hwclock/install```
3. enable and start service:
```systemctl enable fake-hwclock.service && systemctl start fake-hwclock.service```

