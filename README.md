# ibm-ups

## Overview

An Uninterruptible Power Supply (UPS) provides a temporary power source if AC
(wall) power is lost.

The UPS contains a battery that can support a system for a brief period (such
as 30 minutes). The UPS allows the system to keep running during a short power
outage. During a long outage, the UPS gives the operating system time to
perform an orderly shutdown.

The UPS must be connected to a USB port using an IBM "System Port Converter
Cable". At most one UPS can be attached using a USB port.

The ibm-ups application monitors the UPS. ibm-ups publishes the UPS status on
D-Bus. The chassis state manager application utilizes the D-Bus information.
PLDM creates a composite state sensor based on the D-Bus information. The PLDM
sensor makes the UPS status available to the operating system.

## Build

To build the repository:

```sh
  meson setup build
  ninja -C build
```

To clean the repository and remove all build output:

```sh
  rm -rf build
```
