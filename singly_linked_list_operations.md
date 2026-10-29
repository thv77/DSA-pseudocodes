# Pseudocode: Singly Linked List Operations

Each node contains data and a next link. Initialize head ← NULL.

## INSERT AT BEGINNING

~~~text
ALGORITHM InsertFront(head, value)
    node ← CREATE_NODE(value)
    IF node = NULL THEN
        OUTPUT "Allocation failed"
        RETURN head
    END IF
    node.next ← head
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
        RETURN node
    END IF
    current ← head
    WHILE current.next ≠ NULL
        current ← current.next
    END WHILE
    current.next ← node
    RETURN head
END ALGORITHM
~~~

## INSERT AFTER A KEY

~~~text
ALGORITHM InsertAfter(head, key, value)
    current ← head
    WHILE current ≠ NULL AND current.data ≠ key
        current ← current.next
    END WHILE
    IF current = NULL THEN
        OUTPUT "Key not found"
        RETURN head
    END IF

    node ← CREATE_NODE(value)
    IF node = NULL THEN
        OUTPUT "Allocation failed"
        RETURN head
    END IF
    node.next ← current.next
    current.next ← node
    RETURN head
END ALGORITHM
~~~

## DELETE FROM BEGINNING

~~~text
ALGORITHM DeleteFront(head)
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN head
    END IF
    temp ← head
    head ← head.next
    FREE temp
    RETURN head
END ALGORITHM
~~~

## DELETE FROM END

~~~text
ALGORITHM DeleteEnd(head)
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN head
    END IF
    IF head.next = NULL THEN
        FREE head
        RETURN NULL
    END IF

    current ← head
    WHILE current.next.next ≠ NULL
        current ← current.next
    END WHILE
    FREE current.next
    current.next ← NULL
    RETURN head
END ALGORITHM
~~~

## DELETE BY KEY

~~~text
ALGORITHM DeleteKey(head, key)
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN head
    END IF
    IF head.data = key THEN
        temp ← head
        head ← head.next
        FREE temp
        RETURN head
    END IF

    previous ← head
    current ← head.next
    WHILE current ≠ NULL AND current.data ≠ key
        previous ← current
        current ← current.next
    END WHILE
    IF current = NULL THEN
        OUTPUT "Key not found"
        RETURN head
    END IF

    previous.next ← current.next
    FREE current
    RETURN head
END ALGORITHM
~~~

## DISPLAY

~~~text
ALGORITHM DisplayList(head)
    current ← head
    WHILE current ≠ NULL
        OUTPUT current.data
        current ← current.next
    END WHILE
END ALGORITHM
~~~

**Time:** Search and end operations O(n); insertion/deletion at the beginning O(1).
