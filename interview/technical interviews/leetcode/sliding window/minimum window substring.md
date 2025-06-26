>[!question]
>Given two strings `s` and `t` of lengths `m` and `n` respectively, return _the **minimum window**_ **_substring_** _of_ `s` _such that every character in_ `t` _(**including duplicates**) is included in the window_. If there is no such substring, return _the empty string_ `""`.
>
>The testcases will be generated such that the answer is **unique**.

**Initial Questions:**
- What happens when the length of `t` is greater then the length of `s`?

**Explanation**
- Optimal: Using sliding window approach by having one pointer going over the array and the other resizing the window. Add the current character into our window continuously then check if this character is also inside `t`. We resize the window when the number of characters in `t` is equal to the unique characters of `t` in the current window. Next, we update the minimum window and start resizing the window by removing the character and incrementally moving the second pointer. 

**Code:**
```Python
def minWindow(s, t):
	t_freq = defaultdict(int)
	for c in t:
		t_freq[c] += 1

	required = len(t_freq)

	l = 0
	min_start = 0
	min_len = float("inf")

	unique_char = 0
	curr_freq = defaultdict(int)

	for r in range(len(s)):
		curr_freq[s[r]] += 1

		if s[r] in t_freq and curr_freq[s[r]] == t_freq[s[r]]:
			unique_char += 1

		while l <= r and required == unique_char:
			if r-l+1 < min_len:
				min_len = r-l+1
				min_start = l

			curr_freq[s[l]] -= 1
			if s[l] in t_freq and curr_freq[s[l]] == t_freq[s[l]]:
				unique_char -= 1

			l += 1

	return s[min_start:min_start+min_len] if min_len != float("inf") else ""
```

**Algorithm Complexity:**
- Time Complexity: $O(t + s)$ since we are building the frequency map of string `t` and each character in `s` is visited at most twice
- Space Complexity: $O(t + s)$ since the max number of characters stored in both frequency maps is equal to the number of characters in `s` and `t` respectively

