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

<div class="row"> <div class="6u"> I read through probably about a dozen different articles and half a dozen different videos documenting all the different varying approaches to setting up a rasberry pi distributed computing cluster with either Kubernetes or Docker Swarm.

<div markdown="1">

##### By the end I'd concluded that by far the best maintained tutorial documenting how to do this was this link here:

[alexellis/k8s-pi.md github gist](https://gist.github.com/alexellis/fdbc90de7691a1b9edb545c17da2d975 "https://gist.github.com/alexellis/fdbc90de7691a1b9edb545c17da2d975")

</div>

During the installation process to setup a Rasberry Pi distributed computing cluster with Kubernetes I ran into a number of issues caused by updates to dependencies from the tutorials I found. After banging my head against the problem for a while I ended up commenting and shortly later had replies from others that had run into the same problems.
</div>
<div class="6u">
<div align="center">
<img src="/uploads/2018/07/07/Screenshot_20180703-094001_Chrome.jpg" alt="Comment Screenshot" height="80%" width="80%">
</div>
</div>
</div>

Notice, YMMV as this is all very dependency version dependent and a few weeks, months or so in the future as new versions of all the dependencies are released the install and setup process may change wildly. 

Here's the installation dependencies I'm working with as of writing this post:

Installation and setup machine:

* MacBook Pro (13-inch, 2017, Four Thunderbolt 3 Ports)
* macOS High Sierra 10.13.3
* Hyperdrive Usb C Hub with Micro Sd card slot

Pi Cluster setup:

* 2x Raspberry Pi 3
* 1x 16gb Sandisk (SD cards are mismatched because that's what I had)
* 1x 32gb Sandisk
* 2018-06-27-raspbian-stretch-lite.img
* Rasbian is flashed with "Etcher" by resin.io
* Anker 6 Port USB PSU
* Maker sure Usb cables are high quality!
* Internet over ethernet directly into router switch ports

### Installation Steps

##### This also accounts for the dependency downgrades to fix the tutorial

 1. FLASH RASPBIAN LITE
 2. Eject and reinsert
 3. cd /Volumes/boot && touch ssh && cd .. && diskutil unmount /boot
 4. Install sd card, ethernet and power to the pi to boot it up
 5. ifconfig | grep broadcast && arp -a
 6. sudo ssh pi@192.168.0.6
    1. password: raspberry
 7. sudo nano /boot/cmdline.txt
    1. paste to the end: cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1
    2. ctrl+x
 8.  Change hostname
    1. sudo raspi-config > Network Options > N1 Hostname > raspberrypi1
    2. THEN, Advanced Options > Memory Split > 16
    3. THEN, Change User Passsword > Finish > Reboot
 9. Set a static IP address
    1. cat >> /etc/dhcpcd.conf
    2. `profile static_eth0
       static ip_address=192.168.0.100/24
       static routers=192.168.0.1
       static domain_name_servers=8.8.8.8`
    3. ctrl+d
10. sudo ssh pi@192.168.0.6
11. sudo curl -sSL get.docker.com | sh
12. sudo usermod pi -aG docker
13. Sign out and and back into ssh to enable docker user with admin
    1. type "exit" then hit enter
    2. sudo ssh pi@192.168.0.6
14. Disable swap for kubernetes

        sudo dphys-swapfile swapoff && \
          sudo dphys-swapfile uninstall && \
          sudo update-rc.d dphys-swapfile remove
15. Edit /boot/cmdline
    1. sudo`nano /boot/cmdline`
    2. past in: cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1
    3. ctrl+x
16. Sign out and back in
    1. exit
    2. sudo ssh pi@192.168.0.6
17. Install Kubernetes v1.9.7-00
    1. curl -s [https://packages.cloud.google.com/apt/doc/apt-key.gpg](https://packages.cloud.google.com/apt/doc/apt-key.gpg "https://packages.cloud.google.com/apt/doc/apt-key.gpg") | sudo apt-key add - && echo "deb [http://apt.kubernetes.io/](http://apt.kubernetes.io/ "http://apt.kubernetes.io/") kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list && sudo apt-get update -q && sudo apt-get install -qy kubelet=1.9.7-00 kubectl=1.9.7-00 kubeadm=1.9.7-00
18. Initialize Kubernetes(Can take up to 15 mins)
    1. sudo kubeadm init --token-ttl=0 --apiserver-advertise-address=192.168.0.100 --ignore-preflight-errors=ALL

INITIAL FAILED INSTALL STEPS HERE FOR NOTES WHILE UPDATING STEPS

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