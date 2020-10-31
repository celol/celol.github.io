---
title: "Lab c) : Build your first Unity3D Application"
description: Building my Roll a Ball version.
date: 2020-09-17
draft: false
tags: [labs,Unity,Application]
---
## Choosing a project and following its tutorial.

For this lab, I decided to follow the [Roll a Ball tutorial](https://learn.unity.com/project/roll-a-ball?language=en) from Unity.
This tutorial alongside the one we got during the lab were enough to get the basics down. And I did not have any problems whatsoever. But I wanted my implementation to be a bit different.

## Making my game unique.

To give my game a bit of IP Paris spiciness, I added a few things.

First of all I want to change the skybox because otherwise my game would look boring and tasteless (it will look cooler in VR too :wink:). To do so here are all the steps required :

1. Go to the asset store and pick the fanciest looking skybox material you'd like
2. Import your new asset
3. Go to Window -> Rendering -> Lighting Settings 
4. Go to the Skybox Material menu and change it to your newly imported asset
5. Congrats, now your game will look a lot cleaner !

Next, I don't want my player to only bounce on walls and be able to get away with it. To prevent this, I enbale the isTrigger option on my walls and add a code that will restart the game if the player collides with them. I need not to forget to add a relevant tag for the death walls.

{{< highlight cs "linenos=table,linenostart=1" >}}
if (other.gameObject.CompareTag("Wall"))
{
    SceneManager.LoadScene(SceneManager.GetActiveScene().name);
}

{{< / highlight >}}

To make my game a bit more competitive I added a timer so that each and everyone can compete to complete it the fastest. Since I'm going to modify the value of the WinningText, we need to change a bit the initial code of the tutorial.
We are then adding a timer that will use the update function to be incremented and round it. When we collect everything, we display the final time.
See full code : 

{{< highlight cs "linenos=table,linenostart=1" >}}
if (other.gameObject.CompareTag("Wall"))
{
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.InputSystem;
using TMPro;
using System;
using UnityEngine.SceneManagement;

public class PlayerController : MonoBehaviour
{
    public float speed = 0;
    public TextMeshProUGUI countText;
    public TextMeshProUGUI winTextObject;
    private Rigidbody rb;

    private float movementX;
    private float movementY;


    private int count;
    private int remaining;

    public float timeStart = 0;
    private int finalTime;
    private float timer = 0f;
    public TextMeshProUGUI Timer;


    // Start is called before the first frame update
    void Start()
    {
        rb = GetComponent<Rigidbody>();
        count = 0;
        

        SetCountText();

        winTextObject.gameObject.SetActive(false);

    }



    private void OnMove(InputValue movementValue)
    {
        Vector2 movementVector = movementValue.Get<Vector2>();

        movementX = movementVector.x;
        movementY = movementVector.y;
    }

    private void FixedUpdate()
    {
        Vector3 movement = new Vector3(movementX, 0.0f, movementY);

        rb.AddForce(movement * speed);
        timeStart += Time.deltaTime;
        Timer.text = "Timer : " + Mathf.Round(timeStart).ToString() + " seconds";
    }

    private void OnTriggerEnter(Collider other)
    {
        if (other.gameObject.CompareTag("PickUp"))
        {
            other.gameObject.SetActive(false);

            // Add one to the score variable 'count'
            count = count + 1;
            

            // Run the 'SetCountText()' function (see below)
            SetCountText();
        }

        if (other.gameObject.CompareTag("Wall"))
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name);
        }
    }

    private void SetCountText()
    {
        remaining = 12 - count;
        countText.text = remaining.ToString() + " Collectibles remaining" ;

        if (count >= 12)
        {
            // Set the text value of your 'winText'
            finalTime = (int)Mathf.Round(timeStart);
            winTextObject.text = "Congrats it took you " + finalTime.ToString() + " seconds to collect them all. Try again to be even faster ! :)";
            winTextObject.gameObject.SetActive(true);
        }
    }

}
}

{{< / highlight >}}


And here you have it, an "improved" version of the basic Roll A Ball. Let's see how it goes :

{{< videofig mp4="/Gameplay.mp4" loop=true autoplay=true caption="Don't think I'm bad, I'm just showing off the respawn system..." >}}
