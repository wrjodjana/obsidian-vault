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
			return "Invalid"
		return str(int(left) + int(right))

	if root.val == "subtract":
		if left is None or right is None:
			return "Invalid"
		return str(int(left) - int(right))

	if root.val == "square":
		if left is None and right is None:
			return "Invalid"
		if left is None:
			return str(int(right) ** 2)
		if right is not None:
			return "Invalid"
		return str(int(left) ** 2)

	if left is not None or right is not None:
		return "Invalid"
	
```