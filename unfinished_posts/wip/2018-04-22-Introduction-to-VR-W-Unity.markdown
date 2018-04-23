---
layout: post
title: "VR in Unity3D - feat. I-chih"
date: 2018-04-20
author: Anders
category: XR
tags: VR OculusRift
finished: false
img:
---

# This is I-chih

// Picture of I-chih

She is very concerned about the environment, and rightfully so - its an important issue. We first met back in 2017 at a clothe swapping party - back then it was after I opened a zero waste grocery store in Bergen, and I really needed some pants. We got along very well - she is always smiling and she is very nice. She is also an exchange student taking her masters degree in graphics design here in Bergen, but before we get into that lets fast forward to January 2018.

![Global Game Jam Team]({{site.baseurl}}/assets/img/ggj.jpg)

I attend Global Game Jam, which is a global 48h weekend session to create a game, with Kjetil, one of my friends from south Norway where I took by bachelors.  Together with him and Peer who we met there, we created a 2D platformer in Unity called Echo. Ill surely write a more detailed post at a later point about attending GGJ. Anyway, I-chih took note of that I wasn't completely useless in Unity3D and asked my help with her masters project, which concerned creating scenes in Unity3D with VR integration using Oculus Rift.

It sounded awesome, I didn't own a VR headset and always wanted to see how its like making stuff for VR, so I said yes to help her out. Basically what I said yes to was to help her integrate her models and animations from Cinema4D - a 3D modeling and animation program - to Unity3D, write scripts to activate the animations whenever the player looked at the models, and to integrate Oculus Rift with the project aswell as letting the player teleport around the scenes to look around at the world. It was actually pretty fun, and here are the end results:

// Video of results

## What Ive learned

Now I never intended to work much on Unity3D or blender or modelling or these kinds of things.  I just happen to do it for fun, and I think its really great for expression.  Even though my main work is about embedded systems, writing about 500 lines of code for device drivers can be off putting for even seasoned engineers, while these kinds of VR, modelling and graphical things are fun and cool to show off.

Anyway aside from the digression, Ive gotten into a few things about how to integrate VR with unity projects. I was suprised at how simple it is to convert existing projects into VR in Unity3D, and indeed Unity3D is great at this - making it easy on the developers (looking aside from Unity's horrible sense of version control - both semantic and rolling releases, whats that about?).  My main takeaways from doing this project was the following:

- Using OVR (Oculus VR) Utilities
- Using the lovely animator controller
- Using the manager pattern (ish) in Unity3D

Lets look into each individually:

### Using OVR Utilites

### The animator components and Unity3D Animation stack

### Unity3D Manager pattern
