# Pseudocode: Circular Queue Using an Array

A circular queue reuses array positions by wrapping indices around. Initialize front ← -1 and rear ← -1; array capacity is MAX.

## ENQUEUE

~~~text
ALGORITHM CircularEnqueue(queue, front, rear, MAX, item)
    IF (rear + 1) MOD MAX = front THEN
        OUTPUT "Queue Overflow"
        RETURN (front, rear)
    END IF

    IF front = -1 THEN
        front ← 0
        rear ← 0
    ELSE
        rear ← (rear + 1) MOD MAX
    END IF

    queue[rear] ← item
    RETURN (front, rear)
END ALGORITHM
~~~

## DEQUEUE

~~~text
ALGORITHM CircularDequeue(queue, front, rear, MAX)
    IF front = -1 THEN
        OUTPUT "Queue Underflow"
        RETURN (front, rear, EMPTY)
    END IF

    item ← queue[front]
    IF front = rear THEN
        front ← -1
        rear ← -1
    ELSE
        front ← (front + 1) MOD MAX
    END IF
    RETURN (front, rear, item)
END ALGORITHM
~~~

## DISPLAY

~~~text
ALGORITHM DisplayCircularQueue(queue, front, rear, MAX)
    IF front = -1 THEN
        OUTPUT "Queue is empty"
        RETURN
    END IF

    i ← front
    REPEAT
        OUTPUT queue[i]
        IF i = rear THEN
            BREAK
        END IF
        i ← (i + 1) MOD MAX
    UNTIL FALSE
END ALGORITHM
~~~

**Time:** Enqueue O(1), Dequeue O(1), Display O(n). **Space:** O(MAX).
