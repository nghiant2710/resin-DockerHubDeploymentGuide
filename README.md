# Deployment Guide for Docker Images from Docker Hub

## Introduction

Resin.io offers you the flexibility to deploy your application from a custom <span style="color:red">Dockerfile</span> which allows you to define your own development environment. 

Freely constructing the environment gives you all the power but sometimes takes a lot of time to create a proper <span style="color:red">Dockerfile</span> for your application. Why not save your effort by utilising existing Docker images instead of building from scratch, Resin.io allows you to use Docker image from [Docker Hub](https://hub.docker.com/) which contains many repos of pre-built Docker image.

On [Docker Hub](https://hub.docker.com/), there are many Docker images for Resin.io supported devices with an installed OS and applications. You can find the Docker image satisfied with your specifications, point to this Docker image in your <span style="color:red">Dockerfile</span> and you have a configured environment for your application. This approach provides a fast and simple way for the deployment of application to Resin.io.

## Instructions

### Finding a Docker Image

To find a suitable Docker image for your devices, you can go to [Docker Hub](https://hub.docker.com/) and search with specific keywords related the device - e.g., rpi or raspbian for Docker images of Raspberry Pi.

Typically you will find 2 types of image:

* Docker image with installed OS and sofware which create a development environment for a platform or a programming language - e.g., Python, Java. This type of Docker image can save your time and effort on setting up the environment, just add your code and launch them on Resin.io.
* Docker image with installed OS and software which fully deploy an application or service - e.g., OwnCloud, MQTT Broker. This type of Docker image is ready to be deployed on Resin.io, you sometimes need to add some configurations to make it work properly.

### Using Docker Image from Docker Hub

To use the image from Docker Hub just simply put its name in the place of the base image for the container in your <span style="color:red">Dockerfile</span>. For example:

To use repo [key3/rpi-raspbian-python2.7-dev](https://registry.hub.docker.com/u/key3/rpi-raspbian-python2.7-dev/) on [Docker Hub](https://hub.docker.com/), we set the base image for <span style="color:red">Dockerfile</span> as:
<br>`FROM key3/rpi-raspbian-python2.7-dev`<br>
And we have the basis with raspbian OS, python 2.7 and development packages installed ready for deploying python projects. then we can just follow the instructions in [Dockerfile guide](http://docs.resin.io/#!/pages/dockerfile.md) to make Resin.io deploys the container to devices.

Let's take repo [comzone/rpi-owncloud6](https://registry.hub.docker.com/u/comzone/rpi-owncloud6/) as an example for using Docker image with fully installed application. We set the base image for <span style="color:red">Dockerfile</span> as:
<br>`FROM comzone/rpi-owncloud6`<br>
And add a command line to start [OwnCloud](http://owncloud.org/) service in <span style="color:red">start</span> file (see [Dockerfile guide](http://docs.resin.io/#!/pages/dockerfile.md) for more details on start file).
<br>`/usr/bin/supervisord`<br>
Then Resin.io can help you deploy OwnCloud 6 to devices fast and effortlessly (see details of this project in below section).

_Notice: some applications needs to be configured before starting_

## Example Projects

Here are some applications on Resin.io using Docker image from Docker Hub as examples for you:

1. [OwnCloud 6 on Resin.io](https://github.com/nghiant2710/Resin-Owncloud6)
This project based on a repo from Docker Hub: [comzone/rpi-owncloud6](https://registry.hub.docker.com/u/comzone/rpi-owncloud6/). Using Docker image with installed OwnCloud and adding a script to start the OwnCloud service then Resin.io can deploy OwnCloud 6 on your devices.

2. [Hello World with Go on Resin.io]()
This project is a simple example for using Docker image from Docker Hub: [cretzel/rpi-golang](https://registry.hub.docker.com/u/cretzel/rpi-golang/) to set up development environment for [Go](http://golang.org/) project.

3. [Hello World with Python on Resin.io]()
This project is a simple example for using Docker image from Docker Hub: [key3/rpi-raspbian-python2.7-dev](https://registry.hub.docker.com/u/key3/rpi-raspbian-python2.7-dev/) to set up environment for Python project.