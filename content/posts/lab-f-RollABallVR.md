---
title: "Lab f) : VR Roll-a-Ball Unity and course's feedback"
description: Roll a Ball to VR.
date: 2020-11-02
draft: false
tags: [labs,Unity,VR]
---

## A VR Implementation that became a failure.

Well, this is not the happiest I've been. I had kept the VR Lab as far away as I could from me but maybe I should have put more thought in it because it ended up as a complete failure but I still want to write a blogpost for it.

I had basically started the lab on Evry Campus on an Occulus Rift but switched to a Quest right after. 
I followed the advices from the lab, got the same importing errors for my Roll A Ball android package and I was happy. The problems started when I tried to debug my game using Occulus Link.

My scene looks something like this : 

{{< figure src="/Scene.PNG" title="Isn't it beautiful ?" >}}  

Basically, I had added a skybox, changed the material of my floor and added the roll a ball on the table. But I when I hit play in Occulus Link, this is what I end up with : 

{{< figure src="/OculusScreenshot1604263987.jpeg" title="Meh..." >}}  

Basically I was unable to have any VR interaction. I thought at first this was a package problem and I tried to uninstall & reinstall the VR packages required to make it run but it did not change anything. I reupdated Unity, Occulus and it didn't change either.
Since Carl is living with me, has the same PC and used the same headset I tried to copy the maneuvers he did to get it to work but it did not seem like it would work on my machine.
   
Then, I thought about the mobile implementation I did and realised that I had completed it without debugging available. So I decided to complete the lab, adding some music (Adding a component AudioSource to the OVRCameraRig does the trick I guess) and then I build the app without erros and using SideQuest I transferred it onto my headset. I only got a black screen at launch and nothing was happening...

You can find my project on my [GitHub](https://github.com/celol/RollABallVR)
## Why it didn't work ?

Well I bear the entire responsibility for the failure of this lab. I didn't give it as much time as I should have and I should have asked more questions earlier. My overall feeling about this lab is the fact that I never truly expected for a VR App to be so complicated to implement : there are numerous steps some that I had trouble understanding .
I believed that since VR was getting more and more popular, its implementation would be more simple but it was not the case.

## Conclusion / Feedback on the course.

{{< youtube IEe2pxiUKFE >}}

