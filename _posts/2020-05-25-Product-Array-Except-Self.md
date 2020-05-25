---
layout: post
title:  "Product of Array Except Self - LeetCode #238"
date:   2020-05-25
desc: "Solution to Product of Array Except Self Problem on LeetCode"
keywords: "coding, competitive coding, leetcode, hackerrank, interview, question, facebook, amazon, lyft, goldman sachs, microsoft, apple, oracle, google, adobe, asana"
categories: [Leetcode]
tags: [product of array except self, LeetCode, Interview Question, Facebook, Amazon, Lyft, Goldman Sachs, Microsoft, Apple, Oracle, Google, Adobe, Asana]
icon: icon-html
---

Being one of the most asked questions and also one of the important problem patterns on LeetCode, the product of array except self problem has become a subject of interest for this blog. It uses a modification of a general approach called prefix sum as an optimal solution.

Let's dive into it!

<br/><br/>

## Problem Statement
-------------------------------------
You can find the problem statement here: [Product of Array except Self - LeetCode](https://leetcode.com/problems/product-of-array-except-self/)
<br/><br/>


## Solution(s)
-------------------------------------
### 1. Naive Approach - Brute Force

The brute-force approach to solution is simple. For each index in the the array, we calculate the product of every remaining element.

The python code for it will look like this:

```python
def productExceptSelf(nums):
    n = len(nums)
    result = [0]*n
    for i in range(n):
        product = 1
        for j in range(n):
            if i != j:
                product = product * nums[j]
        result[i] = product
    return result
```

<code>
Time Complexity: O(N<sup>2</sup>)
<br/>
Space Complexity: O(1) [Not considering the result array]
</code>
<br/><br/>

### 2. Better Approach - Prefix and postfix products

As we can observe in the brute-force solution, there is a lot of recomputation happening which can be avoided to speed up our code. All we have to do is to precompute all the products from the left side and right side leaving apart the element at their index and have 2 new arrays holding the products. We can do this in two single passes through the array and then we can finally make the result array going through the arrays once more. A more detailed explanation can be seen in the image below:

<div align="center">
  <img width="800" height="300" src="/static/assets/img/blog/prod-array-except-self/prod_array_except_self.jpg">
</div>

The time complexity will be reduced to O(N) due to single passes but the space complexity will rise to be O(N) as well.

The python code for this approach is given below:

```python
def productExceptSelf(nums):
    n = len(nums)
    left_prod = [1] * n
    right_prod = [1] * n
    result = [1] * n

    for i in range(1, n):
        left_prod[i] = left_prod[i-1] * nums[i-1]
        
    for i in range(n-2, -1, -1):
        right_prod[i] = right_prod[i+1] * nums[i+1]
    
    for i in range(n):
        result[i] = left_prod[i] * right_prod[i]

    return result
```

<code>
Time Complexity: O(N)
<br/>
Space Complexity: O(N) [Extra space used for Left Product and Right Product arrays]
</code>
<br/><br/>

### 3. Optimal Approach - Prefix and postfix products without extra space

We can modify the approach discussed above to not use any extra space by simple trickery.

The python code for it is given below:

```python
def productExceptSelf(nums):
    n = len(nums)
    result = [1] * n

    for i in range(1, n):
        result[i] = result[i-1] * nums[i-1]
        
    r_prod = 1

    for i in range(n-1, -1, -1):
        result[i] = r_prod * result[i]
        r_prod *= nums[i]

    return result
```

<code>
Time Complexity: O(N)
<br/>
Space Complexity: O(1) [Extra space not used - Disregarding result array]
</code>
<br/><br/>

___Best of Luck! Later.___