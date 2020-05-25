---
title: "Some Little Known Things in Python"
date: 2013-08-08T22:25:25-07:00
draft: false
images:
tags: [python, quirks, coding, optimization]
---
> Revitilizing very old post from the past. Of course, my thinking has changed since then, but its always fun to open a time capsule.

This article came after a long hiatus from the previous one and I would like to apologize for that. I came across many neat things in python recently and am somewhat finding it overwhelming to master them all. Every time I learn something, there is something else that completely baffles me or at least intrigues me to solve problems differently.

Hopefully writing this article would be comforting of some sort. In this article I am going to document some little capabilities available to python users to help them in their day to day adventures. 

## Lambda Function

Python gives a powerful utility to create anonymous functions to users. These functions are not bound to any name (i.e they are anonymous, as already stated, by me :-P). Lambda functions are apparently well built into the core of python structure and support all possible optimizations and provide good performance. Let me just start off with an example so that my rants make sense.

```python
>>g = lambda x: x**2 # lambda function returns
>>
>>print g(8)
64
>>print g(5)
25
```

You can assign lambda functions to variables and they act as function names, but not exactly. Note that lambda function does not use any return statements explicitly, but they always have some expression that they return. 

Suppose you want a function that increments the number given to it by 2, 5 and 7. You can have 3 different functions or pass different arguments to them or you can use lambda functions like this

```python
>>def incrementor(n): return lambda x: x+n

>>two_incrementor = incrementor(2)
>>five_incrementor = incrementor(5)
>>seven_incrementor = incrementor(7)
>>print two_incrementor(10), five_incrementor(14), seven_incrementor(11)
12  19 18

#you can also chain them up like
>>print incrementor(11)(55)
66
```

One other really cool application I want to point out is that lambda functions can be used to operate as path joiners for different folders you might need in some configuration files. 

```python
>>import os
>>def joiner(basefolder): return lambda x: os.path.join(basefolder, x)
>>root_joiner = joiner(“/”)
>>home_joiner = joiner(“/home/usr”)
>>print root_joiner(“etc”)
/etc
>>print home_joiner(“code/sites”)
/home/usr/code/sites
>>print home_joiner(“../..”)
/home/usr/../..
```

Lambda functions would work awesome with python map, filter and reduce operations. But more on that later.

## Dictionaries as arguments to functions

In python you can send a dictionary to a function for all the arguments. This feature is like that gizmo you read about, you know it's expensive, you may not use it as well, but you want it. Now, after knowing about this feature, I may not use it, but I want it in all programming languages I use. 

Its amazing how well it is integrated in python. You can now organize your code even better and not worry about the order of the arguments at all and also write really good tests as well. Here is how you do it.

```python
def TVfunction( channel, volume):
	print “The channel is %s and the volume is %s”%channel, volume

argDict = {“channel”: “23”, “volume”: “45”}
TVfunction(**argDict)
```

The double '\*\*' does the trick of taking your dictionary and passing the required arguments to the function, in the order required.

## Arbitrarily Long Argument List

There are many instances where you don’t have a specific number of arguments that you want to pass to a function. So, you can send any number of arguments to a function by adding '\*' before an argument at the end of the argument list. The arguments will be given to you as a tuple and can be zero or more in number. There can be zero or more arguments before the variable argument, but none after. An example would be

If you want to send filenames to a function that deletes it, but you don’t know how many files you have to delete at the time of programming you can do something like this.

```python
def delete_files(basefolder, *arg):
	for t in arg:
		fullFile = os.path.join(basefolder, t)
		os.remove(fullFile)

#You can call the function using

delete_files(“file1.txt”, “file2.txt”)
delete_files(“file.txt”)
delete_files()
```

Notice the '\*' before __arg__ in the first line, but not in the second line. The '\*' just informs python that the argument should be considered as a tuple containing variable number of arguments.

## Doc comments

It's very surprising how long it took me to discover this functionality when I first started to learn python. All these while I thought that python only came with single line comments using the ‘#’ symbol. I found it hard to comment a large number of lines until I learned of the doc string. This feature is mainly, let me stress, “mainly” used for documentation of various parts of code. But like most things doc strings can be used to comment sections of code that you don’t want to use right now but don’t want to delete as well. Doc string does not require you to indent your text to work.

Example of using doc string for documenting.

```python
def some_function(a, b, c):
	‘‘‘ 
	This is some function, that does something, takes some variables and returns something else.
	‘‘‘
	pass
```
It can also be used as.

```python
def config_server():
	‘‘‘
	# Local config
	server = localhost
	port = 1024
	user = blah
	‘‘‘
	#Deployment config
	server = something.com
	port = 80
	user = admin
```
Doc strings are three continuous single quotes and everyone should use them as much as possible. 
