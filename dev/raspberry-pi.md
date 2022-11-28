---
layout: default
parent: Development
nav_order: 6
---

# Raspberry Pi

## Overview
After inspecting the Intel NUC that was installed in the robot, it was clear that we would be having problems with it at every step of the project.
The computer was old and the version of Ubuntu 14.04 it was running was having problems connecting to Kennesaw's WiFi.
A Raspberry Pi seemed like a good solution, as it has a small form factor and would be much easier to keep updated.

## Configuration
We are using the 8 GB RAM model of the Raspberry Pi 4 with Ubuntu 22.04 LTS installed.

## Docker
Code was initially tested on our personal computers, then deployed onto the Pi using Docker images. To see more about Docker click [here](docker).

{: .important }
Due to differences in CPU architecture, Docker images are implemented using Docker multiplatform. For more info see [Multiplatform Support](github-actions#multiplatform-support).

