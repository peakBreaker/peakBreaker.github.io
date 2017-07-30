---
layout: post
title: "Basics of web - Part 1: Web technology"
subtitle: "An introduction to a series on web technology"
date: 2017-07-21
author: Anders
category: webseries
tags: python flask web
finished: true
---

## Web is cool

Hello and welcome to this series on web development with python flask. I aim to go through web development from a software engineering viewpoint in this series, from a conceptual level to the actual running code. If you follow the series, I aim that you will need no technical knowlege from before to actually understand what we're doing. So put on your engineering hat and lets make and learn some awesome stuff! First out: Web

## Why is web cool?

Ever heard of the ".com bubble"? Yeah, it was basically a huge market crash in the late 90s because of the overhype of the internet. College kids were planning IPOs in their dorms, and investors threw money at anything with a website. It was the time where everyone could be an expert hacker by knowing XSS and SQL injection, or walk into a company saying "I know HTML tables" and get hired as a junior engineer on the spot. Good times indeed. Today? Not so much.

![One does not simply HTML tables]({{site.url}}/assets/html_tables_meme.png)

Why is this? Well today we hardly think about the value of the internet and web, because it has soked itself into our everyday life, but back in the 90s things like mobile phones, computers and that you could order stuff online was friggin sci-fi level stuff. And it is. We do not think about how amazing these technologies are today, but it is increasingly harder to imagine a world without webservices and magic websites which can serve you personalized, highly accurate data every day, or give you magical powers and interaction with the world. The capabilities and the vision of the internet as the neural net connecting humanity as a single brain is scarily awesome. So... stepping foot into web technology is today a bit more complex than before.

But fear not - We have Python.

## So what do we even mean by web?

Well web is basically what people think of as the internet (though its inaccurate). Think of URL and HTTP. It resides in the upper layers of the OSI stack, over the internet itself, and its purpose is to give you user friendly data. Woah, thats a lot of techy talk. We'll look into the specifics of the technology in later posts. For now, just think of the web as when you access a webpage like google. Web technology is (part of) what lets you do that.

## Lets set up a webserver

This is the best part of the blogpost

There is a million ways to set up a server, but due to the simplicity and readability of python and flask we will be using that throughout this series to illustrate each part of the technology. So enter flask!

![Python flask]({{ site.url }}/assets/flask.png)

First we install python, you can follow the instructions in this link:
https://wiki.python.org/moin/BeginnersGuide/Download

and use the python packagemanager pip to install pip:

$ pip install flask

{% highlight ruby %}

  from flask import Flask
  app = Flask(__name__)

  @app.route("/")
  def hello():
      return "Hello World!"

{% endhighlight %}

Congrats - You set up your first webserver! In the next post I will get deeper into the the technical terms before we move onto developing craazey fun features!
