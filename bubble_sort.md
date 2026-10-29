# Bubble Sort

## Algorithm

1. START
2. Read the number of elements, `n`.
3. Read `n` elements into array `A`.
4. Repeat for each pass `j` from 1 to `n - 1`:
   - Compare adjacent elements from index 0 to `n - j - 1`.
   - If `A[i] > A[i + 1]`, swap the two elements.
5. Output the sorted array in ascending order.
6. STOP

## Pseudocode

```text
ALGORITHM BubbleSort
    READ n
    READ array A of n elements

    FOR j = 1 TO n - 1
        FOR i = 0 TO n - j - 1
            IF A[i] > A[i + 1] THEN
                temp = A[i]
                A[i] = A[i + 1]
                A[i + 1] = temp
            END IF
        END FOR
    END FOR

    OUTPUT A
END ALGORITHM
```

## Complexity

- Best case: O(n²) for this implementation (it always completes every pass).
- Average case: O(n²)
- Worst case: O(n²)
- Auxiliary space: O(1)

## Note

This version sorts the array in ascending order by comparing and swapping adjacent elements. It does not use an early-exit flag, so even an already sorted array takes O(n²) time.
