
### Arrays and Strings

**Definition:** both arrays and strings represents an ordered group of elements
#### Arrays
- Python uses lists as arrays, initialization is as follows: `arr = []`
- An array can't be resized while a dynamic array (or list) can be, in algorithms it's always a dynamic array

#### Strings
- Python strings are immutable, which means it's a type of data that can't be changed
- Example: imagine you have mutable array, `arr = ["a", "b", "c"]` and immutable string `s = "abc"` and you want to change `"c"` to `"d"` you can do `arr[2] = "d"` but not `s[2] = "d"`

#### Time Complexity of Arrays/Strings

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

#### Dynamic Sliding Window

**First scenario:** Defining a criteria to make a subarray valid. There are 2 components to making a subarray valid:
1. A constraint metric. This could mean like the sum, unique number of elements, the frequency of a specific element.
2. A numeric restriction on constraint metric. This is what the constraint metric should be for a a subarray to be valid.

**Second scenario:** Problem will ask to find valid subarrays in some way such as:
1. Finding the best valid subarray.
2. Finding the number of valid subarrays.

#### Algorithm
1. Initially have we `l = r = 0`  meaning the first subarray is just the first element
2. To expand size of "window" we do `r += 1`, adding this element to our window
3. If after adding new element, subarray becomes invalid, we remove element by `l += 1`
4. As we are adding and removing elements, we are "sliding" our window along the input from left to right

#### Implementation
Example: find longest subarray with a sum less than or equal to k

```Python
def fn(nums, k):
	l = 0
	curr = 0
	ans = 0
	for r in range(len(nums)):
		curr += nums[r]
		while curr > k:
			curr -= nums[l]
			l += 1
		ans = max(ans, r-l+1)
	return ans
```
- `curr` tracks our current sum so adding element is `curr += nums[r]` and removing is `curr -= nums[l]`
- Since  `r` is always moving forward, just use for loop to iterate while `l` is only when we want to shrink the window, which is when subarray becomes invalid or `curr > k`
- When we add new element, we may have to remove multiple elements before it which is why we used the `while` loop

#### Time Complexity
- Any algorithm that looks at every subarray will run at $O(n^2)$, but sliding window has a maximum of $2n$ window iterations, so runs on $O(n)$ time complexity

#### Fixed Sliding Window
- Sometimes, a sliding window problem could have a fixed length of `k`
- The main idea is that the difference between two adjacent windows is only two elements (add one element to right and removing one element left)

```Python
def fn(arr, k):
	curr = # some data to track window

	# build first window
	for i in range(k):
		# do something with curr to build first window

	ans = # some answer variable (could be equal to curr)
	for i in range(k, len(arr)):
		# add arr[i] to window
		# remove arr[i-k] to window
		# update ans

	return ans
```


### Prefix Sum

#### Algorithm
- Create an array `prefix` where `prefix[i]` is the sum of all elements until `i` (inclusive).
- When subarray starts at index `0` it is a prefix of the array. A prefix sum is the sum of all prefixes.
- Sum of subarray from `i` to `j` is `prefix[j] - prefix[i - 1]`
	- Works because `prefix[i - 1]` is the sum of all elements before element `i`
	- and `prefix[j]` is the sum of all elements until `j`

#### Implementation

```Python

```