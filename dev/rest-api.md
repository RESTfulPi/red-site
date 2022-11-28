---
layout: default
parent: Development
nav_order: 5
---

# REST API

## What is a REST API?

<center>
<div class="code-example" markdown="1">
**REST**: **RE**presentational **S**tate **T**ransfer

**API**: **A**pplication **P**rogram **I**nterface
</div>
</center>


An API defines how two parties can communicate with each other (e.g. a robot and a controller). A REST API is an API that uses the REST standard, which has a set of guidelines which dictate the API architecture.

## Server
Implemented with:

- Node.js: open-source, cross-platform, back-end JavaScript runtime environment that runs on the V8 engine and executes JavaScript code outside a web browser.
- Express.js: back-end web application framework for building RESTful APIs with Node.js

These 2 existing environments and frameworks are standard and widely used for most web applications. They fit our perfect needs to communicate to our robot wirelessly over a network or the internet. Typescript is not necessary and offers no boost in performance, however it makes the development process significantly smoother with the use of typing.

## ROS Integration

In order for the API server to perform robot actions, there needs to be a connection to ROS. It’s possible to communicate by sending messages over ROS nodes. There is an existing Node.js package called [rclnodejs](https://www.npmjs.com/package/rclnodejs) that eases this process.

## API Documentation

Full documentation for using the API can be found [here](api), or by exploring the API section in the tab on the side of the page.
This serves as a way for others to utilize the power of the API without needing development experience.
