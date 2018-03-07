---
permalink: "/blog/:title/"
layout: post
author: ''
title: 'Exploring Angular + GraphQL: Hackathon Mentor Manager App'
date: 2018-03-06 00:00:00 +0000
excerpt: ''
image: ''
---
This project is a collaborative effort between myself and my buddy [Sameez Charania](https://www.linkedin.com/in/sameez) who thought of the idea. From it we will be exploring full stack SPA development with Angular and GraphQL.

## Premise

Sameez and I attend and have long time involvement with [CodeDay.org](http://codeday.org) hackathons. We'd been discussing ideas of how to streamline the process of running them. From this Idea Sameez approached me with the concept of making an app to help the student attendees get linked up with the mentors at the event.

The hope was that this way anyone at any skill level or focus could look through a list of mentors, see which were currently busy or available and pick to request them based off of the mentors profile of strengths and interests.

So here's a list of proposed features and tech stack:

* Angular Single Page Web App front end
* Angular PrimeNG for UI component library
* Graph.cool GraphQL as the back end for persisting the mentors information
* Twillio SMS API support to hail the mentors

To keep it simple we were thinking of only having the accounts for the Mentors and pre-configuring them. The students will all then look from the same public queue of mentors on a first come first serve basis. The mentors that are busy will be greyed out and others will have a button to select them. After selecting them the users will then be able to request them buy giving a brief description, their phone number for contact, along with there general location at the venue so the mentor can find them, this will all then be sent to the mentor to notify them that they're being summoned.