---
permalink: "/blog/:title/"
layout: post
author: ''
title: 'LXD/LXC, Docker & Microservices: Sharing External Physical Compute & Networking
  Peripherals'
date: 2018-07-15 00:00:00 +0000
excerpt: Looking for a solution to share usb peripherals with containerized microservices
image: "/uploads/2018/07/16/419.png"

---
### Premise:

While setting up my own Raspberry Pi cluster that I'm orchestrating with Docker Swarm I've been wondering how I could interface with USB peripherals and the like with my docker container microservices. Why would someone want to do this? Well for my desired use cases I would like to be able to build custom servers, interfaces and programatic interactions with sensors or computing devices not standard on a traditional server or single board computer like the raspberry pi.

Some examples of the exciting external hardware peripherals that I want to develop with are:

Movidius Compute Stick Deep Learning ASIC

![](/uploads/2018/07/16/5a058ff088603f150a87aa37-640x640.jpg)

\(SDL) Software Defined Radio

Alternative wireless protocol devices for IOT

##### Glossary:

* Container
* VM: 
* LXC: LinuX Containers (LXC) is an operating system-level virtualization method for running multiple isolated Linux systems (containers) on a single control host (LXC host)
* Docker: Is a container based LXC focused on application delivery however is poorly suited for interfacing with hardware as that is sandboxed out of the containers it is a fantastic solution for application delivery and interfacing via the network like a REST Api server
* LXD
* Microservices

##### Resources:

[https://unix.stackexchange.com/questions/254956/what-is-the-difference-between-docker-lxd-and-lxc](https://unix.stackexchange.com/questions/254956/what-is-the-difference-between-docker-lxd-and-lxc "https://unix.stackexchange.com/questions/254956/what-is-the-difference-between-docker-lxd-and-lxc")

LXC/LXD Deep Dive : [https://www.youtube.com/watch?v=GYppOyCbM68](https://www.youtube.com/watch?v=GYppOyCbM68 "https://www.youtube.com/watch?v=GYppOyCbM68")

Introducing the Intel Movidius Neural Compute Stick : [https://www.youtube.com/watch?v=sRYs0dZLXkw](https://www.youtube.com/watch?v=sRYs0dZLXkw "https://www.youtube.com/watch?v=sRYs0dZLXkw")