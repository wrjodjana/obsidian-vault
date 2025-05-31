
> [!question]
> **Longest Palindromic Substring**
> Given a string s, return the longest palindromic substring in s. Note: substring means continuous characters in s
> 
> Example 1:
> Input s = "babad"
> Output: "bab"
> Explanation: "aba" is also a valid answer
> 
> Example 2:
> Input s = "cbbd"
> Output: "bb"
****

Answer:
```Python
def longestPalindrome(s):
	if not s:
		return ""

	long_start = 0
	long_len = 1

	def expand_center(l, r):
		while l >= 0 and r < len(s) and s[l] == s[r]:
			l -= 1
			r += 1
		start = l + 1
		length = (r - 1) - (l + 1) + 1
		return start, length

	for i in range(len(s)):
		start, length = expand_center(i, i)
		if length > long_len:
			long_len = length
			long_start = start

		start, length = expand_center(i, i+1)
		if length > long_len:
			long_len = length
			long_start = start

	return s[long_start:long_start+long_len]	
```


1. Questions to ask
	a. 


