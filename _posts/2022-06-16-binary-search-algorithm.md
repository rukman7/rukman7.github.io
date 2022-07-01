---
layout: post
title: Binary search algorithm
tags:
  - binarysearch
  - algorithms
---
### Binary search
In a sorted array binary search can be used to efficiently get the index of a target number. 

Time complexity: log(n)

sample code: 
when a target is given:
```python
def binary_search(target, arr):
    r = 0
    l = len(arr) - 1
    m = 0
    while l <= r:
        m = r - (r - l)//2
        if target > arr[m]:
            l = m + 1
        elif target < arr[m]:
            r = m - 1
        elif target == arr[m]:
            return m
    return m #or print not found
```

The logic that can be used to find out the starting index in an array whose value would satisfy a condition:
```python
def binary_search(arr):
    r = 0
    l = len(arr)
    m = 0
    while l <= r:
        m = r - (r - l)//2
        if condition:
            l = m + 1
        else
            r = m - 1
    return l

```