---
permalink: "/blog/:title/"
layout: post
author: ''
title: Infrastructure As Code Configuration Management
date: 2018-06-29 00:00:00 +0000
excerpt: Consistent, Manageable Devops provisioning for Lazztech Private Cloud
image: ''
---
My first exposure to infrastructure as code configuration management tools and the powerful utility they offer in managing deployment was during a conversation I had with Tyler Menezes, the Executive Director of SRND as I was asking him how he was able to manage all of SRND's online web presence mostly by himself along with his already busy life.

He introduced me to puppet, chef, terraform and gave me a quick demo on how he's scripted out the entire SRND web deployment as code he can check into git to maintain consistency across deployments. He explained to me that this gave him freedom to deploy all of SRND's web presence quickly to the provider of his choice in minutes.

This is incredibly powerful and offers the convenience of being able to do things like deploy to the cloud hosting environment that may be sponsoring SRND & CodeDays at that time.

I was hooked and saw places that this sort of work flow could improve development projects all around. Once I really got my head wrapped around it I've been surprised that not everyone is doing it yet. I can't tell you how many hours I've spent installing and setting up build dependencies only to get myself further and further invested in an increasingly more rigid and difficult to reproduce build environment...

I want to move beyond that as much as possible.

{::nomarkdown}<div align="center"><script type="text/javascript" src="https://ssl.gstatic.com/trends_nrtr/1480_RC02/embed_loader.js"></script> <script type="text/javascript"> trends.embed.renderExploreWidget("TIMESERIES", {"comparisonItem":[{"keyword":"Ansible","geo":"US","time":"2017-06-30 2018-06-30"},{"keyword":"Puppet","geo":"US","time":"2017-06-30 2018-06-30"},{"keyword":"Chef","geo":"US","time":"2017-06-30 2018-06-30"},{"keyword":"Salt","geo":"US","time":"2017-06-30 2018-06-30"},{"keyword":"Terraform","geo":"US","time":"2017-06-30 2018-06-30"}],"category":32,"property":""}, {"exploreQuery":"cat=32&geo=US&q=Ansible,Puppet,Chef,Salt,Terraform&date=today 12-m,today 12-m,today 12-m,today 12-m,today 12-m","guestPath":"https://trends.google.com:443/trends/embed/"}); </script></div>{:/}  

Ansible and the Lazztech Private Cloud

[https://chrisshort.net/my-raspberry-pi-kubernetes-cluster/](https://chrisshort.net/my-raspberry-pi-kubernetes-cluster/ "https://chrisshort.net/my-raspberry-pi-kubernetes-cluster/")

Plus NASA uses Ansible to provision their environment on cloud.

[https://www.ansible.com/blog/nasa-automation](https://www.ansible.com/blog/nasa-automation "https://www.ansible.com/blog/nasa-automation")

<div align="center">
<iframe width="560" height="315" src="[https://www.youtube.com/embed/OmRxKQHtDbY](https://www.youtube.com/embed/OmRxKQHtDbY "https://www.youtube.com/embed/OmRxKQHtDbY")" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
</div>

<div align="center"><script type="text/javascript" src="[https://ssl.gstatic.com/trends_nrtr/1480_RC02/embed_loader.js](https://ssl.gstatic.com/trends_nrtr/1480_RC02/embed_loader.js "https://ssl.gstatic.com/trends_nrtr/1480_RC02/embed_loader.js")"></script> <script type="text/javascript"> trends.embed.renderExploreWidget("TIMESERIES", {"comparisonItem":\[{"keyword":"Ansible","geo":"US","time":"2017-06-30 2018-06-30"},{"keyword":"Puppet","geo":"US","time":"2017-06-30 2018-06-30"},{"keyword":"Chef","geo":"US","time":"2017-06-30 2018-06-30"},{"keyword":"Salt","geo":"US","time":"2017-06-30 2018-06-30"},{"keyword":"Terraform","geo":"US","time":"2017-06-30 2018-06-30"}\],"category":32,"property":""}, {"exploreQuery":"cat=32&geo=US&q=Ansible,Puppet,Chef,Salt,Terraform&date=today 12-m,today 12-m,today 12-m,today 12-m,today 12-m","guestPath":"[https://trends.google.com:443/trends/embed/](https://trends.google.com:443/trends/embed/ "https://trends.google.com:443/trends/embed/")"}); </script></div>