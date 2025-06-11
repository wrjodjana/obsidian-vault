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
- Brute Force: Basically loop through the entire array twice, and using the two indexes find the profit which is the sell price minus the buy price. Keep on updating this profit with a variable outside of the loop
- 