# Pseudocode: Merge Sort

Merge sort uses divide and conquer: recursively sort each half, then merge the sorted halves.

## MAIN ALGORITHM

~~~text
ALGORITHM MergeSort(A, left, right)
    IF left ≥ right THEN
        RETURN
    END IF
    mid ← floor((left + right) / 2)
    MergeSort(A, left, mid)
    MergeSort(A, mid + 1, right)
    Merge(A, left, mid, right)
END ALGORITHM
~~~

## MERGE TWO SORTED PARTS

~~~text
ALGORITHM Merge(A, left, mid, right)
    CREATE empty temporary array T
    i ← left
    j ← mid + 1

    WHILE i ≤ mid AND j ≤ right
        IF A[i] ≤ A[j] THEN
            APPEND A[i] TO T
            i ← i + 1
        ELSE
            APPEND A[j] TO T
            j ← j + 1
        END IF
    END WHILE

    WHILE i ≤ mid
        APPEND A[i] TO T
        i ← i + 1
    END WHILE
    WHILE j ≤ right
        APPEND A[j] TO T
        j ← j + 1
    END WHILE

    COPY T into A[left ... right]
END ALGORITHM
~~~

**Initial call:** MergeSort(A, 0, n - 1)  
**Time:** O(n log n) in all cases. **Auxiliary space:** O(n).
