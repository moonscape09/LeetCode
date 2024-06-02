<h1>Question: <a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/">Buy and Sell Stock II</a></h1>

```
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        n = len(prices)
        buyDay = 0
        sellDay = 0
        currentProfit = 0
        maxProfit = 0
        for i in range(n):
            if prices[i] <= prices[buyDay]:
                buyDay = i
                sellDay = i
            
            if prices[i] - prices[buyDay] > currentProfit:
                sellDay = i
                currentProfit = prices[sellDay] - prices[buyDay]
            else: 
                maxProfit += currentProfit
                currentProfit = 0
                buyDay = i

            if i == n - 1:
                maxProfit += currentProfit
        
        return maxProfit
            
```

**Data structures used**: Array

**Time complexity**: O(n)

**Space complexity**: O(1)

<h3>Function</h3>
Given an array of integers `prices` where `prices[i]` is the price of a given stock on `ith` day. At most one stock can be held at a time, and must be bought before it is sold. Returns the maximum profit achieved.


**Parameters:**
- <code>prices</code>: non-empty array of integers

**Variables:**
- <code>buyDay</code> and <code>sellDay</code>: index variables representing the day (`i`) to buy and sell respectively

- <code>currentProfit</code>: tracks the current profit as the array is being traversed

**Return value:**
- <code>maxProfit: int </code>

**Explanation:**
A greedy approach is used to determine the maximum profit that can be achieved from the `prices` array. We traverse the array to check various conditions with the current `i` or day we are on.

First, we check for if the price is lower than what our current `buyDay` is set to, and to maximize profits we will reassign if true. As the `sellDay` must be >= `buyDay` (sell day should be the same or later) then we also set the `sellDay` to the same day.

Then we check for if the profit is larger than what we have set in our intermediate `currentProfit` variable. Note that this condition also addresses the case for holding one stock at a time, as simply if we approach a lower value than the current `buyDay`, then the difference would be negative which is lower than our initial `currentProfit` value: 0.

If the profit is larger, then we reassign our `sellDay` and consequently the `currentProfit`.

If not, then we have attained the maximum profit so far and we cumulatively add these profits to our return variable: `maxProfit`. Then we reset the `currentProfit` and set the `buyDay` to the current day to find a new stock/profit.

Lastly, we have addressed an edge case where we have a strictly increasing array and we don't assign a `sellDay` anywhere. Hence we have reached the last day and added up our `maxProfit`.

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>prices = [0]</code>  | 0 |
| <code>prices = "[1,2,3,4,5]"</code>  | 4 |
| <code>prices = "[7,1,5,3,6,4]"</code> | 7 |
| <code>prices = "[7,6,4,3,1]"</code> | 0 |

**Statistics**: beat 83% of solutions in runtime and 99% of solutions in memory usage.

<img width="360" alt="image" src="https://github.com/moonscape09/LeetCode/assets/101025804/92e534c3-5239-4008-9d25-14203e1722eb">
