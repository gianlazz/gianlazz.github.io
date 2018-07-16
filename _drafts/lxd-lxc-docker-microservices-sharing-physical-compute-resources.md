---
permalink: "/blog/:title/"
layout: post
author: ''
title: LXD/LXC, Docker, Microservices & Sharing External Physical Compute & Networking
  Peripherals
date: 2018-07-15 00:00:00 +0000
excerpt: Looking for a solution to share usb peripherals with containerized microservices
image: "/uploads/2018/07/16/419.png"

---
### Premise:

While setting up my own Raspberry Pi cluster that I'm orchestrating with Docker Swarm I've been wondering how I could interface with USB peripherals and the like with my docker container microservices. Why would someone want to do this? Well for my desired use cases I would like to be able to build custom servers, interfaces and programatic interactions with sensors or computing devices not standard on a traditional server or single board computer like the raspberry pi.

Some examples of the exciting external hardware peripherals that I want to develop with are:

* Intel Movidius Neural Compute Stick:

  The NCS is an application specific integrated circuit(ASIC) capable of running Caffe convolutional neural network(CNN) models with performance comparable to a graphics card however it only consumes 1 watt of power. As Intel states, the Movidius NCS is “the world’s first self-contained AI accelerator in a USB format,” This is part of an industry push to move more computing to the "edge" [https://www.ge.com/digital/blog/what-edge-computing](https://www.ge.com/digital/blog/what-edge-computing "https://www.ge.com/digital/blog/what-edge-computing")
* Software Defined Radio(SDR)
* Alternative wireless protocol devices for IOT like, zigbee, LoRa or BLE

##### Glossary:

* Container: A container is an sandboxed development environment that shares the host kernel and can ease the consistency between various development environments and deployment as everything needed to run will be kept in the container. Changes can also easily be tracked in git allowing for software best practices(DevOps)
* VM: A virtualized instance of an entire computer and it's operating system. This is also a way of managing predictable deployment and development environments however it insures much more computational overhead to run and can be slow to boot up.
* LXC: LinuX Containers (LXC) is an operating system-level virtualization method for running multiple isolated Linux systems (containers) on a single control host (LXC host)
* Docker: Is a container based LXC focused on application delivery however is poorly suited for interfacing with hardware as that is sandboxed out of the containers it is a fantastic solution for application delivery and interfacing via the network like a REST Api server
* LXD: 
* Monoliths: Typically composed of N-Tier, Service Oriented architecture where everything must be redeployed to make a change to any part of the code. These model has advantages however it can make scaling difficult and isn't well suited for distributed computing clusters.
* Microservices: 

##### Resources:

[https://unix.stackexchange.com/questions/254956/what-is-the-difference-between-docker-lxd-and-lxc](https://unix.stackexchange.com/questions/254956/what-is-the-difference-between-docker-lxd-and-lxc "https://unix.stackexchange.com/questions/254956/what-is-the-difference-between-docker-lxd-and-lxc")

LXC/LXD Deep Dive : [https://www.youtube.com/watch?v=GYppOyCbM68](https://www.youtube.com/watch?v=GYppOyCbM68 "https://www.youtube.com/watch?v=GYppOyCbM68")

Introducing the Intel Movidius Neural Compute Stick : [https://www.youtube.com/watch?v=sRYs0dZLXkw](https://www.youtube.com/watch?v=sRYs0dZLXkw "https://www.youtube.com/watch?v=sRYs0dZLXkw")