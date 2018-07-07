---
permalink: "/blog/:title/"
layout: post
author: ''
title: Setting Up A Lazztech Private Cloud With A Kubernetes Raspberry Pi Cluster
date: 2018-06-27 00:00:00 +0000
excerpt: Raspberry Pi Cloud w/ Docker & Kubernetes
image: "/uploads/2018/07/01/20180701_130708.jpg"
---
\[WIP POST BEING USED AS REFERENCE FOR NOTES\]

Objective ELI5: I want to run and control my code from anywhere and learn how to set it up myself.

Services like Azure and other cloud offerings are so frequently such a high abstraction over what actually is going on that it can leave a user wondering what all is involved and how can someone setup a relatively reliable private "Cloud" of their own?

Lets assume that by Cloud, we just mean a system architecture above just individual server hosting on a single machine by allowing for dynamic horizontal scaling of computing instances across cluster of different computers providing system failure redundancy. This also orchestrates more easy utilization of computing resources by interconnecting them and allowing for self managing of execution across the machines.

 1. FLASH RASPBIAN LITE
 2. cd /Volumes/boot && touch ssh && cd .. && diskutil unmount /boot
 3. Install sd card, ethernet and power to the pi to boot it up
 4. ifconfig | grep broadcast && arp -a
 5. sudo ssh pi@192.168.0.6
 6. sudo raspi-config > Network Options > N1 Hostname > raspberrypi1

    THEN, Advanced Options > Memory Split > 16

    THEN, Change User Passsword > Finish > Reboot
 7. sudo ssh pi@192.168.0.6
 8. sudo curl -sSL get.docker.com | sh
 9. sudo usermod pi -aG docker
10. SIGN OUT OF SSH AFTER THIS AND BACK IN TO SSH TO ENABLE TO RUN AS ROOT

    type "exit" then hit enter
11. sudo ssh pi@192.168.0.6
12. DISABLE SWAP FOR KUBERNETES TO RUN PROPERLY

    sudo su

    dphys-swapfile swapoff

    dphys-swapfile uninstall

    update-rc.d dphys-swapfile remove

    sudo nano /boot/cmdline

        cgroup_enable=cpuset cgroup_enable=memory
        
        ctrl + X
        
        yes
        
        yes

    exit

    sudo ssh pi@192.168.0.6
13. INSTALL KUBERNETES

    curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add - && \\

        echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list && \\
        
        sudo apt-get update -q && \\
        
        sudo apt-get install -qy kubeadm

Looks like you'll need to downgrade docker to get this working:

sudo apt-get install -y docker-ce=18.04.0\~ce\~3-0\~raspbian --allow-downgrades

Then you should be able to get sudo kubeadm init --token-ttl=0 working

cgroup_memory missing issue:

![alt text](/uploads/2018/07/07/Screenshot_20180703-094001_Chrome.jpg "Logo Title Text 1")

[https://github.com/moby/moby/issues/35587](https://github.com/moby/moby/issues/35587 "https://github.com/moby/moby/issues/35587")

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

[https://chrisshort.net/my-raspberry-pi-kubernetes-cluster/](https://chrisshort.net/my-raspberry-pi-kubernetes-cluster/ "https://chrisshort.net/my-raspberry-pi-kubernetes-cluster/")

[https://gist.github.com/alexellis/fdbc90de7691a1b9edb545c17da2d975](https://gist.github.com/alexellis/fdbc90de7691a1b9edb545c17da2d975 "https://gist.github.com/alexellis/fdbc90de7691a1b9edb545c17da2d975")

[https://github.com/rak8s/rak8s](https://github.com/rak8s/rak8s "https://github.com/rak8s/rak8s")

[rak8s.io: Stand up a Raspberry Pi based Kubernetes cluster with Ansible](https://rak8s.io "https://rak8s.io")

[Ansible playbooks for setting up a Kubernetes Raspberry Pi 3 cluster github.com](https://github.com/Project31/ansible-kubernetes-openshift-pi3 "https://github.com/Project31/ansible-kubernetes-openshift-pi3")

Other interesting links:

[https://blog.alexellis.io/gpio-on-swarm/](https://blog.alexellis.io/gpio-on-swarm/ "https://blog.alexellis.io/gpio-on-swarm/")

Automate the build of the image to flash onto the raspberry pi with HashiCorp's Packer tool

[https://www.packer.io](https://www.packer.io "https://www.packer.io")

[https://grafana.com](https://www.packer.io "https://www.packer.io")

[https://www.ebay.com/p/Mikrotik-Hap-Lite-RouterBoard-Rb941-2nd-Wireless-N-4xport-Router-RouterOS-L4/1442141958?iid=173237597174&chn=ps](https://www.ebay.com/p/Mikrotik-Hap-Lite-RouterBoard-Rb941-2nd-Wireless-N-4xport-Router-RouterOS-L4/1442141958?iid=173237597174&chn=ps "https://www.ebay.com/p/Mikrotik-Hap-Lite-RouterBoard-Rb941-2nd-Wireless-N-4xport-Router-RouterOS-L4/1442141958?iid=173237597174&chn=ps")

[https://www.hootoo.com/hootoo-tripmate-ht-tm05-wireless-router.html](https://www.hootoo.com/hootoo-tripmate-ht-tm05-wireless-router.html "https://www.hootoo.com/hootoo-tripmate-ht-tm05-wireless-router.html")