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

These 2 existing environments and frameworks are standard and widely used for most web applications. They fit our perfect needs to communicate to our robot wirelessly over a network, or even potentially the internet. Typescript is necessary and offers no boost in performance. However, it makes the development process significantly smoother with the use of typing.

## ROS Integration
In order for the API server to perform robot actions, there needs to be a connection to ROS.
It is possible to communicate by sending messages over rose nodes.
There is an existing Node.js package called [rclnodejs](https://www.npmjs.com/package/rclnodejs) that makes this process easier.

## Prototype

## Documentation

## Client
