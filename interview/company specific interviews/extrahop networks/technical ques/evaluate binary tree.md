>[!question]
>Consider a binary tree representing an expression, where each node is a string representing either a function ("add", "subtract", or "square") or a number ("1", "2", "1634", etc.). If the node is a function, its subtree(s) represent the argument(s). Write a function that evaluates the expression, and returns the result as a string.
>
>To start, assume that the tree will represent a valid expression.

Answer:
```Python

class TreeNode:
	def __init__(self, val, left, right):
		self.val = val
		self.right = right
		self.left = left

def evaluate_tree(root):
	if not root:
		return None

	left = evaluate_tree(root.left)
	right = evaluate_tree(root.right)

	if root.val == "add":
		if left is None or right is None:
			return None
		return str(int(left) + int(right))

	if root.val == "subtract":
		if left is None or right is None:
			return None
		return str(int(left) - int(right))

	if root.val == "square":
		if left is None and right is None:
			return None
		if left is None:
			return str(int(right) ** 2)
		if right is not None:
			return None
		return str(int(left) ** 2)

	if left is not None or right is not None:
		return None

	try:
		return str(int(root.val))
	except ValueError:
		return None
```

Extensions:

Add error handling: Return the string “Invalid” if the tree represents an invalid expression
- just replace return None in the errors to "Invalid"

Handle more functions, such as “multiply”, “min”, “max”

```Python
if root.val == "multiply":
	if left is None or right is None:
		return "Invalid"
	return str(int(left) * int(right))

if root.val == "min":
	if left is None or right is None:
		return "Invalid"
	return str(min(int(left), int(right)))

if root.val == "max":
	if left is None or right is None:
		return "Invalid"
	return str(max(int(left), int(right)))
```

Write some more test cases

`("multiply", ("3", null, null), ("4", null, null))` → "12"
`("min", ("5", null, null), ("3", null, null))` → "3"
