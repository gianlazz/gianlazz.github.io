---
permalink: "/blog/:title/"
layout: post
author: ''
title: 'LXD/LXC, Docker & Microservices: Sharing Physical Compute Resources'
date: 2018-07-15 00:00:00 +0000
excerpt: Looking for a solution to share usb peripherals with containerized microservices
image: "/uploads/2018/07/16/419.png"

---
### Premise:

While setting up my own Raspberry Pi cluster that I'm orchestrating with Docker Swarm I've been wondering how I could interface with USB peripherals and the like with my docker container microservices. Why would someone want to do this? Well for my desired use cases I would like to be able to build custom servers, interfaces and programatic interactions with sensors or computing devices not standard on a traditional server or single board computer like the raspberry pi.

Some examples of the exciting external hardware peripherals that I want to develop with are:

Movidius Compute Stick Deep Learning ASIC

Software Defined Radio

Alternative wireless protocol devices for IOT

##### Glossary:

* Container
* VM
* Docker
* LXD
* LXC
* Microservices

##### Resources: