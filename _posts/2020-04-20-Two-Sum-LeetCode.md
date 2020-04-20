---
layout: post
title:  "#1 Two Sum - LeetCode Problem"
date:   2020-04-20
desc: "Two Sum Problem Walktrough from LeetCode"
keywords: "coding, competitive coding, leetcode, hackerrank, interview, question"
categories: [Leetcode]
tags: [\#1, Two Sum, LeetCode, Interview Question]
icon: icon-html
---

## Introduction
-------------------------------------
As "Hello, World!" is to Programming, so is the Two Sum problem to LeetCode. Any blog series or YouTube channel targetted towards solving LeetCode problems has to first pay deference to this problem. It is therefore implied that this blog series will be no different.

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
```
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

### 2. Better Approach #1 - Sorting

I know developing intuition for solving LeetCode problems is difficult. Over time, you will understand that there are a few approaches that should first be tried out for each problem. Just try to apply them mentally and think if they would in any way help you in getting to the answer.

One such approach is called the two pointer approach. It might be difficult to get to it logically, but on knowing it, it is as simple as it can be.

For this problem, we noticed that there have been no comments on the order of the elements in the array making us assume that it is an unsorted one. We can initially sort the array to get ordering introduced in the problem. Once, we have the ordering we can make decisions by trying out different sum of two elements.
