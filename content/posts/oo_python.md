---
title: "Object Oriented Python?"
date: 2013-09-05T22:24:46-07:00
draft: false
images:
tags: [python, programming, coding, object oriented, object, oo]
---
> Revitilizing very old post from the past. Of course, my thinking has changed since then, but its always fun to open a time capsule.

Most people I have spoken to about python do not believe in the object oriented capabilities of python. Python does not require you to always create a class like Java or C# but it is a language that is inherently object oriented. Like we say that __“In linux everything is a file”__, in python, everything is an object. Even functions are objects and can be passed around. Python decorators pass around functions but that will be an article for some other time (and maybe a long one as well).  

Python follows the __Verb__ method of programming. The two ways of programming verb vs noun are explained beautifully [here](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html). But let me brief it for you. Suppose the task is to take out the garbage, in the verb world you would do something like this
```
Get up from the couch.
Take the garbage out.
Dump it.
Walk back.
Plop back on the couch.
```

But in certain programming world __"Noun is god"__ and you would have to do something like this.
```java
cv = CouchWakeUpper( Person)
gw = GarbageWalker(cv)
dc = Dumper(gw)
wb = WalkBacker(dc)
Plopper(person)
```
or something similar, but you get the point. This is explained much better in the above link. I am only trying to convey the point. The noun form is not bad, but it takes away the natural flow a program should have which are verbs. Python, according to its BDL (Benevolent Dictator for Life) Guido Van Rossum gives maximum importance to readability of code and hence follows the __Verb__ way of programming and that is what I enjoy the most about python. 

## Objects
I can’t start an article called __OO Python__ and not tell about some technical aspects of python’s object oriented programming. An example class in python would be

```python
class Admin:
	def display(self, name):
		print “Hello, World” + str(name)
```

here the class __Admin__ has a member function called ‘display’ which takes an argument ‘self’ that corresponds to ‘this’ keyword in Java and is used to access all member variables. ‘self’ has to be passed to all functions in a class that are going to be called outside the class i.e by the objects. 

A way to call the above class would be 

```python
>>>objA = Admin()
>>>objA.display(“ Nani”)
```

The output would be 
```
Hello, World Nani
```
The call can be visualized as
```python
Admin.display(objA, “Nani”)
```
hence the ‘self’ keyword is used.

## Inheritance

Python supports simple inheritance and also multiple inheritance. The class definition with simple inheritance would look something like this.

```python
class DerivedClass( BaseClassName):
	→ member functions 
	→ member variables
```

Python also supports multiple inheritance and the syntax is 
```python
class DeriveClass( Base1, Base2, Base3):
	→ member functions 
	→ member variables
```
member variables are created and called using 

```python
self.variableName = something
```

