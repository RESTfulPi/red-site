---
layout: default
parent: Development
nav_order: 7
---

# Docker
In order to simplify installation and updates on the Raspberry Pi, Docker images containing the REST API and Robot Operating System Code were created in the late stages of development. All docker images are automatically built using Github Actions. To see information on that, see [Github Actions](github-actions).

## Robot Operating System Container
Docker provides prebuilt containers containing the necessary build tools and base libraries for the Robot Operating System. Using Docker's multistaged build process and the ROS development image `ros:humble`, our code is compiled and then copied over to another ROS image `ros:humble-ros-core`, which contains only the ROS runtime.
### Code

{: .note }
This container uses multiplatform base images, allowing docker's build chain to build for multiple platforms using the same Dockerfile. For more info see [Multiplatform Support](github-actions#multiplatform-support).

```Dockerfile
ARG ROS_VERSION=humble
ARG ROS_PLATFORM=

FROM ${ROS_PLATFORM}ros:${ROS_VERSION} AS builder
ARG OVERLAY_WS=/opt/ros/overlay_ws

WORKDIR ${OVERLAY_WS}
COPY . .

RUN . /opt/ros/$ROS_DISTRO/setup.sh && colcon build



FROM ${ROS_PLATFORM}ros:${ROS_VERSION}-ros-core AS exec
ARG OVERLAY_WS=/opt/ros/overlay_ws
WORKDIR ${OVERLAY_WS}

COPY --from=builder ${OVERLAY_WS}/install .

# source entrypoint setup
ENV OVERLAY_WS $OVERLAY_WS
RUN sed --in-place --expression \
      '$isource "$OVERLAY_WS/setup.bash"' \
      /ros_entrypoint.sh

RUN echo "chmod 777 /dev/ttyUSB0" >> /cmd.sh && echo "ls -l /dev" >> /cmd.sh && echo "ros2 launch uxa_serial uxa-system-launch.xml" >> /cmd.sh
# run launch file
CMD ["sh", "/cmd.sh"]
```


## REST API Container
Due to the REST API Server's use of the [rclnodejs](https://github.com/RobotWebTools/rclnodejs) Node.js package, the API Server requires Robot Operating System to be installed in order to access the ROS library. To facilitate this, the API Server container is built over the `uxa-90_ros_packages` image built on Github. Node.js is installed and `npm ci` is run to install all package dependencies for the API Server.
### Code

{: .note }
This container uses multiplatform base images, allowing docker's build chain to build for multiple platforms using the same Dockerfile. For more info see [Github Actions](github-actions#multiplatform-support).

```Dockerfile
FROM ghcr.io/4850-red/uxa-90_ros_packages:main

WORKDIR /opt/api

RUN apt-get update && apt-get install -y curl && \
    curl -fsSL https://deb.nodesource.com/setup_16.x | bash - && apt-get install -y nodejs && \
    npm install -g npm && apt-get clean

COPY . .

RUN apt-get install -y g++ make && . /opt/ros/humble/setup.sh && \
    npm ci && apt-get remove -y g++ make && apt-get autoremove -y && apt-get clean

CMD npm run start
```