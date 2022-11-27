---
layout: default
parent: Development
---

# Mobile App

## Implementation

As an example for a front-end interface, we decided to create a mobile app to demonstrate the API.
The app is programmed in Expo, which is based on React Native.
The app just sends HTTP requests while the seperate server does all of the heavy lifting.
This modularity is beneficial for future projects.

## Usage

The current design of the app is tailored to fit a proof-of-concept demonstration.
When the app is first opened, the user is greeted with a login screen.
After putting in an IP address, the user is brought to a controller screen.
The user can directly control the movement of the robot with the buttons shown.
At the bottom of the app, there is also a motions tab and a motor tab.
The motions tab lets the user select and play a programmed motion for the robot,
and the motor tab lets the user mantually select and control the motors on the robot.
