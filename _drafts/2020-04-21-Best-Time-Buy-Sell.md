---
layout: post
title:  "Best Time to Buy and Sell Stock Series from LeetCode - The Complete Guide"
date:   2020-04-21
desc: "Best Time to Buy and Sell Stock Series #1-6 from LeetCode"
keywords: "coding, competitive coding, leetcode, hackerrank, interview, question"
categories: [Leetcode]
tags: [Best Time to Buy and Sell Stocks, Stocks, LeetCode, Interview Question]
icon: icon-html
---

Hello everyone! I am back again with some of the most asked interview questions out there in the industry right now. It is the Best Time to Buy and Sell Stock series. There are a total of 4 questions based on the same idea of buying and selling stock. We will solve them all one by one.

Let jump into it!
<br/><br/>

## Best Time to Buy and Sell Stock - I
-------------------------------------

### Problem Statement
-------------------------------------
You can find the problem statement here: [Best Time to Buy and Sell Stock - LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
<br/><br/>

### Solution(s)
-------------------------------------
Well, this one is the most simplest of all. We just need to buy and sell the stock only once all the while maximizing the profit. If you think about it, a straight-forward solution can be made using a brute-force approach with two loops. Not good enough for FAANG. The time complexity in that case would quadratic and we can do much better here.

With some more thought, it will become clear that we need to buy at the minimum price and sell in order to maximize the profit. We can then simple go throught the prices array only once while keeping track of the minimum price and maximum profit possible.

The python code looks something like this:

```python
def maxProfit(prices):
    if len(prices) < 2:
        return 0
    min_price = float('inf')
    max_profit = float('-inf')

    for price in prices:
        max_profit = max(max_profit, price - min_price)
        min_price = min(min_price, price)
    
    return max_profit
```

On evaluation, the computational complexities of this solution would be:

<code>
Time Complexity: O(N)
<br/>
Space Complexity: O(1)
</code>
<br/><br/>

## Best Time to Buy and Sell Stock - II
-------------------------------------

### Problem Statement
-------------------------------------
You can find the problem statement here: [Best Time to Buy and Sell Stock II -  LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)
<br/><br/>

### Solution(s)
-------------------------------------
The problem statement here has been slightly changed and now we have the liberty to buy and sell stocks as many times as we want. We can choose to make some transactions which in turn maximizes the profit and it seems difficult to think of a solution at first sight.

Let's evaluate an approach that we learn in our algorithms class called the Greedy approach for this problem.

Consider three consecutive indices i, j and k in the prices array (i < j < k). All the possible cases for the prices are,

i. `prices[i] < prices[j] < prices[k]`

ii. `prices[i] < prices[j]` and `prices[j] > prices[k]` and `prices[i] > prices[k]`

iii. `prices[i] < prices[j]` and `prices[j] > prices[k]` and `prices[i] < prices[k]`

iv. `prices[i] > prices[j] > prices[k]`

v. `prices[i] > prices[j]` and `prices[j] < prices[k]` and `prices[i] > prices[k]`

vi. `prices[i] > prices[j]` and `prices[j] < prices[k]` and `prices[i] < prices[k]`

Pardon me for covering all the 6 permutations but it is a much simpler method to prove that the greedy approach works for this method rather than trying to mathematically prove it.

In all cases, you can see that the maximum profit can be gained simply by adding the difference between two consecutive indices if the difference results in a profit. We can simple make multiple transactions whenever two adjacent values allow us to make a profit and the answer should be the sum of profits of all such transactions.

It has been also demonstrated in the picture below from LeetCode's solution as well.

<div align="center">
  <img width="460" height="300" src="/static/assets/img/blog/best-time-buy-sell/122_maxprofit_1.png">
</div>

The python code for the optimal solution i.e. the greedy approach is given below:

```python
def maxProfit(prices):
    n = len(prices)
    if n < 2:
        return 0
    
    total_profit = 0

    for i in range(n-1):
        total_profit += max(prices[i+1]-prices[i], 0)
    
    return total_profit
```

<code>
Time Complexity: O(N)
<br/>
Space Complexity: O(1)
</code>
<br/><br/>

## Best Time to Buy and Sell Stock - III
-------------------------------------

### Problem Statement
-------------------------------------
You can find the problem statement here: [Best Time to Buy and Sell Stock III -  LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)
<br/><br/>

### Solution(s)
-------------------------------------
