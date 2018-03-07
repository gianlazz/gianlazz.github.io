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

#### Proposed features and tech stack:

* Angular Single Page Web App front end
* Angular PrimeNG for UI component library
* Graph.cool GraphQL as the back end for persisting the mentors information
* Twillio SMS API support to hail the mentors

To keep it simple we were thinking of only having the accounts for the Mentors and pre-configuring them. The students will all then look from the same public queue of mentors on a first come first serve basis. The mentors that are busy will be greyed out and others will have a button to select them. After selecting them the users will then be able to request them buy giving a brief description, their phone number for contact, along with there general location at the venue so the mentor can find them, this will all then be sent to the mentor to notify them that they're being summoned.

#### Tools, DevOps and Hosting:

* For collaboration we'll be using Github
* TravisCI.org for continuous integration
* We'll also be using TravisCI for continuous deployment from the master branch to a free Heroku vm for hosting
* And we'll be coding it all in VSCode

This tutorial will also assume that you're working on a Mac though the commands and tools should work well on other platforms with few changes

#### Step one Project initialization

Install Node.js which will include NPM for managing the packages.

[https://nodejs.org/en/](https://nodejs.org/en/ "https://nodejs.org/en/")

Install the Angular CLI in Terminal line with

    sudo npm install -g @angular/cli

Then create and initialize the new Angular project and all of it's dependencies

    ng new hackathon-manager

Change directories into your project with

    cd hackathon-manager

From there you can then locally serve you're newly create angular app

    ng serve --open

You can then close your app in the terminal by typing the shortcut control + c. After that install PrimeNG to your new angular app while still in it's directory with this command

    npm install primeng --save

Then initialize git

    git init

Go to GitHub and create a new repository. At that point it will be empty and you'll have to push the newly created Angular app from your computer to your GitHub repository.

Here's my repo:

[https://github.com/gianlazz/Hackathon-Manager](https://github.com/gianlazz/Hackathon-Manager "https://github.com/gianlazz/Hackathon-Manager")

When you initialize an angular project it automatically sets it up for git to track and ignore the correct files.

While still having you're terminal window open still with the directory pointed to your angular project run this command

    git remote add origin https://github.com/YOUR_USERNAME/YOUR-PROJECT-NAME.git

Stage your project files

    git add .

Commit

    git commit -m "first commit"

Then push your code

    git push -u origin master

#### Step two Continuous Integration setup

Create a free account on [https://travis-ci.org/](https://travis-ci.org/ "https://travis-ci.org/") with it configured to your GitHub account. From there find your repository for the new Angular app you just pushed and check it.

From there we'll need to do a bit more configuring.

Now is a good time to open up your project folder in vscode. From there you can easily create a new file which will be named:

    .travis.yml

The period at the beginning will make this file hidden by default from your file browser but on a Mac you can type CMD + SHIFT + . to be able to view them. Other wise you'll also be able to see it by default in vscode.

This file is going to serve as a configuration file that Travics-CI is going to look for in your repository so I knows how to build and deploy your project.

In the file you're going to paste:

    language: node_js
    node_js:
      - "7"
    sudo: true
    dist: trusty
    
    branches:
      only:
      - master
    
    before_script:
     - export CHROME_BIN=/usr/bin/google-chrome
     - export DISPLAY=:99.0
     - sh -e /etc/init.d/xvfb start
     - sudo apt-get update
     - sudo apt-get install -y libappindicator1 fonts-liberation
     - wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
     - sudo dpkg -i google-chrome*.deb
    
    script: 
      - ng test --watch false -cc
      - npm run e2e
      - ng build -bh "https://ahsanayaz.github.io/ng-traffic-ci/"
    
    deploy:
      provider: pages
      skip_cleanup: true
      github_token: $GITHUB_TOKEN # Set in travis-ci.org dashboard
      local_dir: dist
      on:
        branch: master