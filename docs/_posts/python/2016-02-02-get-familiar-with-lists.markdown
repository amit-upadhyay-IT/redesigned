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


### Appending in the list

Appending a list is adding more element(s) at the end of the list. To add new elements at the end of the list, Python provides a method append ( ).

Syntax is:

```py
# List. append (item)

L1. append (70)
```

This will add 70 to the list at the end, so now 70 will be the 5 th element of the list, as it already have 4 elements.

Using `append()`, only one element at a time can be added. For adding more than one element, `extend()` method can be used, this can also be used to add elements of another list to the existing one.

Example:

```py
>>> A = [100, 90, 80, 50]
>>> L1. extend (A)
>>> print L1
[1, 2, 5, 4, 70, 100, 90, 80, 50]
```

will add all the elements of list `A` at the end of the list `L1`.


```py
>>>print A
[100, 90, 80, 50]
```

> Remember: `A` remains unchanged.


### Updating array elements

Updating an element of list is, accomplished by accessing the element & modifying its value in place. It is possible to modify a single element or a part of list. For first type, we use index to access single element and for second type, list slice is used. We have seen examples of updations of an element of list. 

Lets update a slice.

Example1:

```py
>>> L1 [1:2] = [10, 20]
>>> print L1
# will produce
[1, 10, 20, 4, 70, 100, 90, 80, 50]
```

Example2:

```py
>>> A=[10, 20, 30, 40]
>>> A [1:4] = [100]
>>> print A
# will produce
[10, 100]
```
As lists are sequences, they support many operations of strings. For example, operator `+` & `*` results in concatenation & repetition of lists. Use of these operators generate a new list.

Example:

```py
>>> a= L1+L2

# will produce a 3 rd list a containing elements from L1 & then L2. a will contain
[1, 10, 20, 4, 70, 100, 90, 80, 50, “Delhi”, “Chennai”, “Mumbai”]

>>> [1, 2, 3] + [4, 5, 6]
[1, 2, 3, 4, 5, 6]

>>> ['Hi!']* 3
['Hi!', 'Hi!', 'Hi!']
```
> It is important to know that `+` operator in lists expects the same type of sequence on both the sides otherwise you get a type error.

If you want to concatenate a list and string, either you have to convert the list to string or string to list.


Example:

```py
>>> str([11, 12]) + “34”
'[11, 12] 34'
>>> “[11,12]” + “34”
'[11, 12] 34'


>>> [11, 12] + list (“34”)
[11, 12, '3', '4']
>>> [11, 12] + [“3”, “4”]
```


### Deleting Elements

It is possible to delete/remove element(s) from the list. There are many ways of doing:

(i) If index is known, we can use `pop()` or del

(ii) If the element is known, not the index, `remove ()` can be used.

(iii) To remove more than one element, `del()` with list `slice` can be used.

(iv) Using assignment operator.

**Let us study all the above methods in details**:

#### Pop()

It removes the element from the specified index, and also return the element which was removed.

Example:

```py
>>> L1 = [1, 2, 5, 4, 70, 10, 90, 80, 50]
>>> a= L1.pop (1) # here the element deleted will be returned to ‘a’
>>> print L1
[1, 5, 4, 70, 10, 90, 80, 50]
>>> print a
2

# If no index value is provided in pop ( ), then last element is deleted.
>>>L1.pop ( )
50
```

**del** removes the specified element from the list, but does not return the deleted value.

```py
>>> del L1 [4]
>>> print L1
[1, 5, 4, 70, 90, 80]
```

### remove ()

In case, we know the element to be deleted not the index, of the element, then `remove()` can be used.

```py
>>> L1. remove (90) # will remove the value 90 from the list

>>> print L1
[1, 5, 4, 70, 80]
```






Thank you 👏
