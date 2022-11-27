---
layout: default
parent: Development
nav_order: 4
---

# Robot Operating System (ROS)

## Overview

The robot has ROS (Robot Operating System) 1.0 installed on the onboard computer. ROS is a data communication library/system the helps facilitate easier communication between various sub-processes (sometimes refered to as nodes/packages) that perform various functions in a complicated robotic system.


ROS 1.0 is an outdated version and needed to be upgraded.
Using a Raspberry Pi 4, the robot could be upgraded to the more functional ROS 2.0 and be controlled externally through a serial port.
Much of the source code provided by the robot manufacturer had to be converted to be compatible with the new version of ROS.

Robot Operating System supports implementing ROS packages in several languages. All packages here are implemented in C++ 11.

## Changes to Provided Code

- ### Build System Change
    - Build system changed from `catkin` to `colcon`
    - Build scripts needed to be completely rewritten for `colcon`
    - `package.xml` files needed to be recreated in new format for ROS 2.0

- ### Dependency Changes
    - Library and function names were updated between ROS 1.0 and ROS 2.0

- ### Broken Code
    - Provided `uxa-uic-drvier` package from RoboBuilder was not formatting serial messages correctly
    - ROS 2.0's `msg` file format changed slightly, requiring reworking of all the message types

## Implementation
This communication layer is made up of the `uxa_serial`, `uxa_uic_driver`, and `uxa_sam_driver` ROS packages. These packages run concurrently handling various functions by passing messages between them.
, while the `uxa_uic_driver` and `uxa_sam_driver` packages handle prebuilt motion control and individual motor control, respectively.
The `uxa_uic_driver` and `uxa_sam_drivers` format commands into raw bytes and forward them to the `uxa_serial` package for transmission to the robot.

### Package Overview: `uxa-serial`
The `uxa_serial` package handles connecting to the robot over a USB serial interface. Using messages defined in `uxa_serial_msgs`, this package takes byte array messages and forwards them across the serial connection to the robot and optional responds with a byte array of return data.

### Package Overview: `uxa_uic_driver`
The `uxa_uic_driver` package handles motion messages defined in the `uxa_uic_msgs` package. This package takes the specified motion and creates the serial byte message needed to call that action on the robot. The message is then forwarded to the `uxa-serial` package.

### Package Overview: `uxa_sam_driver`
The `uxa_sam_driver` package handles motor position messages defined in the `uxa_sam_msgs` package. This packages takes the specified motor position information and generates the serial command to move the motor to a position. This package also has the special multi-move service which allows multiple motors to be moved at the same time. The serial messages are forwarded to the `uxa-serial` package and returns the serial response of the motor move command.

---

## Message Packages
In order to share the message types across the various packages, ROS messages are defined and generated in separate packages to better facilitate code sharing.

### Package Overview: `uxa_sam_msgs`
The `uxa_sam_msgs` package contains the ROS messages related to motor movement.

### Package Overview: `uxa_uic_msgs`
The `uxa_uic_msgs` package contains the ROS messages related to motions.

### Package Overview: `uxa_serial_msgs`
The `uxa_serial_msgs` package contains the ROS messages related to serial communication. This package is a dependency of all other packages in the ROS system.