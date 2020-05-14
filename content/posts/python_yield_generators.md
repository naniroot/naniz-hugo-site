---
title: "Python Yield Command and Generators"
date: 2013-07-14T14:15:17-08:00
draft: false
images:
tags: [python, coding, yeild, generators]
---
> Revitilizing very old post from the past. Of course, my thinking has changed since then, but its always fun to open a time capsule.

I come across a lot gems in python. Some are easy to understand, some require more time. The best way to understand them is by working with them and using them in programs. To make the understanding stronger you can write about them. I wanted to understand the yield command better so here it is.

To understand **yield** you first have to understand generators, iterables and their differences.

## Iterables

Iterables are a pretty well-known concept. They are anything that you can iterate on. Remember in basic C you first had to find the length and then run a ‘for’ loop to find all the elements. Iterables you can directly iterate and access all the elements. They are now available in most languages. Since we are talking about python, here are few examples

```python
A = [1, 2, 3]
for ch in A:
	print ch
```
```
output:
1
2
3
```
```python
B = [ x*x for x in range(3)]
for x in B:
	print x
```
```
output:
0
1
4
```
## Generators

Now, these are not that well-known. Generators are also iterables, they can also be iterated on, but only once. They do not store every value in memory. An example in python would be

```python
A = (x*x for x in range(3))
for x in A:
	print x
```
```
Output:
0
1
4
```
Notice that the generator uses ‘(‘ compared to a ‘[‘ of a iterable. Now, why would somebody need a generator? 
 Whenever there is a function call in python, the function continues to execute until it finds a return statement or an exception or end of context where the default “return None” is executed. After this, all the context of the function is lost like the local variables, stack frames etc. This is good for many scenarios but sometimes you would need the function to retain context, like, for example you want to

### Print squares of the first 1000 numbers

You can do this in 3 ways.

1. Create a list of numbers and print from there.

```python
def square_print():
	return [x*x for x in range(1000)]
```
This creates a huge list takes a lot of memory, and its too cumbersome to move an entire list around if you need the squares at different point of time. 

Remember in python the integer object has no limit and can take values as much as the memory you have.

2. You could use global variable and send the square only when you need it. That would work right? 
```python
glbV = 0

def square_print():
	global glbV
	if glbV <1000:
		square = glbV*glbV
		glbV+=1
		return square
```
This would work, will not take much memory as well. But again global variables are ugly, they act weird when threads are used and also the variable would not be protected, security and accidental modification is a concern. So, what should we do?

3. We use generators.
Generators were created to ease programmers woes. They very cleanly take care of situation exactly like this. This is where the **yield** command also comes into picture. A generator for the above application would look something like this.
```python
def square_print():
	num = 0
	while num<1000:
	yield num*num
	num = num+1

generator = square_print()
for x in generator:
	print x
```
This is a very clean way to program and python automatically takes care of context, it protects accidental modification, provides security to the variable, is thread safe and very neat. Python is fun ain’t it?

## References
- http://stackoverflow.com/questions/231767/the-python-yield-keyword-explained
- http://wiki.python.org/moin/Generators
- http://www.jeffknupp.com/blog/2013/04/07/improve-your-python-yield-and-generators-explained/