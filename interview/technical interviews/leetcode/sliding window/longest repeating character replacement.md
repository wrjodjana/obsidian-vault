>[!question]
>You are given a string `s` and an integer `k`. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most `k` times.
>
>Return _the length of the longest substring containing the same letter you can get after performing the above operations_.

**Questions:**
1. What's the maximum number of unique characters in string `s`?
2. Could integer `k` be a negative value or 0, and how to handle those cases?

**Explanation:**
- Brute force: Checking every possible substring and checking if it can have all same characters with at most `k` changes.
- Optimal: Use sliding window when it's a valid substring. Keep track of the frequency of the current character in the window and track the count of the most frequent character in the window. Then find the current number of changes needed which is the substring length minus the count of the most frequent number. If this value exceeds the `k` then we shorten the window, then update the result of the current window.