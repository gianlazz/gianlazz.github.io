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