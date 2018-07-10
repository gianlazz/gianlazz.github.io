---
permalink: "/blog/:title/"
layout: post
author: ''
title: Raspberry Pi Usb Webcam IP Camera Server
date: 2018-07-08 00:00:00 +0000
excerpt: ''
image: "/uploads/2018/07/10/Screen Shot 2018-07-09 at 11.23.48 PM.png"
---
#### Hardware & Software

Logitech USB Webcam

Raspberry Pi

Rasbian Light

#### Resources

[http://www.instructables.com/id/Raspberry-Pi-remote-webcam/](http://www.instructables.com/id/Raspberry-Pi-remote-webcam/ "http://www.instructables.com/id/Raspberry-Pi-remote-webcam/")

[https://motion-project.github.io/motion_config.html](https://motion-project.github.io/motion_config.html "https://motion-project.github.io/motion_config.html")

[http://www.instructables.com/id/How-to-Make-Raspberry-Pi-Webcam-Server-and-Stream-/](http://www.instructables.com/id/How-to-Make-Raspberry-Pi-Webcam-Server-and-Stream-/ "http://www.instructables.com/id/How-to-Make-Raspberry-Pi-Webcam-Server-and-Stream-/")

[https://pimylifeup.com/raspberry-pi-webcam-server/](https://pimylifeup.com/raspberry-pi-webcam-server/ "https://pimylifeup.com/raspberry-pi-webcam-server/")

[https://www.raspberrypi.org/forums/viewtopic.php?t=125597](https://www.raspberrypi.org/forums/viewtopic.php?t=125597 "https://www.raspberrypi.org/forums/viewtopic.php?t=125597")

[https://www.youtube.com/watch?v=4rfGc8WM0vk](https://www.youtube.com/watch?v=4rfGc8WM0vk "https://www.youtube.com/watch?v=4rfGc8WM0vk")

[https://sourceforge.net/projects/mjpg-streamer/](https://sourceforge.net/projects/mjpg-streamer/ "https://sourceforge.net/projects/mjpg-streamer/")

#### Finding motion snapshots and http serving them

`cd /var/lib/motion`

`ls`

`python -m SimpleHTTPServer`

`http://ipofyourrapsberrypi:8000/`