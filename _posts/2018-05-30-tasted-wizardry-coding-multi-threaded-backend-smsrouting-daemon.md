---
permalink: "/blog/:title/"
layout: post
author: Gian
title: 'Coding Multi Threaded Backend Inbound Sms Routing Daemon For HackathonHandler.com '
date: 2018-05-30 00:00:00 +0000
excerpt: HackathonHandler.com's inbound sms processing queue for client team SignalR
  updates
image: "/uploads/2018/05/31/MultiThreadedSmsQueueProcessingDaemon.png"
---
The feeling of elation was palpable as I sent an Sms response to my HackathonHandler.com site and saw it immediately light up a break-point in my code to denote a positive, request, response match.

This was the first time I'd ever written multi threaded code, along with a robust set of back-end layers, transient real time dynamic client JS code being executed and orchestrated by a C# domain layer. The rich web front end to bridge the gaps of the given technologies I had to work with really polished it off nicely.

The challenge I'd been presented with in making the HackathonHandler.com site and experience was to create the most friction-less experience. It was to create a natural ongoing interactive user experience from the moment they were registered into the Hackathon event. All this mind you had to be in accordance with tasteful privacy considerations. For example I wanted the most empowering experience for the event attendees. I'd decided this was to be able to request the assistance of whichever resource they saw most fit. For this I needed to ask as little of the students and empower them through the technology as much as possible.

I accomplished this with pre-generated team login pins that would enable them to prompt an experienced technology mentor of their choice by sms, where as upon them entering their pre-generated pin they would enable the real time server client response updates though a combination of SignalR, C# backend logic, and client JS/CSS & Html technologies.

For more about HackathonHandler, feel free to reach out to Gian Lazzarini though this site or any other google searched modality.

Looking forward to deploying it at this CodeDay EastSide hosted at T-Mobile, June 2-3 2018 and seeing what lessons come from it .