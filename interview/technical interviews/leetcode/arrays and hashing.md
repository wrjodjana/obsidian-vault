
**Longest Common Prefix**
- Initialize the first string in array as our first prefix, then continually reduce it by using another pointer to check if the first string's characters are equal to the rest of the ones in the array

**Remove Element**
- Use the end of the element as a missing number, then loop through the array using another pointer, then do in place operations using that end of element

**Majority Element**
- Sort the array then use the n // 2 value as the index

**Valid Sudoku**
- Use different sets to track the digits in each row, column and sub boxes, then check if the current value exists in the current row, column or sub boxes (return False). Check if it's the dot meaning that its an empty space so continue and then finally add back the digits 