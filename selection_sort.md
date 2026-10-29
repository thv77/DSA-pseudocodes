# Pseudocode: Selection Sort

Selection sort repeatedly finds the smallest element in the unsorted section and swaps it into the next position.

~~~text
ALGORITHM SelectionSort(A, n)
    FOR i ← 0 TO n - 2
        minIndex ← i
        FOR j ← i + 1 TO n - 1
            IF A[j] < A[minIndex] THEN
                minIndex ← j
            END IF
        END FOR
        IF minIndex ≠ i THEN
            SWAP A[i] WITH A[minIndex]
        END IF
    END FOR
    OUTPUT A
    RETURN A
END ALGORITHM
~~~

**Time:** Best, average, and worst O(n²). **Auxiliary space:** O(1).
