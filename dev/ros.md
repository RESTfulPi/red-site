---
layout: default
parent: Development
nav_order: 4
---

# Robot Operating System

## Overview

The robot has ROS (Robot Operating System) 1.0 installed on the onboard computer.
This was outdated and needed to be upgraded.
Using a Raspberry Pi 4, the robot could be upgraded to the more functional ROS 2.0 and be controlled externally through a serial port.
Much of the source code had to be converted to be compatible with the new version of ROS.

## Changes

- ### Build System Change
Changed from `cmake` to `colcon`

- ### Dependency Changes
Library and function names were updated

- ### Broken Code
Provided code from RoboBuilder was not formatting serial messages correctly

## Implementation

This communication layer is made up of the `uxa_serial`, `uxa_uic_driver`, and `uxa_sam_driver` packages.
The uxa_serial package handles connecting to the robot over a USB serial interface, while the `uxa_uic_driver` and `uxa_sam_driver` packages handle prebuilt motion control and individual motor control, respectively.
The `uxa_uic_driver` and `uxa_sam_drivers` format commands into raw bytes and forward them to the `uxa_serial` package for transmission.
