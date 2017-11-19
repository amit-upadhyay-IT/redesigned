---
layout: tutorials
permalink: /tutorials/separate-0's-and-1's/
title: Separate 0's and 1's
---

<div class="note info">
  <h5>Separate the 0's and 1's in an array containing only 0's and 1's.</h5>
  <p></p>
</div>


<div class="note unreleased">
  <h5>Approach 1</h5>
  <p>
    Try to solve in only one iteration.
  </p>
</div>

**Use counting sort**:

We can maintain the count of either 0 or 1

Now we can override the elements of array with 0 and 1 respectively


### Code:


```c
#include<stdio.h>
#include<stdlib.h>

int zero_cnt(int *arr, int n)
{
    int i, cnt = 0;
    for (i = 0; i < n; ++i)
        if (arr[i] == 0)
            cnt++;
    return cnt;
}

void set_array_element(int *arr, int n, int z_cnt)
{
    int i;
    for (i = 0; i < z_cnt; ++i)
         arr[i] = 0;
    for (i = z_cnt; i < n; ++i)
        arr[i] = 1;
}

void print_array(int *arr, int n)
{
    int i;
    for (i = 0; i < n; ++i)
        printf("%d ", arr[i]);
}

int main()
{
    int i, n, *arr;
    scanf("%d", &n);
    arr = (int*) malloc(n*sizeof(int));
    for (i = 0; i < n; ++i)
        scanf("%d", &arr[i]);
    int z_cnt = zero_cnt(arr, n);
    set_array_element(arr, n, z_cnt);
    print_array(arr, n);
    return 0;
}
```


<div class="note unreleased">
  <h5>Approach 2</h5>
  <p>
    Think about other problems that can be solved using this algo
  </p>
</div>

Using kadane's algorithm to solve this problem:

- Simple idea in Kadane's algo is to look for all positive contiguous segments of the array(max_ending_here is used for this purpose).

- And keep track of maximum sum contiguous segment among all positive segments(max_so_far is used for this).

- Each time we get a positive sum, we compare it with max_so_far and update max_so_far if it is greater than max_so_far.


#### Algo:

**Initialize**:
```c
max_so_far = 0
max_ending_here = 0
```
Loop for each element of the array:

a)
```c
max_ending_here = max_ending_here+a[i];
if(max_ending_here<0) 
{
	max_ending_here = 0
}
```

c)

```c
if (max_so_far < max_ending_here)
{
	max_so_far = max_ending_here;
}

return max_so_far;
```
Above was a normal introduction to Kadane's algo for finding the maximum sum subarray.

Now we can use this approach to find maximum difference in the given array.

Step 1: Create difference array: it has elements as the difference between two successive elements i.e. `diff[i] = arr[i+1]-arr[i];`

Step 2: The maximum sum subarray in difference array is the maximum difference in original array where the greater element comes later than the smaller one.


### Code:


```c


```

