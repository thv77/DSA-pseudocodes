# Algorithm: Stack Operations Using Array

**Step 1:** Start.

**Step 2:** Initialize `top = -1` and create an array `stack` of size 5.

**Step 3:** Display the menu:
1. Push (insert an element)
2. Pop (delete an element)
3. Display elements
4. Exit

**Step 4:** Read the user's choice.

**Step 5: If choice = 1 (Push)**
- Read the element.
- Check whether `top == maxsize - 1`.
- If true, display **"Stack Overflow"**.
- Otherwise, increment `top` by 1 and insert the element at `stack[top]`.
- Return to the menu.

**Step 6: If choice = 2 (Pop)**
- Check whether `top == -1`.
- If true, display **"Stack Underflow"**.
- Otherwise, store `stack[top]` in `data`, decrement `top) by 1, and display a successful deletion message.
- Return to the menu.

**Step 7: If choice = 3 (Display)**
- Start from `top`.
- Print the elements one by one down to index 0.
- Return to the menu.

**Step 8: If choice = 4 (Exit)**
- Display **"Have a nice day"**.
- Terminate the program.

**Step 9:** If any other choice is entered, display **"Wrong choice"** and return to the menu.

**Step 10:** Stop.
