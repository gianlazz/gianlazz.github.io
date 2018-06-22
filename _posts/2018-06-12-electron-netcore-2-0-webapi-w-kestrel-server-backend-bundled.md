---
permalink: "/blog/:title/"
layout: post
author: ''
title: Electron & .NETCORE 2.0 WebApi w/ Kestrel Server Backend Bundled
date: 2018-06-11 00:00:00 +0000
excerpt: ''
image: "/uploads/2018/06/12/Screen Shot 2018-06-11 at 9.23.18 PM.png"
---
First of all I'd like to give credit to this article I followed along with to get up to speed: [https://scotch.io/@rui/how-to-build-a-cross-platform-desktop-application-with-electron-and-net-core](https://scotch.io/@rui/how-to-build-a-cross-platform-desktop-application-with-electron-and-net-core "https://scotch.io/@rui/how-to-build-a-cross-platform-desktop-application-with-electron-and-net-core")

Original projects GitHub: [https://github.com/figueiredorui/cross-platform-desktop](https://github.com/figueiredorui/cross-platform-desktop "https://github.com/figueiredorui/cross-platform-desktop")

However I'm making this post as that article was a bit out of date with .Net Core 1.1 and so I ran into and solved some issues as I went along and got it working with some minor changes in steps while using .Net Core 2.0

I ended up making a parallel folder and project to the original tutorials outlined "api" project made from \`\`\`dotnet new console\`\`\` and instead in .Net Core 2.0 project named "webapi", used \`\`\`dotnet new webapi\`\`\` and copied over the differing methods from the original tutorials Program.cs which had both a Program class and the Startup class in it.

I then also changed the references in the main.js for the electron file where it's grabbing the binary from using the "api" to "webapi"

If you have issues consult with my GitHub repo and if need be I you can follow along with the commit history as I tried to illustrate my problem solving in the commit messages.

[https://github.com/gianlazz/ElectronWithDotNetCoreServerTutorial](https://github.com/gianlazz/ElectronWithDotNetCoreServerTutorial "https://github.com/gianlazz/ElectronWithDotNetCoreServerTutorial")