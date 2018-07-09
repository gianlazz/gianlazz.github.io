---
permalink: "/blog/:title/"
layout: post
author: ''
title: Setting Up A Lazztech Private Cloud With Docker Swarm Raspberry Pi Cluster
date: 2018-07-08 00:00:00 +0000
excerpt: An introduction into maintaining and provisioning a distributed server cluster
image: "/uploads/2018/07/09/picocluster3s.jpg"
---
\[WIP POST BEING USED AS REFERENCE FOR NOTES\]

Objective ELI5: I want to run and control my code from anywhere and learn how to set it up myself.

Services like Azure and other cloud offerings are so frequently such a high abstraction over what actually is going on that it can leave a user wondering what all is involved and how can someone setup a relatively reliable private "Cloud" of their own?

Lets assume that by Cloud, we just mean a system architecture above just individual server hosting on a single machine by allowing for dynamic horizontal scaling of computing instances across cluster of different computers providing system failure redundancy. This also orchestrates more easy utilization of computing resources by interconnecting them and allowing for self managing of execution across the machines.

#### Desired Use-cases:

* Host more of my own code deployments from websites to rest apis for custom code
* Manage IOT Devices such as the ESP8266 and host a HomeAsssistant server
* Learn about Devops, docker, cluster computing, Infrastructure as code etc
* To have a reliable hardware interface to write REST Api servers to interface against any hardware peripherals I may want in my own personal cloud
* Host a private VPN server
* Host a server to update Cloudflare's dns to hack together my own free DDNS
* Move away from depending on highly abstracted cloud hosting services like Azure and learn the Devops provisioning skills to avoid the slippery slope of vendor lock in that comes from relying on those high level hosting abstractions
* Learn about more about "Serverless" cloud architecture with open source tools like OpenFaas

#### Docker

#### Choosing Docker Swarm vs. Kubernetes Docker Cluster Management