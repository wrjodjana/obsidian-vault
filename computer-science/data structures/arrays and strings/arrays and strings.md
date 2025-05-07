
**Definition:** both arrays and strings represents an ordered group of elements

### Arrays
- Python uses lists as arrays, initialization is as follows: `arr = []`
- An array can't be resized while a dynamic array (or list) can be, in algorithms it's always a dynamic array

### Strings
- Python strings are immutable, which means it's a type of data that can't be changed
- Example: imagine you have mutable array, `arr = ["a", "b", "c"]` and immutable string `s = "abc"` and you want to change `"c"` to `"d"` you can do `arr[2] = "d"` but not `s[2] = "d"`

### Time Complexity of Arrays/Strings

| Operation               | Array/List | String (immutable) |
| ----------------------- | ---------- | ------------------ |
| Appending to end        | O(1)*      | O(n)               |
| Popping from end        | O(1)       | O(n)               |
| Insertion, not from end | O()        |                    |
