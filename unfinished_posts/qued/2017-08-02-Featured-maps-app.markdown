---
layout: post
title: "Featured pt1: Webapp using apis"
subtitle: "A google maps and api based application"
date: 2017-08-02
category: Featured
author: Anders
tags: Featured maps mvvm knockoutjs
finished: false
---

## Google maps, apis and mvvm
Hello and welcome to this first featured post. My goal with these posts is just to reflect over these spikesolutions and featured works which I will occasionally post on this site.

My first featured application I showcase here features my maps app. My goal of the app was to fully utilize the features of the google maps api, and use this api in junction with at least one other api. I ended up with connecting the maps together with foursquare to get details about a location, such a phone numbers and websites, and use disqus to enable a comment thread on the site.

You can find the sourcecode for the application at [GitHub](https://github.com/peakbreaker/ScriptyJav) and a running demo at [gh-pages]({{site.url}}/ScriptyJav). Below I am writing abit about what Challanges I faced during development and what Ive learned.

#### Technology
For this webapp I am basing myself on the following technologies
- Use of JavaScript and web technology
- Mobile first responsive design
- Use of the KnockoutJS MVVM framework
- Use of JavaScript APIs and webservices

### Challanges
**The first noteable challenge** in developing an application like this is the utilization the designpattern suitable for our application. I took note of how important and useful it is to actually first get a correct vision of what the application is supposed to do, and have a strong understanding of the chosen design pattern used.

**The second major challenge** for me was in the case when I wrote code which creates a working application, but lacked the features needed to complete the requirements and vision of the project.  This hacked together code ran, but it needed refactoring in order to be efficient to work with. Complexity is the software engineers muse.

### Solutions
**First**, remembering to take use of the MVVM design pattern and design architecture can make the entire operation of developing the application a lot easier. Sticking to the designpattern and main architecture of the application made the flow of the code alot more predictable and less confusing. My idea here is not to commend the MVVM pattern, but rather to commend consistency in the patterns of development. Consistent code brings about context, which makes understanding the code alot easier.

**Secondly**, communication through the code is extremely important.  When I started learning to code, I used comments quite frequently, however now I only find it useful in explaining the general steps of a long procedure of code. I am now a much firmer believer in code which is self documenting, and I believe the greatest principles behind this lies in understanding the *Signal-to-Noise* ratio of the code. Particularly here, choosing correct names, formatting/whitespace and shorthands are our tools in making great code. I believe this is about taste, and developers have to cultivate good taste in code.

Example with my for loop shorthand

**Thirdly**, I learned that trying seeing code in different abstraction layers is very useful. This is why we write functions, and I believe that understanding abstraction is the key to designing great subroutines, coroutines, methods and functions.

Example with my makecontent function

To put it in another way - Abstraction is about layering, and code should keep to its correct layer. Code which is at a wrong layer will make understanding the program harder.
