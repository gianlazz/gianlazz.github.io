---
layout: post
permalink: "/blog/:title/"
title: Chrome Style Dev Tools On Mobile With Ionic (Eruda)
date: 2020-01-21 08:00:00 +0000
excerpt: Enable dev tools with Ionic on iOS and Android
image: "/uploads/2020/01/22/IMG_1640.jpg"
author: ''

---
I found myself wanting more debugging information while working on a personal Ionic 4 app. When something goes wrong I would like to be able to read the logs right then and there on app deployed to iOS.

I'm going to share with you how I used a project called [Eruda](https://github.com/liriliri/eruda "Eruda") to add a javascript based implementation of your common browser dev tools. This project allows you to have access to such information while viewing a page on mobile.

In my ionic app's root project directory I ran the following to set things up:

    npm install eruda --save

Then I created an angular service to enable the eruda dev tools from within the app:

    ionic g service debugger