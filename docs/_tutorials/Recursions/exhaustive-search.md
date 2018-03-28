---
layout: tutorials
permalink: /tutorials/exhaustive-search/
title: Exhaustive Search
---

{: .info .note}
**Exploring every possible combination from a set of choices or values.**

The linear search is also an example of exhaustive search because here we are looking at all the numbers present in the list. Sometimes its hard to enumerate all of the choices. For example, printing all possible groups in a list of integers where each group may consist up to 15 elements.

Recursion is a really good algorithmic pattern for performing an exhaustive search.

Famous application:- Producing all permutations of a set of values.

### General pattern:

**What is prefix below?**

It is some data storage entity, it can be a string or a vector and any other type which may store one of the possible output in some call stack out of many call stacks.

```yml
Search(decisions, prefix):
  - if there are no more decisions to make: stop and print prefix
  - else, let's handle one decision ourselves i.e. update prefix (as the prefix
    is the one which stores one of the possibilities), and rest by recursions
    for each available choice C for this decision.
      - choose C and add or append it to the prefix.
      - Search the remaining decisions that could follow C.
```

- Often the search space consists of many decisions, each of which has several available choices. Example: When enumerating all 5-letter string, each of the 5-letter is a decision, and each of those decision has 26 possible choices.


## Example 1: print binary

{: .info .note}
Write a recursive function that accepts an integer number of digits and prints all binary number that have exactly that many digits.

If input = 3,

then, output:

```
000
001
010
011
100
101
110
111
```

The task is to print all the binary numbers of exactly `3` length.

To solve such problems, you can think of the self-similarity in the problem and then write the recursive case, i.e. how is printing `3` digit binary numbers similar to printing `2` digit binary number.

**Example**:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>2 digit binary number</th>
      <th>3 digit binary number</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><code>00</code></p></td>
      <td><p>

    <code>000</code>

      </p></td>
    </tr>
    <tr>
      <td><p><code>01</code></p></td>
      <td><p>

       <code>001</code>

      </p></td>
    </tr>
    <tr>
      <td><p><code>10</code></p></td>
      <td><p>
    <code>010</code>

      </p></td>
    </tr>

    <tr>
      <td><p><code>11</code></p></td>
      <td><p>
    <code>011</code>

      </p></td>
    </tr>

    <tr>
      <td><p><code>10</code></p></td>
      <td><p>
    <code>010</code>

      </p></td>
    </tr>

    <tr>
      <td><p><code></code></p></td>
      <td><p>
    <code>100</code>

      </p></td>
    </tr>

    <tr>
      <td><p><code></code></p></td>
      <td><p>
    <code>101</code>

      </p></td>
    </tr>

    <tr>
      <td><p><code></code></p></td>
      <td><p>
    <code>110</code>

      </p></td>
    </tr>

    <tr>
      <td><p><code></code></p></td>
      <td><p>
    <code>111</code>

      </p></td>
    </tr>
  </tbody>
</table>
</div>

Observe that the `2nd` and `3rd` digit of 3 digit binary numbers are nothing but the 2 digit binary numbers, so we can say that the 3 digit binary number is nothing but the 2 digit binary number but preceded by either `0` or `1`. Now, you can easily write the recursive case.

Let's look at the base case, we can keep a counter which will keep count of the number of digits required to print the output and as soon as the counter becomes equal to the required length binary digit then print the output. But, I know you would ask what is `output`? The `output` is a storage entity which will store the possible binary numbers.

With this much of hint try to solve the problem on your own.

If you have solved it then you are great. But if you are stuck it's okay because it's a different kind of recursion problem where you might need the help of the above general proposed algorithm.

Also, there is one more interesting approach which I like very much. In this approach, you create a tree which will represent the solution and then write the code for that.

Example:

The solution in form of a tree can be represented as:

Let, input = 3
```

                      3
                   /     \
                  0       1
                 / \     / \
                0   1   0   1
               / \ / \ / \ / \
              0  1 0 1 0 1 0 1
```

Now, if you see there are total `8` leaves, thus there are `8` three-digit possible binary numbers that can be formed. You can get the solution on traversing from the root to the leaf node. Now, writing code for this becomes very easy.

To get the possible solutions, you can have a counter which will take care for the number of levels reached in the tree (this variable is referred as `decision` in the above general algorithm) and you need one more storage entity which will store the previous occurrences (i.e. `0` and `1` occurrent in the path from root to leaf. Also, this is referred as `prefix` in the above proposed general algorithm).


