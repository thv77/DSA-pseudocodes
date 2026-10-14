# Algorithm: Circular Queue Using Array

**Step 1:** Start.

**Step 2:** Initialize `front = -1`, `rear = -1), and create a queue array of size 3.

**Step 3:** Display the menu:
1. Enqueue — Insert an element
2. Dequeue — Delete an element
3. Display elements
4. Exit

**Step 4:** Read the choice.

## Enqueue

**Step 5: If choice = 1 (Enqueue)**
- Read the element.
- Check whether `front == (rear + 1) % maxsize`.
- If true, display **"Queue Overflow"**.
- Otherwise, check whether `front == -1 && rear == -1`.
  - If true, set `front = 0), `rear = 0), and insert the element at `queue[rear]`.
  - Otherwise, set `rear = (rear + 1) % maxsize` and insert the element at `queue[rear]`.
- Return to the menu.

## Dequeue

**Step 6: If choice = 2 (Dequeue)**
- Check whether `rear == -1 && front == -1`.
- If true, display **"Queue Underflow"**.
- Otherwise, check whether `rear == front`.
  - If true, delete `queue[front]` and set `front = -1) and `rear = -1`.
  - Otherwise, delete `queue[front]` and set `front = (front + 1) % maxsize`.
- Return to the menu.

## Display

**Step 7: If choice = 3 (Display)**
- Start from `i = front`.
- Display `queue[i]`.
- Repeat `i = (i + 1) % maxsize` until `i == rear`.
- Finally, display `queue[rear]`.
- Return to the menu.

**Step 8: If choice = 4 (Exit)**
- Display **"Have a nice day"**.
- Terminate the program.

**Step 9:** For any other choice, display **"Wrong choice"**.

**Step 10:** Stop.
