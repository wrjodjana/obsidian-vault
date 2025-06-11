>[!question]
>You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.
>
>You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.
>
>Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.

**Initial Questions**
1. Are prices always integers, or could they be floats?
2. What should i return for empty array or array with one element?

**Explanation**
- Brute Force: Basically loop through the entire array twice, and using the two indexes find the profit which is the sell price minus the buy price. Keep on updating this profit with a variable outside of the loop - time complexity: $O(n^2)$
- Optimal: Hold a left pointer and loop through the array from the second value using a right pointer. If the value at the left pointer is smaller then at the right pointer then find the profit and update the maximum profit. If not, move the left pointer to the right pointer's position.

**Code**
```Python
def maxProfit(prices):
	l = 0
	max_profit = 0

	for r in range(1, len(prices)):
		if prices[l] < prices[r]:
			curr_profit = prices[r] - prices[l]
			max_profit = max(max_profit, curr_profit)
		else:
			l = r

	return max_profit
```

**Algorithm Complexity**
- Time Complexity: $O(n)$ since we are looping through the array once, where $n$ is the length of the array
- Space Complexity: $O(1)$ since we are not using any additional data structures and all variables are constant time

