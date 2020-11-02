---
title: "Lab d) & e) : Deploying and Implementing a Mobile Application"
description: Roll a Ball to Mobile.
date: 2020-11-02
draft: false
tags: [labs,Unity,Mobile]
---

## Deploying Mobile App

To deploy my mobile App, I followed the lab tutorial but encountered a problem when I needed to build the app : 

>*Unable to update the SDK. Please run the SDK Manager manually to make sure you have the latest set of tools and the required platforms installed. See console log for details.*

Well this one was a quick fix, I had to reinstall Unity's tools and it worked but I came across another error while trying to build: 

>*Error building Player because scripts have compile errors in the editor*

This was once again a quick fix : When I imported my asset of skybox, there was a script in it which was using UnityEditor which impeded the building process. Simply erasing this file allowed me to build !
   
Since my phone has a broken usb port I was not able to plug and test and decided to build straight away.

{{< videofig mp4="/FirstMobileBuild.mp4" loop=true autoplay=true caption="Yeah, it works" >}}

## Implementing Accelerometer 

Following the lab tutorial I did not have any problems, except the fact that I found it hard juggling between two builds versions in the same script... Like I'm not entirely sure that my script can support transitions from Windows Build to Android but it works for Android. Also it was not comfortable for me to have to build, send, install each and every time I wanted to test my game so I believe I could have been more efficient.

Either way here's the [final version](https://github.com/celol/AndroidRollABall) ! :smile:

{{< videofig mp4="/FinalMobileBuild.mp4" loop=true autoplay=true caption="Yeah, it works also" >}}