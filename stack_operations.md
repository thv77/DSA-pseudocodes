# Pseudocode: Stack Operations Using an Array

A stack follows **LIFO** (Last In, First Out). Initialize top ← -1 for an array of capacity MAX.

## PUSH

~~~text
ALGORITHM Push(stack, top, MAX, item)
    IF top = MAX - 1 THEN
        OUTPUT "Stack Overflow"
        RETURN top
    END IF
    top ← top + 1
    stack[top] ← item
    RETURN top
END ALGORITHM
~~~

## POP

~~~text
ALGORITHM Pop(stack, top)
    IF top = -1 THEN
        OUTPUT "Stack Underflow"
        RETURN (top, EMPTY)
    END IF
    item ← stack[top]
    top ← top - 1
    RETURN (top, item)
END ALGORITHM
~~~

## DISPLAY

~~~text
ALGORITHM DisplayStack(stack, top)
    IF top = -1 THEN
        OUTPUT "Stack is empty"
        RETURN
    END IF
    FOR i ← top DOWNTO 0
        OUTPUT stack[i]
    END FOR
END ALGORITHM
~~~

**Time:** Push O(1), Pop O(1), Display O(n). **Space:** O(MAX).
