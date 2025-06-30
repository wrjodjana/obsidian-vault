>[!question]
>Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.
>Implement the `MinStack` class:
>- `MinStack()` initializes the stack object.
>- `void push(int val)` pushes the element `val` onto the stack.
>- `void pop()` removes the element on the top of the stack.
>- `int top()` gets the top element of the stack.
>- `int getMin()` retrieves the minimum element in the stack.
>
>You must implement a solution with `O(1)` time complexity for each function.

**Initial Questions:**
1. Are we allowed to use like existing functions in Python?

**Explanation:**
- Optimal: For the stack object, just initialize two stacks (as lists) one where its the normal stack and the other for the minimum element at the top. `pop()` is self-explanatory, just use the `pop()` function in python. `top()` and `getMin()` would just be getting the top value in each stack respectively. `push(val)` is just adding the value to the normal stack then for the stack with the minimum element at the top just check if there are values, if there are then get the minimum of the smallest element and the current value and push it to the stack.

**Code:**
```Python
class MinStack:
	def __init__(self):
		self.stack = []
		self.min_stack = []

	def push(self, val):
		self.stack.append(val)
		if len(self.min_stack) == 0:
			self.min_stack.append(val)
		else:
			self.min_stack.append(min(min_stack[-1], val))

	def pop(self):
		self.stack.pop()
		self.min_stack.pop()

	def top(self):
		return self.stack[-1]

	def getMin(self):
		return self.min_stack[-1]
```

**Algorithm Complexity:**
- Time Complexity: $O(1)$ since everything is constant time
- Space Complexity: $O(n)$ since the max number of elements in the stack is $n$