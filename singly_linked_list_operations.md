# Algorithm: Single Linked List – Menu Driven

## Main Algorithm

**Step 1:** Start.

**Step 2:** Initialize `head = NULL`.

**Step 3:** Display the menu:

1. Insert at first
2. Insert at last
3. Insert after a key
4. Delete from front
5. Delete from end
6. Delete a key
7. Display
8. Exit

**Step 4:** Read the user's choice.

**Step 5:** Perform the selected operation using the corresponding algorithm below.

**Step 6:** Repeat Steps 3–5 until the user chooses Exit.

**Step 7:** Stop.

---

## Case 1 – Insert at First

**Step 1:** Create a new node.

**Step 2:** If memory allocation fails, display "Memory underflow" and stop this operation.

**Step 3:** Read the element.

**Step 4:** Store the element in the new node.

**Step 5:** Link the new node to `head`.

**Step 6:** Update `head` to the new node.

**Step 7:** Display the list.

---

## Case 2 – Insert at Last

**Step 1:** Create a new node.

**Step 2:** If memory allocation fails, display "Memory underflow" and stop this operation.

**Step 3:** Read the element and store it in the new node.

**Step 4:** If the list is empty, set the new node as `head`.

**Step 5:** Otherwise, traverse the list until the last node is reached.

**Step 6:** Link the last node to the new node and set the new node's link to `NULL`.

**Step 7:** Display the list.

---

## Case 3 – Insert After a Key

**Step 1:** Create a new node.

**Step 2:** If memory allocation fails, display "Memory underflow" and stop this operation.

**Step 3:** Read the element and the key.

**Step 4:** Search for the key in the list.

**Step 5:** If the key is found, link the new node after that node.

**Step 6:** Otherwise, display "Search fails".

**Step 7:** Display the list.

---

## Case 4 – Delete from Front

**Step 1:** If the list is empty, display "The list is empty" and stop this operation.

**Step 2:** Store `head` in a temporary pointer.

**Step 3:** Move `head` to the next node.

**Step 4:** Free the old head node.

**Step 5:** Display the list.

---

## Case 5 – Delete from End

**Step 1:** If the list is empty, display "The list is empty" and stop this operation.

**Step 2:** Set the previous and current pointers to the head node.

**Step 3:** Traverse to the last node while keeping track of the previous node.

**Step 4:** Set the previous node's link to `NULL`.

**Step 5:** Free the last node.

**Step 6:** Display the list.

---

## Case 6 – Delete a Key

**Step 1:** If the list is empty, display "The list is empty" and stop this operation.

**Step 2:** Read the key to be deleted.

**Step 3:** Search for the key while maintaining previous and current pointers.

**Step 4:** If the key is found, unlink the node from the list and free it.

**Step 5:** Otherwise, display "Search fails".

**Step 6:** Display the list.

---

## Case 7 – Display

**Step 1:** If the list is empty, display "The list is empty".

**Step 2:** Otherwise, set a pointer to `head`.

**Step 3:** Traverse from `head` to `NULL`, displaying each node's data.

---

## Case 8 – Exit

**Step 1:** Display "Have a nice day".

**Step 2:** Terminate the program.
