# Pseudocode: Binary Search

**Input:** Sorted array A with n elements and search key key  
**Output:** Index of key, or -1 if absent

Binary search requires the array to be sorted in ascending order.

~~~text
ALGORITHM BinarySearch(A, n, key)
    low ← 0
    high ← n - 1

    WHILE low ≤ high
        mid ← floor((low + high) / 2)
        IF A[mid] = key THEN
            RETURN mid
        ELSE IF A[mid] < key THEN
            low ← mid + 1
        ELSE
            high ← mid - 1
        END IF
    END WHILE

    RETURN -1
END ALGORITHM
~~~

**Time:** O(log n). **Auxiliary space:** O(1).
