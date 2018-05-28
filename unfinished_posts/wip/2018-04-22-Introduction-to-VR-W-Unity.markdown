---
layout: post
title: "VR in Unity3D - feat. I-chih"
date: 2018-04-20
author: Anders
category: XR
tags: VR OculusRift
finished: false
img: covers/ichih-cover.JPG
---
*Just a heads up dear reader - My posts have two parts, the first part is some personal story and the second part is purely about technology and code*

*-- If youre here just for code snippets, then scroll down --*

# This is I-chih

![I-chih]({{site.baseurl}}/assets/img/blog/ichihvr/sc.jpg)

She is very concerned about the environment, and rightfully so - its an important issue. We first met back in 2017 at a clothe swapping party - back then it was after I opened a zero waste grocery store in Bergen, and I really needed some pants. We got along very well - she is always smiling and she is very nice. She is also an exchange student taking her masters degree in graphics design here in Bergen, but before we get into that lets fast forward to January 2018.

![Global Game Jam Team]({{site.baseurl}}/assets/img/ggj.jpg)

I attend Global Game Jam, which is a global 48h weekend session to create a game, with Kjetil, one of my friends from south Norway where I took by bachelors.  Together with him and Peer who we met there, we created a 2D platformer in Unity called Echo. Ill surely write a more detailed post at a later point about attending GGJ. Anyway, I-chih took note of that I wasn't completely useless in Unity3D and asked my help with her masters project, which concerned creating scenes in Unity3D with VR integration using Oculus Rift.

It sounded awesome, I didn't own a VR headset and always wanted to see how its like making stuff for VR, so I said yes to help her out. Basically what I said yes to was to help her integrate her models and animations from Cinema4D - a 3D modeling and animation program - to Unity3D, write scripts to activate the animations whenever the player looked at the models, and to integrate Oculus Rift with the project aswell as letting the player teleport around the scenes to look around at the world. It was actually pretty fun, and here are the end results:

<div class="responsive_iframe">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/4jgxrPBn9s0" frameborder="0" allowfullscreen></iframe>
</div>

## What Ive learned  :: Code and tech

Now I never intended to work much on Unity3D or blender or modelling or these kinds of things.  I just happen to do it for fun, and I think its really great for expression.  Even though my main work is about embedded systems, writing about 500 lines of code for device drivers can be off putting for even seasoned engineers, while these kinds of VR, modelling and graphical things are fun and cool to show off.

Anyway aside from the digression, Ive gotten into a few things about how to integrate VR with unity projects. I was suprised at how simple it is to convert existing projects into VR in Unity3D, and indeed Unity3D is great at this - making it easy on the developers (looking aside from Unity's horrible sense of version control - both semantic and rolling releases, whats that about?).  My main takeaways from doing this project was the following:

- Using OVR (Oculus VR) Utilities
- Using the lovely animator controller
- Using the manager pattern (ish) in Unity3D

Lets look into each individually:

### Using OVR Utilites

To get started with using Oculus with Unity3D, one installs the OVR utilities. Indeed the guide (and documentation in general) from Unity is very good for doing this.  Download the utilities as a unitypackage [here](https://developer.oculus.com/documentation/unity/latest/concepts/unity-utilities-overview/) and import it to your project. Make sure your unity version is compatible with the OVR utilities.

**Using Unity with Oculus touch controllers** was pretty straight forward.  Make sure the OVR Manager is in the scene and you should have access to the input methods

**Using OVR with UI** was a bit of a challenge.  The assignment was to be able to answer a quiz, built with Unity3Ds UI tools, in Oculus VR. To solve it, I followed [this guide](https://developer.oculus.com/blog/unitys-ui-system-in-vr/) to the letter - a bit tricky.  It worked but ..

**A quite frustrating issue** we ran into when porting from normal UI on the screen to OVR was the player clicked a button to answer a quiz question.  The next question would automatically be answered on the same spot that the previous question was answered.  At first I thought this was due to the player holding the button down for too long or that the UI switched to the next question too fast.  I applied a delay in order to wait for a second before showing the next question:

```
// Added for the time delay
public void Wait(float seconds, Action action)
{
    StartCoroutine(_wait(seconds, action));
}
IEnumerator _wait(float time, Action callback)
{
    yield return new WaitForSeconds(time);
    callback();
}

(...)

// Call the 1 second wait
Wait(1, () => {
              ShowQuestion();
          });
```

Note that in Unity3D you have to use coroutines in order to get time delays, since normal function execution is locked to frames (e.g. calling from void Update(){...}).

This fix didn't work.  After analyzing the issue closer, I still couldn't find the root cause.  In order to not waste more time on the issue, I figured I would create a guard statement to check the time between answers - if the time was shorter than *n* secs since last answer, then the following answer would be ignored.  This worked great, the code was slick aswell, and had us moving forward in no time:

```
// Guard statement to omit issue with question jumping
if (Time.time - timeElapsedQuestion < 2.0f)
    return;
timeElapsedQuestion = Time.time;
```

### The animator components and Unity3D Animation stack

To get animations working and to be able to alter them through the scripting system, unity provides the animator controller which is very slick for handling animations. Even though code is itself very powerful for many things, sometimes using node editors can make the system much easier to represent and self document. Since animation is indeed a very visual thing, node editors are often very useful for handling them - for example one of the most popular add-ons for blender is the node editor for animation handling.

Basically the requirement was to activate the animations of animated objects after a short delay after the player looked at them.  So I did the following:

```
bool ObjectIsVisible(Vector3 targetPoint) {
        Camera MainCam = gameObject.GetComponent<CameraSwitcher>().MainCamera;
        Vector3 screenPoint = MainCam.WorldToViewportPoint(targetPoint);

        if (screenPoint.z > 0 && screenPoint.x > 0 && screenPoint.x < 1 && screenPoint.y > 0 && screenPoint.y < 1)
            return true;
        else
            return false;
    }

    // Update is called once per frame
    void Update()
    {
        for (int i = 0; i < AnimObjects.Length; i++) // Loop through the objects
        {
            /* Get the data on the object */
            _animObject = AnimObjects[i];
            _animController = _animObject.GetComponent<Animator>();
            _curr_animAmount = _animController.GetFloat("AnimParam");

            if (ObjectIsVisible(_animObject.transform.GetChild(0).position))
            { // If object is visible
                _animController.SetFloat("AnimParam",
                    ( _curr_animAmount < 5 ? _curr_animAmount + animationIncrementer : _curr_animAmount ) // Then increment animation
                  );
            } else { // Object invisible
                _animController.SetFloat("AnimParam",
                    ( _curr_animAmount > 0 ? _curr_animAmount - animationIncrementer : _curr_animAmount ) // Then decrement animation
                  );
            }
        }
    }
```

So in short this code will
1. Iterate through all objects which we will be animating (we get the objects by using a tag like so: `GameObject.FindGameObjectWithTag("AnimObject");`)
2. Check if the object is visible
3. Increment the animation amount float up to 5 every frame the player is looking at object
4. If player is not looking at object, we will decrement the animation amount

### Unity3D Manager pattern

There is a recurring pattern in Unity to have manager scripts to handle management of a scene, or at least as far as Ive seen. Basically this means that there are game objects in a scene which does not render or anything like that, they just have scripts attached to them in order to handle various utility tasks.  Now this may or may not be an official pattern, and it may be a some what self evident way of structuring an object oriented setup such as a Unity game.  In the tree view, it may look something like this:

// Screenshot from Unity3D

For the project, part of the requirements was also to give the player the ability to "teleport" or switch between scenes.  This requirement was solved using this code in a manager called CameraSwitcher:

```
/*
cameras is an array of Camera objects.  We can get all cameras in the scene at start
by calling the following code:

cameras = Camera.allCameras;

Next we can use the SetCameraActive function with an index to enable a given camera
*/
public void SetCameraActive(int _cameraIndex) {
        for (int i = 0; i < cameras.Length; i++)
        {
            cameras[i].gameObject.GetComponent<AudioListener>().enabled = false;
            cameras[i].enabled = false;
        }
        cameras[_cameraIndex].gameObject.GetComponent<AudioListener>().enabled = false;
        cameras[_cameraIndex].enabled = true;
        MainCamera = cameras[_cameraIndex];
        Debug.Log("Main camera is now" + MainCamera);
    }
```
