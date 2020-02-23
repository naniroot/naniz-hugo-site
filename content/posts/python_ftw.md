---
title: "Python FTW"
date: 2013-09-27T14:15:17-08:00
draft: false
images:
tags: [python, coding, xkcd, winning]
---
> Revitilizing very old post from the past. Of course, my thinking has changed since then, but its always fun to open a time capsule.

Python has made programming an absolute pleasure for me. I simply love working with python. The ease of programming and the importance given to programming logic than programming syntax is an absolute delight. I first learnt python from this [tutorial](http://cscircles.cemc.uwaterloo.ca/). It is an awesome website to learn python. Whenever someone asks me how is it to code in python? I always remember this xkcd comic.

[{{< image src="/images/xkcd_python.png" alt="XKCD Python" position="center">}}](https://xkcd.com/353/)

According to me, python is the only true “high” level language. I mean, if programming languages took part in “Game of Thrones” python would be on Iron Throne the whole time and nobody would dare rebel against it. 

Some common observations is the syntax. There is absolutely very minimal syntax, there are no semicolons, parentheses or type declaration. There are tons and tons of packages that you can import and work on. Writing modules in python is also a cakewalk, you find modules for a lot of things. You want to access UNC path there is a module, want to SFTP, there is a module, want to write a web crawler, there is a module. There are gateway and wrapper modules that supports almost all common programming languages and frameworks.

Even web programming is amazing. _Django_ and _Pylons_ are the major ones and they take web programming to a whole new level. These web frameworks take a lot of work out of your hands and provide you with a lot of power to simply code and build beautiful things.

Some examples of why python is a breeze to learn and use.

This is a common one.

### How do you print “hello, world” in python?

```python
print “Hello, World”
```
### How do you print “hello, world” in say, Java?

```java
class Foo{
	public static void main(String v[ ]){
		System.out.println(“Hello, World”);
	}
}
```

## List Comprehension 
### Generate a list of even integers below 100

One line,
```python
A = [ x for x in range(2, 100, 2)]
```
List of square numbers below 10.
No problem, just one line again
```python
A = [x * x for x in range(10) ]
```
Suppose you have a huge list of numbers and you want to extract only even numbers from it.
```python
A = [ 3, 5, 34, 77, 88, 500, 145, 338, ….., 1538]
even = [ x for x in A if x%2 == 0]
```
Yes, just two lines and the first line does not even count.

Python eases coding a lot. But **do not** get carried away, other programming languages are also very good . And depending on the requirement you should choose the appropriate language. **Compiled languages are faster and should always be considered before interpreted language.** If speed of execution is important then compiled languages, if speed of development is essential then python is an amazing choice.

Another good example of python would be the ‘with’ statement.

As a programmer you tend to forget sometimes. You will have open files, sockets or other connections and forget to close it. The python ‘with’ statement comes in handy. One can simply say 

```python
with open(“filename”, “r”) as fs:
	do something
```
and python takes care of closing the file on its own after the scope is over. In a broader sense, what ‘with’ statement is trying to accomplish is this
```
 set things up
    try:
        do something
    finally:
        tear things down
```
Here the `tear things down` will be taken care by `with` statement and does not require explicit `finally` block.

Python is very powerful, I am sure there are plenty of other examples out there that show the power of python. I highly recommend development in python.


