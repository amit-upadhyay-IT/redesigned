---
layout: tutorials
permalink: /tutorials/play-with-a-random-code/
title: A random code.
---

Before I tell what is `dp`? I would like you to go through an example code.

{: .info .note}
**Some random code:**

```py
def F(n):
    if n == 0:
        return 0
    else:
        result = 0
        for i in range(n):
            result += F(i)
        return result+n


print F(int(raw_input()))
```
If you observe the function `F(n)` is calculating `(2**n)-1` with a time complexity of **O(2^n)**.

This is an example of Exhaustive Search where we are exploring every possible branch that can be formed from a set of whole numbers up to n (which is passed as the argument and for loop is used for that). Let's construct the decision tree (recursive call stack) for the above function.

Let a call be made with `F(3)`, now three branches will be formed for each number in the set S (S is set of whole numbers up to n). I have taken n = 3, coz it will be easy for me to make the diagram for it. You can try will other larger numbers and observe the recursion call stack.

```
    3
   /| \
  0 1  2    ----> the leftmost node is returns 0 coz (n==0) it's the base case 
    |  /\
    0  0 1
         |
         0   ----> returns 0
```

So here you have explored every possibility branches. If you try to write the recursive equation for the above problem then:

```
T(n) = 1; n is 0
     = T(n-1) + T(n-2) + T(n-3) + ... + T(1); otherwise
```

Here,

```
T(n-1) = T(n-2) + T(n-3) + ... T(1).
So, T(n-1) + T(n-2) + T(n-3) + ... + T(1) = T(n-1) + T(n-1)
```

So, the Recursive equation becomes:

```
T(n) = 1; n is 0
     = 2*T(n-1); otherwise
```

Now you can easily solve this recurrence relation (or use can use Masters theorem for the fast solution). You will get the time complexity as **O(2^n)**.

Solving the recurrence relation:

```
T(n) = 2T(n-1)
     = 2(2T(n-1-1) = 4T(n-2)
     = 4(2T(n-3)
     = 8T(n-3)
     = 2^k T(n-k), for some integer `k` ----> equation 1
```

Now we are given the base case where n is 0, so let,

```
n-k = 0 , i.e. k = n;
```

Put `k = n` in equation 1,

```
T(n) = 2^n * T(n-n)
     = 2^n * T(0)
     = 2^n * 1; // as T(0) is 1
     = 2^n
So, T.C = O(2^n)
```
