---
layout: post
title: "Basics of blender - Part 1"
subtitle: "Overview, models & texturing"
date: 2017-07-25
author: Anders
category: Blender
tags: Blender 3D cgi
finished: false
---

## Ah, blender
Blender is an open source 3D computer graphics software for creating pretty much whatever you can imagine in 3D.
![Blender logo]({{site.url}}/assets/blender-logo.png)

It is a pretty awesome piece of software, entirely free, with a great amount of features for creating professional level content.  In the hands of a trained person the results can be quite astonishing. Just take a look at this short film made by the blender foundation itself:

<iframe width="560" height="315" src="https://www.youtube.com/embed/aqz-KE-bpKQ" frameborder="0" allowfullscreen></iframe>

So one can do some pretty awesome stuff in this software!

### Thats cool, but..
Youre not going to be a professional 3D artist. Or if you are, you probably want to use some of paid software with more cutting edge features. So is there then any reason to spend time learning to use Blender?

Well yeah - First of all blender is fully featured as a 3D graphics software. You can get a job just working with blender, and in many cases it can do more than the crazy expensive software. Blender is a quite hard software to use, with a very sharp learning curve, but I believe this grants the software more strength as it is hard because of great multitude of features and that it is driven by hotkeys. And when you start to feel confident with the software, it can be a lot of fun.

In addition, if you are just a casual user, you can greatly empower your main occupation by using and learning blender. It is free and accessible, and will give you the features you need to help you create 3D graphics for your applications. This last point is where for example my application lies.

As an engineer you will find yourself making models using CAD software from time to time. Or you design systems which requires a lot of learning for other people to comprehend. Your goal will always be to work with other people and sell forward your product, and therefore you must be able to show off your work. Knowing blender for 3d graphics together with inkscape for vectorgraphics and gimp for photoshop can give you a very powerful stack for displaying your work.  At a later time i might do a post on the use of blender together with other tools to create something cool.

### Interesting, can we get our hands dirty now?

Yes! Time for the fun part - Lets look at some basics of blender!  Currently I am working on / have a blender library repository on github where I keep/will keep models, materials etc. and personal notes on the use of the software - So you can take a look there.

[Anders' personal blender library](https://github.com/Andurshurrdurr/lib_blender)

To create a textured model there are basically 3 things we need to do:
- Create the mesh (modelling)
- Mapping our mesh and applying textures
- Adding our materials

**Good stuff, lets begin**
Allright, lets try to make this low poly tombstone to just get a grip of the basics:

![Blender render]({{site.url}}/assets/blender1-1.png)

#### Model:
1. We can use the default cube when opening a new scene, or create a new cube by pressing **Shift-A** -> mesh -> cube
2. To edit the cube object we enter edit mode by selecting the cube and pressing **Tab**
3. At the lower part of the window you see this (see below) which will let you select vertex/edge/face ![Select vertex/edge/face]({{site.url}}/assets/blender1-2.png)
4. To make the model we select different vertecies/edges and faces and use **G** to move them about and **S** to scale the selections, and extrude new elements with **E** - You just have to try about things till you have what looks good.
5. Finally you should have something that looks like this
![Final mesh]({{site.url}}/assets/blender1-3.png)

#### Texturing & materials:

1. First we gotta UV map our model. If you dont know what this is, google it and read abit on the wiki page for the subject. The first part of this in blender is to mark seams. Select edges (in edit mode), hit **CTRL-E** and mark seam. Seams are where our unwrapper cannot stitch our UV map.
2. After getting our seams correct we can unwrap our model.  Select all vertecies/edges/faces on our model with **A** and hit **U** and -> Unwrap
3. Bring up a pane with with UV/Image editor, add an image ![Adding a new texture image]({{site.url}}/assets/blender1-4.png)
4. One would typically check and alter the UV map with a checkerpattern now, but we will skip this step in this tut
5. We will now add our material. Make sure you are using cycles render as the rendering engine (set this in upper right corner), go to the materials tab (see below), and create a new material. On the material, make sure you are using nodes. ![Materials tab]({{site.url}}/assets/blender1-5.png)
6. Enter node editor, add a Image Texture node with **SHIFT-A** -> Texture -> Image Texture and put the output to a diffuse shader node which has its output to the Material output. ![Node Editor]({{site.url}}/assets/blender1-6.png)
7. We can now enter texture mode and start texturing our model! ![Texture painting]({{site.url}}/assets/blender1-7.png)

Now make the model like you want it

### Outro

This is the absolute minimum you need to get started with making a textured model in blender. I hope to get into more advanced topics at a later time and the details of what makes blender so powerful. Though I believe in the process of first making something ugly that works first, and doing optimization later.

Hope you enjoyed this tut, I know I did. See you later! :)

- Anders
