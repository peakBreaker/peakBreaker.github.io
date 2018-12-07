---
layout: post
title: "GoLang in Data Engineering"
date: 2018-12-05
author: peakbreaker
category: Data Engineering
tags: javascript web frontend
finished: true
---

*From my personal notes*

## Getting started with Golang as a DE tool

Data Engineering is pretty much what it sounds like - engineering systems to
handle data. I find that Golang is a really great tool for this application, as
it is reliable, handles concurrency well and is a simple tool.

### Arch install

My system is based on arch, so what follows is the procedure of including and
handling goland as a dependency in my system

{% highlight bash %}

$ pacman -S go godep

{% endhighlight %}

After these installs, the $GOPATH should be set to its default `$HOME/go`

### Vim integration

Vim is my editor, so I would naturally want golang integrated well here.
[vim-go](https://github.com/fatih/vim-go) seems to be the most popular plugin
at the moment, so I'll use that. Follow the install instructions based on your
plugin manager or whatever you use in the readme.

In addition...

So finally, **TL;DR**, we add the following to our .vimrc.

{% highlight vimscript %}

Plug 'fatih/vim-go', { 'do': ':GoUpdateBinaries' }

{% endhighlight %}



### GoDep

Godep puts libraries and modules in $GOPATH/src/github.com/<myapp>/vendor and
handler go dependencies for each project

## GoLang development pattern & workflow

<!-- Go into pkg, go and testing -->

## 
