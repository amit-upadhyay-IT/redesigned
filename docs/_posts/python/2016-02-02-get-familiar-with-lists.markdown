---
title: 'Get familiar with lists'
date: 2016-02-03 12:01:40 +0200
author: amit-upadhyay-it
categories: [python]
---


{: .info .note}
**What is a list**<br>Like a String, list also is sequence data type. It is an ordered set of values enclosed in square brackets []. Values in the list can be modified, i.e. it is mutable.

For accessing an element of the list, indexing is used.

Syntax: 
```py
listName[index] #(variable name is name of the list).
```

Index here, has to be an integer value- which can be positive or negative. Positive value of index means counting forward from beginning of the list and negative value means counting backward from end of the list. Remember the result of indexing a list is the value of type accessed from the list.

Let's look at some example of simple list:

```py
>>> L1 = [1, 2, 3, 4] # list of 4 integer elements.

>>> L2 = [“Delhi”, “Chennai”, “Mumbai”] #list of 3 string elements.

>>> L3 = [ ] # empty list i.e. list with no element

>>> L4 = [“abc”, 10, 20] # list with different types of elements

>>> L5 = [1, 2, [6, 7, 8], 3] # A list containing another list known as nested list
```

To change the value of element of list, we access the element & assign the new value.

Example:

```spyh
>>> print L1 # let‟s get the values of list before change
>>> L1 [2] = 5
>>> print L1 # modified list
[1, 2, 5, 4]
```

> **NOTE**: An Index Error appears, if you try and access element that does not exist in the list.

## Creating a list

List can be created in many ways:

i) By enclosing elements in [ ], as we have done in above examples.

ii) Using other Lists

Example:

```py
L5=L1 [:]
```
Here L5 is created as a copy of L1.

```py
>>> print L5
L6 = L1 [0:2]
>>> print L6
# will create L6 having first two elements of L1.
```

iii) List comprehension:

Example:
```py
>>> S= [x**2 for x in range (10)]
>>> print S
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

In mathematical terms, `S` can be defined as `S = {x 2 for: x in (0.....9)}`. So, we can say that list comprehension is short-hand for creating list.


iv) Using built-in object

`L = list ()` will create an empty list.

or

`L = list [(1, 2, 3, 4)]`

> A single new list is created every time, you execute [ ]. We have created many different lists each using [ ]. But if a list is assigned to another variable, a new list is not created.

Example:
```py
A = []
B = A # Will also create one list mapped to both
C = []
```

You can try to check the address of A and B.

```py
if id(A) == id(B):
  print 'yes'

# printing the address
print hex(id(A))
print hex(id(B))
```
## Accessing an element of list

For accessing an element, we use index and we have already seen example doing so. To access an element of list containing another list, we use pair of index. Lets access elements of L5 list. Also a sub-list of list can be accessed using list slice.

### List Slices

Slice operator works on list also. We know that a slice of a list is its sub-list. For creating a list slice, we use `[n:m]` operator.

```py
>>> print L5 [0]
1
>>> print L5 [2]
[6, 7, 8]
>>> print L5 [2] [0]
6
>>> print L5 [2] [2]
8
>>> L1 [1:2]
[2]
```
`list[n:m]` will return the part of the list from n th element to m th element, including the first element but excluding the last element. So the resultant list will have m-n elements in it. Slices are treated as boundaries, and the result will contain all the elements between boundaries.

#### Its Syntax is:

```py
seq = L [start: stop: step]
```

Where `start`, `stop` & `step` - all three are optional. If you omit first index, slice starts from `0` and omitting of stop will take it to `end`. Default value of step is 1.

Example

For list L2 containing [“Delhi”, “Chennai”, “Mumbai”]

```py
>>> L2 [0:2]
[“Delhi”, “Chennai”]

>>> list = [10, 20, 30, 40, 50, 60]
>>> list [::2] # produce a list with every alternate element
[10, 30, 50]

>>> list [4:] # will produce a list containing all the elements from 5 th position till end
[50, 60]

>>> list [:3]
[10, 20, 30]
>>> list [:]
[10, 20, 30, 40, 50, 60]

>>> list [-1] # „-1‟ refers to last elements of list
60
```

> **Note**: Since lists are mutable, it is often recommended to make a copy of it before performing operation that change a list.

## Traversing a List

Let us visit each element (traverse the list) of the list to display them on screen. This can be done in many ways:

- `while` loop

```py
i = 0
while i < len [L1]:
    print L1 [i],
i + = 1
```

will produce following output

```
1 2 5 4
```
- `for` loop

```py
for i in L1:
    print i,
```

or

```py
for i in range ( len (L1)):
    print L1 [i],
```
`range()` function is used to generate, indices from 0 to len -1; with each iteration i gets the index of next element and values of list are printed.

> Note: for loop in empty list is never executed











Thank you 👏
