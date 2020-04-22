---
layout: post
title:  "Contains Duplicate - LeetCode #217"
date:   2020-04-22
desc: "Solution to Contains Duplicate Problem on LeetCode"
keywords: "coding, competitive coding, leetcode, hackerrank, interview, question, amaon, apple, adobe"
categories: [Leetcode]
tags: [contains duplicate, LeetCode, Interview Question, Amazon, Apple, Adobe]
icon: icon-html
---

The Contains Duplicate problem on LeetCode is again one of the most asked questions and has the distinction to be on the Blind Community curated 75 questions list and therefore it makes it a subject of this blog's interest. While it looks simple at first glance, there are a few things that need to be noted and will be helpful further in your journey through LeetCode.

Let's dive into it!
<br/><br/>

## Problem Statement
-------------------------------------
Given an array of integers, find if the array contains any duplicates.

Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

Example 1:
```
Input: [1,2,3,1]
Output: true
```

Example 2:
```
Input: [1,2,3,4]
Output: false
```

Example 3:
```
Input: [1,1,1,3,3,4,3,2,4,2]
Output: true
```
<br/><br/>

## Problem Analysis
-------------------------------------
The problem is to basically to check if the array contains the same element twice or more. Simple enough. Also, note that the array is unsorted. Nothing more to it than this and so we'll move on to solutions.
<br/><br/>

## Solution(s)
-------------------------------------
### 1. Naive Approach - Brute Force (TimeLimitExceeded on LeetCode)

The brute force approach for any problem is probably the easiest to come up with. Here, we need to check for duplicates and in order to do that we will fix one element and try to find it again in the rest of the array.

The python code for it looks something like this:

```python
def containsDuplicate(nums):
    n = len(nums)
    if n < 2:
        return False
    

    for i in range(n):
        for j in range(i):
            if nums[i] == nums[j]:
                return True
    return False
```

<code>
Time Complexity: O(N<sup>2</sup>)
<br/>
Space Complexity: O(1)
</code>
<br/><br/>

### 2. Better Approach - Sorting

We could have come up with a better solution only if we knew where to look for the second element after fixing the first in the brute force approach. Well, we can do this by simply sorting the array as after that, the duplicates will always be consecutive. We can then just conduct a linear search and determine if there are any duplicates or not.

The python code for this approach will look like:

```python
def containsDuplicate(nums):
    n = len(nums)
    if n < 2:
        return False
    
    nums.sort() # In-place sorting

    for i in range(1, n):
            if nums[i-1] == nums[i]:
                return True
    return False
```

<code>
Time Complexity: O(N*log(N))
<br/>
Space Complexity: O(1)
</code>

While we reduced the time complexity from O(N<sup>2</sup>) to O(N*log(N)), we still can do better in terms of the time complexity. But, it comes at a cost.
<br/><br/>

### 3. Optimal Approach - Hash Set

The most optimal approach in terms of time complexity does indeed use extra space. But, as discussed before, space is cheap and time invaluable. Therefore, we can simple put all elements in a Hash Set and as it does not allow for duplicates, the size of the resulting Hash Set should be equal to the length of the array if there are no duplicates and less otherwise.

A simple one line code in python looks like:

```python
def containsDuplicate(nums):
    return len(set(nums)) < len(nums)
```

Beautiful indeed. The computational complexities are:

<code>
Time Complexity: O(N)
<br/>
Space Complexity: O(N)
</code>
<br/><br/>

___Later.___