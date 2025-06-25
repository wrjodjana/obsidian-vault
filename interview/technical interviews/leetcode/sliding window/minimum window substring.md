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
	
```