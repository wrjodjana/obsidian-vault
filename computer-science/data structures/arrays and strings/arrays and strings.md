
**Definition:** both arrays and strings represents an ordered group of elements

### Arrays
- Python uses lists as arrays, initialization is as follows: `arr = []`
- An array can't be resized while a dynamic array (or list) can be, in algorithms it's always a dynamic array

### Strings
- Python strings are immutable, which means it's a type of data that can't be changed
- Example: imagine you have mutable array, `arr = ["a", "b", "c"]` and immutable string `s = "abc"` and you want to change `"c"` to `"d"` you can do `arr[2] = "d"` but not `s[2] = "d"`

### Time Complexity of Arrays/Strings

| Operation                  | Array/List | String (immutable) |
| -------------------------- | ---------- | ------------------ |
| Appending to end           | $O(1)$*    | $O(n)$             |
| Popping from end           | $O(1)$     | $O(n)$             |
| Insertion, not from end    | $O(n)$     | $O(n)$             |
| Deletion, not from end     | $O(n)$     | $O(n)$             |
| Random access              | $O(1)$     | $O(1)$             |
| Modifying an element       | $O(1)$     | $O(n)$             |
| Checking if element exists | $O(n)$     | $O(n)$             |
- appending to end is [amortized O(1)](https://stackoverflow.com/questions/33044883/why-is-the-time-complexity-of-pythons-list-append-method-o1)

### Two Pointers

**Definition:** having two integer variables that both move along an iterable, usually named `left` and `right`

**First Method:** start pointers at edge of the input, move towards each other until they meet

```Python
def fn(arr):
	l = 0
	r = len(arr) - 1
	while l < r:
		# do something based on logic based on problem
		# do some more logic to decide on the following:
			1. l += 1
			2. r -= 1
			3. Both l += 1 and r -= 1
```
- there will never be more than $O(n)$ iterations because pointers start $n$ away from each other

**Second Method:** 
