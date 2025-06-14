>[!question]
>Given a string `s`, find the length of the **longest** **substring** without duplicate characters.

**Initial Questions**
1. What kind of values could "s" be? letters, digits, symbols etc.

**Explanation**
- Optimal: Using the sliding window approach by having one pointer going over the array and the other pointer resizing the window. Add characters into a set until we find a repeating character so we remove the character from the front and move left pointer. Then we update the result by the size of the window which is always `r - l + 1`.

**Code**
```Python
def lengthOfLongestSubstring(s):
	l = 0
	res = 0
	char_set = set()

	for r in range(len(s)):
		while s[r] in char_set:
			char_set.remove(s[l])
			l += 1
		char_set.add(s[r])
		res = max(res, r-l+1)

	return res
```
