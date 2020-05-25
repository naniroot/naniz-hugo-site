---
title: "Immutability"
date: 2013-05-24T20:32:27-07:00
draft: false
images:
tags: [immutability, coding, language, programming, optimization]
---
> Revitilizing very old post from the past. Of course, my thinking has changed since then, but its always fun to open a time capsule.

Immutability is a very important concept that most of us might not know explicitly. An immutable object cannot be modified after it has been created. Consider the following simple python code.

```python
var = "hello"
print var
var[1] = "6"
print var
```
gives an error
```python
TypeError: 'str' object does not support item assignment
```
That is because __String__ is an immutable object it cannot be modified after creation.

### Why are immutable objects needed?
1. A compiler/ interpreter does this to reduce complications and work efficiently. 
2. Immutable objects are inherently thread-safe
3. Simpler to understand
4. Offer good security

### Thats great, but why should I know about immutable object?

Consider an example where you want to print “My name is Nani and I have 3 friends Ravi, Sita and Ram” where “Nani”, “Ravi”, “Sita” and “Ram” are in different String objects. So, in python your code will look something like this

```python
a = “Nani”
b = “Ravi”
c = “Sita”
d = “Ram”
output = “My name is “+a+” and I have 3 friends “+b+”, ”+c+” and ”+d
print output
```

This gets the job done. But its a slow operation, as strings are immutable objects, output string cannot be created in place. A new memory location has to be created and the string copied to the new location from the previous place and a new string created.

But instead, if you write the code like this
```python
a = “Nani”
b = “Ravi”
c = “Sita”
d = “Ram”
output = “My name is %s and I have 3 friends %s, %s and %s”%(a, b, c, d)
print output
```
The compiler pre-allocates the space for the string as it expects things to be added and thus the operation is __in place__ and much faster. The time difference between the first method and second is not much, but when coding huge applications every small bit of execution time you save amounts to a lot. 

### What if I want to modify strings? what should I do?

In Java, you can use StringBuffers which are mutable and hence can be modified. In python you can keep a list of characters and only combine them when needed like

```python
>>> var = list(“hello”)
>>>var
[ ‘h’ , ‘e’ , ‘l’ , ‘l’ , ‘o’ ]
>>>var[0] = ‘z’
>>>var
[ ‘z’ , ‘e’ , ‘l’ , ‘l’ , ‘o’ ]
>>>””.join(var)
‘hello’
```

The basic structure of an mutable object would be an constructor that initializes the data and getter and setter functions. An immutable object on the other hand would only have the constructor and getter function.

```java
class Mutable{
  private int value;

  public Mutable(int value) {
     this.value = value;
  }

  //getter and setter for value
}
```
```java
class Immutable {
  private final int value;

  public Immutable(int value) {
     this.value = value;
  }

  //only getter
}
```

### What are some example immutable objects?
1. In python numbers, booleans, strings, tuples, frozensets are immutable.
2. In Java all primitive wrappers like Integer, Long, Short, Double, Float, Character, Byte, Boolean are all immutable
3. Java variable prepended with “final” keyword.

### References:

- http://en.wikipedia.org/wiki/Immutable_object
- http://stackoverflow.com/questions/1228299/change-one-character-in-a-string-in-python
- http://stackoverflow.com/questions/4658453/difference-between-mutable-objects-and-immutable-objects


