---
layout: default
parent: Development
nav_order: 15
---

# Github Actions
This project utilizes Github Actions to facilitate automatic builds and deployments of the various subprojects. Github Actions is a toolbox service by Github which allows users to trigger actions after certain events happen on a Github Repository. These actions can perform anything from content review of pull requests to performing continuous integration. Github Actions in this project are used to automatically build and deploy the various subprojects, including:
- Generating and publishing this website, 
- Building and publishing the Robot Operating System Docker Image
- Building and publishing the REST API Server Docker Image

## Github Pages Action
Github Actions is used to automatically run our static site generator `Jekyll` when a commit is pushed to the [red-site](https://github.com/4850-red/red-site) Github Repository. After building the website, this action also publishes our website to Github Pages. See the [website](website) page for more information about how `Jekyll` and Github Pages work together.

## Robot Operating System Docker Image Action
Github Actions is used to automatically build and publish Docker images to Github Packages Docker Image Repository. This action builds and publishes the Docker image using the `buildx` Docker buildchain. `buildx` has built-in support for building containers for multiple platforms. This action uses the latest published `ros:humble` image on DockerHub. For more information on Docker, see [here](docker#robot-operating-system-container). For more information on multiplatform support, see [here](#multiplatform-support).

## REST API Server Docker Image Action
Github Actions is used to automatically build and publish Docker images to Github Packages Docker Image Repository. This action builds and publishes the Docker image using the `buildx` Docker buildchain. `buildx` has built-in support for building containers for multiple platforms. This action uses the latest published `uxa-90_ros_packages` image on this project's Github Packages Docker Image Repository. For more information on Docker, see [here](docker#rest-api-container). For more information on multiplatform support, see [here](#multiplatform-support).

---

## Multiplatform Support
Leveraging the power of the Docker build tool `buildx`, this project's Docker containers are automatically built for multiple platforms.

### Why Multiplatform?
Most desktop systems these days run on CPUs using the `amd64` architecture. As such, most of this project's development occur on systems using this architecture. However, our project plans to run our project's codebase on a Raspberry Pi, which uses the `arm64` CPU architecture, complicating our development and our Docker image build chain. By leveraging `buildx`, Github Actions can build a container for both `amd64` and `arm64` through architecture translation, making native Docker images for each architecture. These separate Docker images are then published to Github Packages Docker Image Repository, and linked together with a manafest file specifying that these Docker images are platform specfic versions of an image. 

For example, when pulling the latest API Server image using `docker pull ghcr.io/4850-red/api-ts:main`, Docker will choose the latest image marked with the host's CPU architecture.