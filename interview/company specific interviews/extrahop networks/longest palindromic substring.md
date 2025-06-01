
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
	a. What should I return if the input array is empty?
	b. Are there any constraints on string length?
	c. Case sensitivity, ASCII values?
2. Explain approach
	a. Brute force: check every possible substring to see if its a palindrome, which would take $O(n^3)$ - $O(n^2)$ substrings, each taking $O(n)$ 
	
	b. Optimal approach:  Go through every value in the array, then use this as a center to expand outward and check for either the outward values going out of bounds or not a palindrome. There is also going to be two cases where the palindromes can have odd lengths (where center is 1 character) and palindromes that can have even lengths (where center is 2 characters) so check both cases. Finally, to return the substring hold the longest length and start variables so that we have create the substring to return

3. Test case
	a. "babad"
	- "b" 
		- odd-length:
			- `s[0] == s[0]` so `l -= 1, r += 1`
			- `l = -1`, out of bounds so stop
			- `start = 0, length = 1`
			- `1 > 1`, no so dont update 
		- even-length:
			- `s[0] != s[1] -> "b" != "a"` so dont continue
	- "a":
		- odd-length:
			- `s[1] == s[1]`, `l -= 1, r += 1`
			- `s[0] == s[2], l -= 1, r += 1`
			- `l = -1`, out of bounds so stop
			- `3 > 1`, so update `long_start = 0, long_len = 3`
		- even-length:
			- `s[1] != s[2], "a" != "b"` so dont continue

4. Time/Space Complexity
	- Time Complexity: 


