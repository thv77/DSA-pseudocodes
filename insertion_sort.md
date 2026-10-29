# Pseudocode: Insertion Sort

Insertion sort builds a sorted section one element at a time by shifting larger elements right.

~~~text
ALGORITHM InsertionSort(A, n)
    FOR i ← 1 TO n - 1
        key ← A[i]
        j ← i - 1
        WHILE j ≥ 0 AND A[j] > key
            A[j + 1] ← A[j]
            j ← j - 1
        END WHILE
        A[j + 1] ← key
    END FOR
    OUTPUT A
    RETURN A
END ALGORITHM
~~~

**Time:** Best O(n); average and worst O(n²). **Auxiliary space:** O(1). Stable when equal elements are not shifted past each other.
