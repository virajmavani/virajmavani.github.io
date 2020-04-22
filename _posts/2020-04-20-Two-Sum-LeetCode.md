---
layout: post
title:  "Two Sum - LeetCode #1"
date:   2020-04-20
desc: "Two Sum Problem Walktrough from LeetCode"
keywords: "coding, competitive coding, leetcode, hackerrank, interview, question"
categories: [Leetcode]
tags: ["#1", Two Sum, LeetCode, Interview Question]
icon: icon-html
---

As "Hello, World!" is to Programming, so is the Two Sum problem to LeetCode. Any blog series or YouTube channel targeted towards solving LeetCode problems has to first pay deference to this problem. It is therefore implied that this blog series will be no different.

So let's just jump right into it.
<br/><br/>

## Two Sum Problem Statement
-------------------------------------
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
<br/>

## Problem Analysis
-------------------------------------
Well, the problem statement is clear and to the point enough that we don't need to do much analysis. The only points to note here are:

1. We have to return indices
2. The array is not sorted

<br/><br/>

## Solution(s)
-------------------------------------
### 1. Brute Force Approach

First and foremost, we must try to solve the problem using a brute-force approach so as to get more insight into how to further optimize it.

We can simply iterate over each element and for each such element, we can iterate over the rest of the elements in the array to check if they sum up to the target value.

The python code will look something like this:
<br/>
```python
def two_sum(array, target):
    n = len(array)
    for i in range(n):
        for j in range(i+1, n):
            if array[i] + array[j] == n:
                return [i, j]
    
    return []
```
<br/>
Well, that was cute. But really abhorrent if you want to land that FAANG job you are looking for.

We can safely rely on our Algorithms and Data Structures course content and say that the time complexity here is in the order of O(N<sup>2</sup>) and we are not really using any extra space so the space complexity will be O(1).

<code>
Time Complexity: O(N<sup>2</sup>)
<br/>
Space Complexity: O(1)
</code>
<br/><br/>

### 2. Optimal Approach - Using Hash Table 

I recall that I once was watching a YouTube video on LeetCoding practices and the content creator said that Hash Tables are very over-powered. You can't come up with a solution, just throw Hash Tables at the problem and you will make some progress. Constant time access IS over-powered.

Same applies to this problem as well and in this case, it is the most optimal approach known to programmers worldwide.

The idea here is that we can use Hash Table to store the elements and keys and their indices as values. While iterating through each element, we can then check if (target - element) is present in the Hash Table or not. The answer will simply then become the iterator index and the index stored in the Hash Table.

The python code looks something like this:

```python
def two_sum(array, target):
    n = len(array)
    htable = {}

    for i in range(n):
        residual = target - array[i]
        if residual in htable:
            return [htable[residual], i]
        htable[array[i]] = i
    
    return []
```

Isn't it beautiful? Indeed it is. We have sacrificed some space in order to achieve linear time complexity for the solution. The Hash Table uses O(N) space and the time complexity becomes O(N) as well. But, space is cheap and time invaluable. Therefore, this being the most optimal approach.

<code>
Time Complexity: O(N)
<br/>
Space Complexity: O(N)
</code>
<br/><br/>

### Alternative Problem Statement - Sorting

___Return Elements___

When asked to return the elements and not the indices, the following is also one of the approaches. It is not as good as the Hash Table approach, but still is better than brute force.

The approach is called the two pointer approach. It might be difficult to get to it logically, but on knowing it, it is as simple as it can be.

In this problem, we noticed that there have been no comments on the order of the elements in the array making us assume that it is an unsorted one. We can initially sort the array to get ordering introduced in the problem. Once, we have the ordering we can make decisions by trying out different sum of two elements.

For any indices [i, j] (where i < j) in the sorted array, we can
safely say that if the sum of the elements at i and j is greater than
the target, then we might want to decrement j in order to get to the
target. Same applies vice versa, that is, if the sum is less than the
target, incrementing i will rbing us closer to the solution.

Basically, we will start with i = 0 and j = n-1 (where n = len(array))
adn increment i or decrement j in accordance with the sum of the
elements at i and j.

The python code for this approach looks something like this:

```python
def two_sum(array, target):
    n = len(array)
    i = 0
    j = n-1

    # Sort array in place
    array.sort()

    while i < j:
        curr_sum = array[i] + array[j]
        if curr_sum == target:
            return [array[i], array[j]]
        if curr_sum < target:
            i += 1
        else:
            j -= 1
    
    return []
```

The computational complexities for this approach are given below:

<code>
Time Complexity: O(N*log(N))
<br/>
Space Complexity: O(1) // as sorting in place
</code>
<br/><br/>

## End Note
-------------------------------------
I know developing intuition for solving LeetCode problems is difficult. Over time, you will understand that there are a few approaches that should first be tried out for each problem. Just try to apply them mentally and think if they would in any way help you in getting to the answer. One such approach that we learned today is the Two Pointer Approach.


___Later.___