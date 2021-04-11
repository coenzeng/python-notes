---
tags: [array]
title: Best Time to Buy and Sell a Stock II
created: '2021-04-10T23:09:58.281Z'
modified: '2021-04-11T03:24:23.039Z'
---

## Best Time to Buy and Sell a Stock II
:penguin: **·** `Arrays` **·** `Easy`

You are given an array prices where prices[i] is the price of a given stock on the ith day.

Find the maximum profit you can achieve. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

#### Solution 1: Simple One Pass
```python
profit = 0
for i in range(len(prices) - 1):
    if prices[i] < prices[i + 1]:
        profit += prices[i + 1] - prices[i]

return profit
```





