---
layout: tutorials
permalink: /tutorials/backtracking/
title: Backtracking
---

{: .info .note}
**Finding solutions by trying partial solutions and then abandoning them if they are not suitable.**

- It is often implemented recursively.
- It is generally used when we the solution can be expressed as a set of tuples (or list of n elements)

Example:

- Producing all permutations of a set of values.
- Games: Suduko, word jumbles, etc
- Escaping from a maze.

**A general pseudo-code algorithm for backtracking problems:**

```yml
Explore(decisions):
  - if there are no more decisions to make: stop
  - else, let's handle one decision ourselves and rest by recursions
    for each available choice C for this decision.
      - choose C.
      - Explore the remaining decisions that could follow C.
      - Un-choose C.  # backtracking
```

Your code should have the above form. While writing the code there may be some little variations too.

**NOTE**: In case of backtracking usually the extra parameter that we add in the function is meant to remember things that we have chosen on previous calls.

The [dice roll problem](http://binomial.me/tutorials/exhaustive-search/#example-3-dice-rolls) can also be solved using backtracking concept where we choose (add to the list), explore (handle one case and call the same function for rest cases), and un-choose (remove our choice). Below is the example code.

```py
def dice_roll2(n, lis):
    if n == 0:
        print lis
    else:
        for i in xrange(1, 7):
            # choose
            lis.append(i)
            # explore
            dice_roll2(n-1, lis)
            # un-choose
            lis.pop()  # removing from last
```

The above code might make more sense as compared to the code written in the [example 3 of exhaustive search](http://binomial.me/tutorials/exhaustive-search/#example-3-dice-rolls) tutorial because here I am un-choosing the last explored choice.

But, do you think popping out the last element is required?
Actually, we have not used list `lis` after popping out the last element out of it. So, popping out is just another extra operation we are performing in above code. The updated value of `lis` list is going to persist in the recursion call stack, so it's better to update only if we need to use.

For example, when I append the `i` in the `lis` then I know that it is going to be used in the same recursion call stack, but after popping out the element, the `lis` isn't going to be used in that call stack as well as the subsequent call stacks.

I wouldn't like to use backtracking approach to solve this problem because here I need to explore every possibility thus, its like an exhaustive-search problem.

Let's look at a slightly modified problem statement.

{: .info .note}
Write a recursive function that accepts an integer (representing a number of 6-sided dice to roll) and a value (desired sum), and prints all the combinations that add up to exactly the desired sum.

To solve this problem one can just edit the above code and before printing the `lis` in the base case just check if the sum of elements in lis becomes equal to desired sum or not.

For example:

Input: n = 3, desired sum = 6

Output:
```
[1, 1, 4]
[1, 2, 3]
[1, 3, 2]
[1, 4, 1]
[2, 1, 3]
[2, 2, 2]
[2, 3, 1]
[3, 1, 2]
[3, 2, 1]
[4, 1, 1]
```

Code:

```py
def dice_sum_helper(n, desired_sum, lis):
    if n == 0:
        # checking if sum of elements in lis is equal to desired_sum
        if sum(lis) == desired_sum:
            print lis
    else:
        for i in xrange(1, 7):
            # choose
            lis.append(i)
            # explore
            dice_sum_helper(n-1, desired_sum, lis)
            # un-choose
            lis.pop()  # removing from last


def dice_sum(n, desired_sum):
    dice_sum_helper(n, desired_sum, [])


if __name__ == '__main__':
    dice_sum(3, 6)
```

The above code is a very bad and inefficient solution to the problem. Here we are exploring every possible branch. In backtracking problems we might need to explore a big tree of possiblities but it's really important to limit the possible options (if possible) because if you don't constraint yourself a little bit then the code will take long execution time.

If you make the decision tree or the recursion call stack tree, you will find many branches of the state space tree are not likely to lead to a successful outcome i.e. they are waste of memory and time.

We will not explore that branch where we see the sum of elements in `lis` list (which is recording the previous outcomes in recursion) becomes more than the `desired_sum`. Also, we need to ignore those branches where we know that the sum of elements in `lis` list can never be `desired_sum`.

**Example:**

Let's say you are rolling 3 dices and you want a desired sum of 16. On the first roll you get `2`, now we know that even if you get `6` on the other two throws of the dice still you won't be able to acheive `16` as the desired sum. So there is no point in exploring the branch which has got `2` on its first dict throw.

We need to do two checks before exploring the branches in the recursions, which are:

1. `sum_so_far + current_element + 1*(n - 1) <= desired_sum` and
2. `sum_so_far + i + 6*(n - 1) >= desired_sum`

The first condition is checking if the `sum_so_far` is not too big and second condition is checking if the `sum_so_far` is not too small.

Example code:

```py
# n is number of dice, lis is solution vector
def dice_sum_helper(n, lis, desired_sum, sum_so_far):
    if n == 0:
        print lis
    else:
        for i in xrange(1, 7):
            if sum_so_far + i + 1*(n - 1) <= desired_sum and\
                    sum_so_far + i + 6*(n - 1) >= desired_sum:
                # choose
                lis.append(i)
                dice_sum_helper(n-1, lis, desired_sum, sum_so_far + i)
                lis.pop()  # removing from last


def dice_sum(number_of_dice, required_sum):
    dice_sum_helper(number_of_dice, [], required_sum, 0)


if __name__ == '__main__':
    num = int(raw_input('Enter number of dices you wish to throw: '))
    desired_sum = int(raw_input('Enter the desired sum: '))
    dice_sum(num, desired_sum)
```
The asymptotic time complexity would still be O(6^n)

# Example 1: Permutation of a string

{: .info .note}
Write a function that accepts a string as a parameter and outputs all possible rearrangements of the letter in that string.

Again, as with every recursion problem try to see how is this problem self-similar (optimal substructure) in nature?

You can first choose a letter and then leave the remaining choices of letters to be handled by the later calls of the function.

To solve this problem you can make a decision tree and then simply code it. If you followed the previous posts I wrote then you should be able to code it up.

Example: Possible permutation of {A,B,C}

```
                      {A, B, C}
                  /	     |	      \
            {A|B,C}     {B|A,C}	  {C|A,B}
           /     \        |	  \       \    \
        {AB|C}  {AC|B}  {BA,C}  {BC,A}  {CA,B}  {CB,A}
```
