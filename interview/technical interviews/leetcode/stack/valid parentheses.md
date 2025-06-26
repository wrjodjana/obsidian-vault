>[!question]
>Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.
>An input string is valid if:
>1. Open brackets must be closed by the same type of brackets.
>2. Open brackets must be closed in the correct order.
>3. Every close bracket has a corresponding open bracket of the same type.

**Initial Questions**
- What would happen if the string was empty?
- Imagine we had a scenario like `([]}`, would this return false?

**Explanation**
- Optimal: Using a stack to keep adding the open brackets in the list, then if we reach a close bracket then check if the top of the stack is that corresponding open bracket to that close bracket. If not, then we return false. If it is then continue until the string is finished then do a final check to see if the stack is empty.

