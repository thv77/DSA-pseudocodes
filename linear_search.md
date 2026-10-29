# Pseudocode: Linear Search

**Input:** Array A with n elements and search key key  
**Output:** Index of the first match, or -1 if not found

~~~text
ALGORITHM LinearSearch(A, n, key)
    FOR i ← 0 TO n - 1
        IF A[i] = key THEN
            RETURN i
        END IF
    END FOR
    RETURN -1
END ALGORITHM
~~~

**Time:** Best O(1), worst O(n). **Auxiliary space:** O(1).
