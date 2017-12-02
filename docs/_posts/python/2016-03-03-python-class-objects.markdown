---
title: 'Introduction to classes and objects'
date: 2016-03-03 12:01:40 +0200
author: amit-upadhyay-it
categories: [python]
---

### Classes

It is basically a blueprint to create objects. An object is a basic key concept of OOP but classes provide an ability to generalize similar type of objects.


### Object

**Every object is characterised by**:

- **Identity**: This is the name that identifies an object.

- **Properties**: These are the features or attributes of the object.

- **Behaviour**: The behaviour of an object signifies what all functions an object can perform.



### Namespaces

The variables refer to an object and they are created when they are first assigned a value. In fact the variables are bound to their values using the assignment operator(=). So a namespace is a place where a variable's name is stored and the value of the variable is bound to this namespace.

A namespace is a mapping from names to objects. It is a thing which associates the names with its values. In simple terms, it is a place where name lives. They are created at different moments and have different lifetimes. The examples of namespaces are:

- **Built-in names**:
These consist of functions such as `max()` , `min()` and `built-in exception names`. This namespace is created when the Python interpreter starts up, and is never deleted. The built-in names actually also live in a module called `__ builtin__`.

- **Global names in a module**:
The global namespace for a module is created when the module definition is read in and normally lasts until the interpreter quits. The statements executed by the top-level invocation of the interpreter, either read from a script file or interactively, are considered to be part of a module called `__main__` and they
have their own global namespace.

- **Local names in a function invocation**:
The local namespace for a function is created when the function is called, and deleted when the function returns or raises an exception that is not handled within the function. Even each recursive invocation has its own local namespace.

If we talk about classes and objects, the set of attributes of an object also form a namespace. It must be noted that there is absolutely no relation between names in different namespaces. Two different modules may both define same function without any confusion because the functions are prefixed with the module name. That means `module1.cmp()` has no relation with `module2.cmp()`.













Thank you 👏
