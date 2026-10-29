# Pseudocode: Linear Queue Operations Using an Array

A linear queue follows **FIFO** (First In, First Out). Initialize front ← 0, rear ← -1, and use an array of capacity MAX.

## ENQUEUE

~~~text
ALGORITHM Enqueue(queue, front, rear, MAX, item)
    IF rear = MAX - 1 THEN
        OUTPUT "Queue Overflow"
        RETURN (front, rear)
    END IF
    rear ← rear + 1
    queue[rear] ← item
    RETURN (front, rear)
END ALGORITHM
~~~

## DEQUEUE

~~~text
ALGORITHM Dequeue(queue, front, rear)
    IF front > rear THEN
        OUTPUT "Queue Underflow"
        RETURN (front, rear, EMPTY)
    END IF
    item ← queue[front]
    front ← front + 1

    IF front > rear THEN
        front ← 0
        rear ← -1
    END IF
    RETURN (front, rear, item)
END ALGORITHM
~~~

## DISPLAY

~~~text
ALGORITHM DisplayQueue(queue, front, rear)
    IF rear = -1 THEN
        OUTPUT "Queue is empty"
        RETURN
    END IF
    FOR i ← front TO rear
        OUTPUT queue[i]
    END FOR
END ALGORITHM
~~~

A linear queue may leave unused positions at the beginning after deletions; a circular queue reuses those positions.

**Time:** Enqueue O(1), Dequeue O(1), Display O(n).
