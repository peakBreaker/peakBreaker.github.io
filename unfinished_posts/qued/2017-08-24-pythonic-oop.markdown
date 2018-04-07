---
layout: post
title: "Pythonic Object Oriented Programming"
subtitle: "A short post about some of the features in python, and how to write pythonic"
date: 2017-08-24
category: Samples
author: Anders
tags: Python Software OOP
finished: false
---

# Pythonic classes

I was talking with someone a few days ago about pythonic object oriented programming.  The challange was to create a class which, in instantiating of an object, would instantiate an object as a belonging to the object itself.  In this case he mentioned the use of running a routine in the __init__ method to instantiate another object, as an attribute to the instantiated object.  Like instantiating a person, which owns a dog.  Note here then that the dog is not the child object of the person, like if the person has a *speak()* method, it would make little sense for the dog to have this method aswell, but it makes sense that the dog is an attribute of ther person - say *person.dog.name* would return the name of the persons dog.

I meant that doing this in the init method is not pythonic, as python has the \@classmethod.  Using this we can instantiate the person with a dog like this: person.with_dog() - and we have the added alternative of just instantiating the person itself, without a dog.

So i came up with this code, which i believe is pythonic:

{% highlight python %}
  "Just a program to test some object oriented programming in a pythonic way"
  import json
  
  
  class Dog():
  	"Dog class, pass in string for name when instantiating"
    def __init__(self, name):
  		self.name = name
  		self.timesBarked = 0
  	def bark(self):
  		print "wouf wouf"
  		self.timesBarked += 1
  		return "Times barked: " + str(self.timesBarked)
  
  
  class Person():
  	"Class for a person, pass in string for name when instantiating"
  	def \_\_init\_\_(self, name, dog=None):
  		self.name = name
  		self.dog = dog
  
  	\@classmethod
  	def with_dog(cls, \*\*kw):
  		"Class method to instantiate person with a dog, pass in dogName string"
  		# First we instantiate the doggy
  		dog = Dog(kw.get('dogName', 'defaultDogName'))
  		# Next instantiate person
  		person = cls(kw.get('personName', 'defaultPersonName'), dog)
  		# Finally return the person
  		return person
  
  	\@property
  	def serialize(self):
  		selfdict = {"name": self.name, "dogName" : self.dog.name if self.dog is not None else "None"}
  		return json.dumps(selfdict)
  
  	def \_\_str\_\_(self):
  		if self.dog is not None:
  			return """Hello, I am a person and my name is %s, \
  						and I have a dog named %s!""" % \
  						(self.name, self.dog.name)
  		else:
  			return """Hello, I am a person and my name is %s, \
  			 			and I have no dog :(""" % self.name
  
  
  # We can instantiate person from classmethod
  person1 = Person.with_dog(personName="Runar", dogName="Trofast")
  # Or alone
  person2 = Person("Tore")
  print person1
  print person2
  print person1.dog.bark()
  print person1.dog.bark()
  # Or get person as json
  print person2.serialize
{% endhighlight %}

Note here the use of decorators (property and classmethods), Keyword arguments(\*\*kw) and dundermethods.  Using features like these are what makes python so powerful indeed, as the instantiation and use of these classes makes it look more like english than code.  I really love making readable pythonic code <3

Hope you enjoyed this post!
