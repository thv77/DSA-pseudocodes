# Algorithm: Queue Operations Using Array

**Step 1:** Start.

**Step 2:** Initialize `rear = -1`, `front = 0`, and create a queue array of size 3.

**Step 3:** Display the menu:
1. Enqueue (insert an element)
2. Dequeue (delete an element)
3. Display elements
4. Exit

**Step 4:** Read the choice.

**Step 5: If choice = 1 (Enqueue)**
- Read the element.
- Check whether `rear == maxsize - 1`.
- If true, display **"Queue Overflow"**.
- Otherwise, increment `rear` and insert the element into `queue[rear]`.
- Return to the menu.

**Step 6: If choice = 2 (Dequeue)**
- Check whether `rear == -1 && front == 0`.
- If true, display **"Queue Underflow"**.
- Otherwise, store `queue[front]` in `data`, increment `front`, and display **"One element is successfully deleted"**.
- Return to the menu.

**Step 7: If choice = 3 (Display)**
- Start from `front`.
- Traverse up to `rear` and display each element.
- Return to the menu.

**Step 8: If choice = 4 (Exit)**
- Display **"Have a nice day"**.
- Terminate the program.

**Step 9:** For any other choice, display **"Wrong choice"**.

**Step 10:** Stop.
