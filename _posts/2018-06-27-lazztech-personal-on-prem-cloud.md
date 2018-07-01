---
permalink: "/blog/:title/"
layout: post
author: ''
title: Setting Up A Lazztech Private Cloud With A Kubernetes Raspberry Pi Cluster
date: 2018-06-27 00:00:00 +0000
excerpt: Raspberry Pi Cloud w/ Docker, Kubernetes & Openfaas
image: "/uploads/2018/06/28/20180627_225110.jpg"
---
[https://howchoo.com/g/ndg2mtbmnmn/how-to-install-raspbian-stretch-on-the-raspberry-pi](https://howchoo.com/g/ndg2mtbmnmn/how-to-install-raspbian-stretch-on-the-raspberry-pi "https://howchoo.com/g/ndg2mtbmnmn/how-to-install-raspbian-stretch-on-the-raspberry-pi")

[https://howchoo.com/g/ote0ywmzywj/how-to-enable-ssh-on-raspbian-without-a-screen](https://howchoo.com/g/ote0ywmzywj/how-to-enable-ssh-on-raspbian-without-a-screen "https://howchoo.com/g/ote0ywmzywj/how-to-enable-ssh-on-raspbian-without-a-screen")

[https://howchoo.com/g/mgi3mdnlnjq/how-to-log-in-to-a-raspberry-pi-via-ssh](https://howchoo.com/g/mgi3mdnlnjq/how-to-log-in-to-a-raspberry-pi-via-ssh "https://howchoo.com/g/mgi3mdnlnjq/how-to-log-in-to-a-raspberry-pi-via-ssh")

\`\`\`ifconfig | grep broadcast\`\`\`

\`\`\`arp -a\`\`\`

[https://blog.alexellis.io/your-serverless-raspberry-pi-cluster/](https://blog.alexellis.io/your-serverless-raspberry-pi-cluster/ "https://blog.alexellis.io/your-serverless-raspberry-pi-cluster/")

[https://gist.github.com/alexellis/fdbc90de7691a1b9edb545c17da2d975](https://gist.github.com/alexellis/fdbc90de7691a1b9edb545c17da2d975 "Kubernetes on pi gist by Alexis ")

cloud flare ddns with code to turn their dns into ddns

nopi

[How To using vpn + no-ip ddns](https://www.youtube.com/watch?v=gcCCJnzKBRs "https://www.youtube.com/watch?v=gcCCJnzKBRs")

[http://www.pivpn.io](http://www.pivpn.io "http://www.pivpn.io")

[OpenVPN Server raspberry pi /w PiVPN](https://www.youtube.com/watch?v=WA7QTM9hovQ "OpenVPN Server raspberry pi /w PiVPN")

[https://github.com/oznu/docker-cloudflare-ddns](https://github.com/oznu/docker-cloudflare-ddns "https://github.com/oznu/docker-cloudflare-ddns")

[https://nickjanetakis.com/blog/the-3-biggest-wins-when-using-alpine-as-a-base-docker-image](https://nickjanetakis.com/blog/the-3-biggest-wins-when-using-alpine-as-a-base-docker-image "https://nickjanetakis.com/blog/the-3-biggest-wins-when-using-alpine-as-a-base-docker-image")

[https://www.hanselman.com/blog/HowToBuildAKubernetesClusterWithARMRaspberryPiThenRunNETCoreOnOpenFaas.aspx](https://www.hanselman.com/blog/HowToBuildAKubernetesClusterWithARMRaspberryPiThenRunNETCoreOnOpenFaas.aspx "https://www.hanselman.com/blog/HowToBuildAKubernetesClusterWithARMRaspberryPiThenRunNETCoreOnOpenFaas.aspx")

I'll be foregoing the popular route of the installing OpenFaas to setup server less functions deployment. While I do appreciate the appeal of the server-less architecture as a cloud deployment concept. It is a bit too high of an abstraction than I'm interested or practiced at working on at this time and would likely serve to add more thought and complexity initially than I'm interested in investing in at this time. Also while I really appreciate the work that they're doing on the OpenFaas project and it seems to have a fairly active developer community it just doesn't have enough development behind if for me to want the added potential overhead of investing in it. I'll definitely be watching to see how the project develops over the coming years.

Of course I can always add it in later if I so please and actually at the time of writing this article did already load it up and check it out myself for a brief moment.