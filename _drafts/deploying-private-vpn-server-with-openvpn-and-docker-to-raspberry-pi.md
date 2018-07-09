---
permalink: "/blog/:title/"
layout: post
author: ''
title: Deploying Private VPN Server with OpenVPN, DDNS & Docker to Raspberry Pi
date: 2018-07-08 00:00:00 +0000
excerpt: ''
image: "/uploads/2018/07/09/openvpn_logo.png"
---
In my previous post I talked about setting up my private cloud with a Raspberry Pi Cluster. 

#### Installation Resources

[https://blog.gorilla.moe/47/raspberry-pi-zero-w-openvpn-server-with-noip-dynamic-dns](https://blog.gorilla.moe/47/raspberry-pi-zero-w-openvpn-server-with-noip-dynamic-dns "https://blog.gorilla.moe/47/raspberry-pi-zero-w-openvpn-server-with-noip-dynamic-dns")

[https://gist.github.com/odarriba/2116b7a7ea38400b4fe32c3647c8291c](https://gist.github.com/odarriba/2116b7a7ea38400b4fe32c3647c8291c "https://gist.github.com/odarriba/2116b7a7ea38400b4fe32c3647c8291c")

#### Wireguard VPN Mention

[https://www.ckn.io/blog/2017/12/28/wireguard-vpn-portable-raspberry-pi-setup/](https://www.ckn.io/blog/2017/12/28/wireguard-vpn-portable-raspberry-pi-setup/ "https://www.ckn.io/blog/2017/12/28/wireguard-vpn-portable-raspberry-pi-setup/")

#### DDNS

Honestly I think the subject of DDNS justifies a post of it's own. This used to be pretty conclusively simple to setup back when DynDns offered free DDNS service however back in 2014 they ceased and it has been a little bit more complicated.

For experience I'll be using NoIP, a resource that seems to be popular enough and is referenced by a number of tutorial's I've looked including one I'm using now.

I'm also interested in setting up my own DDNS via a docker container script I could deploy to my cluster that would simply update Cloudflares free 1.1.1.1 dns service via there public api. I've actually found some resource below that I may just use for that purpose:

[https://github.com/oznu/docker-cloudflare-ddns](https://github.com/oznu/docker-cloudflare-ddns "https://github.com/oznu/docker-cloudflare-ddns")

[https://gist.github.com/lyoshenka/6257440](https://gist.github.com/lyoshenka/6257440 "https://gist.github.com/lyoshenka/6257440")

[https://scotthelme.co.uk/replacing-dyndns-cloudflare-ddns/](https://scotthelme.co.uk/replacing-dyndns-cloudflare-ddns/ "https://scotthelme.co.uk/replacing-dyndns-cloudflare-ddns/")

One could also rely on a service to update Cloudflares DNS for them like in this link:

[https://support.cloudflare.com/hc/en-us/articles/206142407-Using-DNS-O-Matic-dynamic-DNS-updates-with-Cloudflare-](https://support.cloudflare.com/hc/en-us/articles/206142407-Using-DNS-O-Matic-dynamic-DNS-updates-with-Cloudflare- "https://support.cloudflare.com/hc/en-us/articles/206142407-Using-DNS-O-Matic-dynamic-DNS-updates-with-Cloudflare-")

During my research I found this discussion helpful in considering my options too:

[https://community.spiceworks.com/topic/2004389-best-ddns-providers?page=2](https://community.spiceworks.com/topic/2004389-best-ddns-providers?page=2 "https://community.spiceworks.com/topic/2004389-best-ddns-providers?page=2")