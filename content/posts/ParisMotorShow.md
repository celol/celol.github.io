---
title: "MRTK : Paris Motor Show"
description: My approach for the Paris Motor Show Project using MRTK.
date: 2021-01-31
draft: false
tags: [Project, MRTK]
---

## Introduction

Basically for this project, I tried to get and put to use everything that I had learned throughout the entire course.

The obvious firsts steps were to correctly reconfigure the MRTK profiles and builds settings for the scene, since I had corruption troubles for the app and had to start over and redo the first tutorials for MRTK.

## Setting up

Before getting too much into technicalities, it's important to setup our scene. We are at the Paris Motor show and we want the users to at least get that feeling a little bit.

To achieve such a thing the asset store is going to be our best ally. We'll get some car assets and some decorum for our scene.

Light it up a little bit so it looks better and here we have it !

{{< figure src="/Showroow.PNG" title="Looks decent ?" >}}

I've put some spots above the car to make them look a bit better.

## Welcome message

A simple dialog that we set unactive on click looks like it does the trick, thanks to MRTK doc. I just needed one button so I deleted the others and went for a single press button after the description was read. 
  

I was very insightful in the description so that you knew what you were about to witness exactly.


{{< figure src="/Dialog.PNG" title="Onto the next step" >}}

## Choosing car of interest 

I decided to keep things simple and downloaded a 4 cars pack from the unity asset store. What I want now is a menu with four different options that will stick with the user so that he can change his mind whenever he pleases.

To do that I use a near menu that is first disabled and that is going to be activated on click by the previous button of the welcome message. I delete the pin component and make the menu automatically follow the player.

I update the four choices based on the four cars that I have available. Some tweaking is required for the menu in order to prevent him from bothering the user.

I add a title with a a 3D object and we have ourselves a menu !

{{< figure src="/Menu.PNG" title="Onto the next step" >}}

## Navigation

I want the user to have the same type of chevron that we have seen in the tutorials, so I keep kind of the same structure but decide to keep a permanent indicator for the user so that he's not lost at any time. An arrow is always there !

To navigate, I use some on click event inside my buttons to activate / deactivate the right chevrons. I was puzzled for a long time because I thought that button clicked was enough to proceed but it's not the case : OnClick event is mandatory !

For some better insights I've added a button to display more information when a car is selected !

{{< figure src="/onclick.PNG" title="Onto the next step" >}}

## Changing Materials

To change the colour of the cars, you first need to be interested in that car and thus to have selected it into our car of interest menu. Once it is done, 3 buttons will appear proposing you to choose a simple colour for your car.

## Evaluation

If you hit the quit button of your preferences menu, you will be asked to rate the app ! :)

## Demo

Here's the full demo of my app that you can find on my [github](https://github.com/celol/SalonDeLauto) : 


{{< videofig mp4="/DEMOAUTO.mp4" loop=true autoplay=true caption="Looks kinda cool ! :)" >}}
