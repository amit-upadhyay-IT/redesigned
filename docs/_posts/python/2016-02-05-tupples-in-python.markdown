---
title: 'Tuple in python'
date: 2016-02-05 12:01:40 +0200
author: amit-upadhyay-it
categories: [python]
---


{: .info .note}
**What is a Tuple?**<br>A tuple is a sequence of values, which can be of any type and they are indexed by integer. Tuples are just like list, but we can’t change values of tuples in place. Thus tuples are immutable. The index value of tuple starts from `0`.

A tuple consists of a number of values separated by commas.

For example:

```py
>>> T=10, 20, 30, 40
>>> print T
(10, 20, 30, 40)
```

But in the result, same tuple is printed using parentheses. To create a tuple with single element, we have to use final comma. A value with in the parenthesis is not tuple.

Example:

```py
>>> T=(10)
>>> type(T)
<type 'int'>

>>> t=10,
>>> print t
(10,)

>>> T=(10,20)
>>> type(T)
<type 'tuple'>
```

Example:

```py
# Tuple with string values
>>> T=('sun','mon','tue')
>>> print T
('sun', 'mon', 'tue')

# Tuples with single character
>>> T=('P','Y','T','H','O','N')
>>> print T
('P', 'Y', 'T', 'H', 'O', 'N')
```

### Tuple Creation

If we need to create a tuple with a single element, we need to include a final comma.


```py
Example
>>> t=10,
>>> print t
(10,)
```

Another way of creating tuple is built-in function `tuple()`.

Syntax:
```py
T = tuple()
```

Example:

```py
>>> T=tuple()
>>> print T
()
```

### Add new element to Tuple

We can add new element to tuple using `+` operator.


Example:
```py
>>> t=(10,20,30,40)
>>> t+(60,)
# this will not create modification of t.
(10, 20, 30, 40, 60)
>>> print t
(10, 20, 30, 40)
>>> t=t+(60,) # this will do modification of t.
>>> print t
(10, 20, 30, 40, 60)
```

**Example**

#### Write a program to input `n` numbers and store it in tuple.

Code
```py
t=tuple()
n=input("Enter any number")
print " enter all numbers one after other"
for i in range(n):
	a=input("enter number")
	t=t+(a,)
print "output is"
print t
```

Another version of the above program:

```py
t=tuple()
n=input("Enter any number")
print " enter all numbers one after other"

for i in range(n):
	a=input("enter number")
	t=t+(a,)

print "output is"
for i in range(n):
	print t[i]
```

We can also add new element to tuple by using `list`. For that we have to convert the tuple into a list first and then use `append()` function to add new elements to the list. After completing the addition, convert the list into tuple. Following example illustrates how to add new elements to tuple using a list.


```py
>>> T=tuple() #create empty tuple
>>> print T
()
>>> l=list(T) #convert tuple
into list
>>> l.append(10) #Add new elements to list
>>> l.append(20)
>>> T=tuple(l)
#convert list into tuple
>>> print T
(10, 20)
```

Initializing tuple values:
```py
>>> T=(0,)*10
>>> print T
(0, 0, 0, 0, 0, 0, 0, 0, 0, 0)
```





Thank you 👏
