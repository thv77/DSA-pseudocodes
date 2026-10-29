# Pseudocode: Doubly Linked List Operations

Each node stores data, prev, and next. Initialize head ← NULL.

## INSERT AT BEGINNING

~~~text
ALGORITHM InsertFront(head, value)
    node ← CREATE_NODE(value)
    IF node = NULL THEN
        OUTPUT "Allocation failed"
        RETURN head
    END IF
    node.prev ← NULL
    node.next ← head
    IF head ≠ NULL THEN
        head.prev ← node
    END IF
    head ← node
    RETURN head
END ALGORITHM
~~~

## INSERT AT END

~~~text
ALGORITHM InsertEnd(head, value)
    node ← CREATE_NODE(value)
    IF node = NULL THEN
        OUTPUT "Allocation failed"
        RETURN head
    END IF
    node.next ← NULL
    IF head = NULL THEN
        node.prev ← NULL
        RETURN node
    END IF

    current ← head
    WHILE current.next ≠ NULL
        current ← current.next
    END WHILE
    current.next ← node
    node.prev ← current
    RETURN head
END ALGORITHM
~~~

## DELETE BY VALUE

~~~text
ALGORITHM DeleteValue(head, key)
    current ← head
    WHILE current ≠ NULL AND current.data ≠ key
        current ← current.next
    END WHILE
    IF current = NULL THEN
        OUTPUT "Value not found"
        RETURN head
    END IF

    IF current.prev ≠ NULL THEN
        current.prev.next ← current.next
    ELSE
        head ← current.next
    END IF
    IF current.next ≠ NULL THEN
        current.next.prev ← current.prev
    END IF
    FREE current
    RETURN head
END ALGORITHM
~~~

## DISPLAY FORWARD

~~~text
ALGORITHM DisplayForward(head)
    current ← head
    WHILE current ≠ NULL
        OUTPUT current.data
        current ← current.next
    END WHILE
END ALGORITHM
~~~

## DISPLAY BACKWARD

~~~text
ALGORITHM DisplayBackward(head)
    IF head = NULL THEN
        RETURN
    END IF
    current ← head
    WHILE current.next ≠ NULL
        current ← current.next
    END WHILE
    WHILE current ≠ NULL
        OUTPUT current.data
        current ← current.prev
    END WHILE
END ALGORITHM
~~~

**Time:** Traversal/search O(n); insertion at beginning O(1).
