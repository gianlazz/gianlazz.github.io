---
permalink: "/blog/:title/"
layout: post
author: ''
title: Setting Up A Lazztech Private Cloud With Docker Swarm Raspberry Pi Cluster
date: 2018-07-08 00:00:00 +0000
excerpt: An introduction into maintaining and provisioning a distributed server cluster
image: "/uploads/2018/07/18/36498620_2016258842021803_3678605842250203136_n.jpg"

---
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

#### Containerized Deployment & Docker

Everyone's moving more and more towards containerized deployment. This allows more scriptable, and predictable development environments and also makes deployment to any server that can host docker containers very straight forward. Contianerizing your projects also allow you to avoid conflicting dependency versions and ensure that things like path variables and such are always in the desired state by developing in a container.

You also can save money on licensing as docker uses your host OS and simply contains it's resources inside so you don't have to pay for a Windows license for every VM you simply pay for the host and have as many containers as you like.

#### Microservices Architecture vs Monoliths and Service Oriented Architecture

Another trend that has been in place now for a while that is largely being facilitated by the proliferation of containerized deployment is Microservices. This is something I would like to learn more about as my experience doing .NET Development has pretty much predominately been through the N-Tier / 3-Tier SOA Architecture that results in the traditional "Monoliths".

#### Choosing Docker Swarm vs. Kubernetes Docker Cluster Management

Running a distributed computer cluster where you want everything to work together and plan to deploy your work with containers requires a "Container Orchestrator" and the two most popular that also supports the raspberry pi's Arm architecture are Kubernetes and Docker Swarm.

I'll ultimately be ending up with Kubernetes as it has much more sophisticated however after a couple of weekend trying to get it setup and running into a myriad of dependency updates that had broken the tutorial I ended up with using Docker Swarm. I found setting up the Docker Swarm to be a largely painless process in comparison and honestly I think it's not a bad place for myself as beginner to start since ultimately I want to focus on actually building a deploying things and not to spend all of my time up front banging my head against Kubernetes.

By opting for docker swarm I'm able to grow my skillset and learn about docker along the way which will eventually make managing a more sophisticated Container Orchestrator like Kubernetes much more natural.

#### PicoCluster

I opted to purchase the Pico 3S from picocluster.com to house my raspberry pi cluster as I really appreciate the totally self contained enclosure requiring only one power outlet and one ethernet port into your modem due to the build in ethernet switch. This will make transporting the cluster much more easy if need be and hopefully encourage me to use and maintain as it'll be much less unwieldy than a wad of raspberry pi's, wires, psu, and ethernet switch to have to setup and hide.

#### Resources on setting up your own:

[https://howchoo.com/g/njy4zdm3mwy/how-to-run-a-raspberry-pi-cluster-with-docker-swarm](https://howchoo.com/g/njy4zdm3mwy/how-to-run-a-raspberry-pi-cluster-with-docker-swarm "https://howchoo.com/g/njy4zdm3mwy/how-to-run-a-raspberry-pi-cluster-with-docker-swarm")