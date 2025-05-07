
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
- Appending to end is [amortized O(1)](https://stackoverflow.com/questions/33044883/why-is-the-time-complexity-of-pythons-list-append-method-o1)

### Two Pointers

**Definition:** Having two integer variables that both move along an iterable, usually named `left` and `right`

**First Method:** Start pointers at edge of the input, move towards each other until they meet

```Python
def fn(arr):
	l = 0
	r = len(arr) - 1
	while l < r:
		# do something based on problem
		# do some more logic to decide on the following:
			1. l += 1
			2. r -= 1
			3. Both l += 1 and r -= 1
```
- There will never be more than $O(n)$ iterations because pointers start $n$ away from each other

**Second Method:** Move along both inputs simultaneously until all elements checked

```Python
def fn(arr1, arr2):
	i = j = 0
	while i < len(arr1) and j < len(arr2):
		# do something based on problem
		# do some more logic to decide on the following:
			1. i += 1
			2. j += 1
			3. Both i += 1 and j += 1
	
	# make sure both iterables are exhausted
	while i < len(arr1):
		# do some more logic based on problem
		i += 1
	
	while j < len(arr2):
		# do some more logic based on problem
		j += 1
```
- The time complexity of this method is $O(m+n)$ where $n = len(arr1)$ and $m = len(arr2)$

### Sliding Window

#### Subarrays
- A contiguous section of an array where all elements are adjacent and in original order
- For example, `arr = [1,2,3,4]` has subarrays:
	- `[1],[2],[3],[4]`
	- `[1,2], [2,3], [3,4]`
	- `[1,2,3], [2,3,4]`
	- `[1,2,3,4]`
- A subarray is defined by two indices, the start and end
- For example, subarray `[2,3]` has start index `1` and end index `2`, meaning `1` is the left bound and `2` is the right bound

![[subarray.png | center]]

#### Using Sliding Window

**First scenario:** Defining a criteria to make a subarra  