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
- Optimal: For the stack object, just initialize two stacks (as lists) one where its the normal stack and the other for the minimum element at the top. `int pop()` is self-explanatory, just use the `pop()` function in python. 
