---
permalink: "/blog/:title/"
layout: post
author: Gian Lazzarini
title: C# MongoDb Driver 2.6.0 Nuget Causing System.Runtime Reference Issues & Solution
date: 2018-04-30 00:00:00 +0000
excerpt: ''
image: "/uploads/2018/05/01/Capture.PNG"
---
This one really had me stumped and was a very frustrating wast of time. I tried everything I could from installing the NuGet package for each missing system.runtime or related dependency for which there were referencing issues, to adding various versions of said dependencies in the .config file and nothing worked...

This issue all would only arise when I referenced another class library layer in my solution for which I had a concrete implementation of a MongoDb repository pattern. I was referencing this from an ASP.NET MVC project for which I'd done a number of modifications to, most namely upgrading to Bootstrap 4. I was unable to replicate these run time errors when I referenced my MongoDb project by a fresh ASP.NET MVC project so I'm still not sure about what that was.

However if you've run into this problem like me from installing the .NET MongoDb driver version 2.6.0 from NuGet then try deleting all of those NuGet packages and re-install a lower version until you get it working. As of writing this I'm having success with version 2.4.4.

From what I read online it sounds like there was a very similar if not the same issue at some point causing these kind of dependency referencing issues with older version for which people also at times solved it by changing to a lower version.