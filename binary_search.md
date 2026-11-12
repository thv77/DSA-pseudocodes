# Pseudocode: Binary Search

Binary search works on a sorted array. First, sort the input array in ascending order using bubble sort. Then repeatedly compare the key with the middle element and reduce the search range by half.

## BUBBLE SORT

~~~text
ALGORITHM BubbleSort(a, n)
    FOR j ← 1 TO n - 1
        FOR i ← 0 TO n - j - 1
            IF a[i] > a[i + 1] THEN
                temp ← a[i]
                a[i] ← a[i + 1]
                a[i + 1] ← temp
            END IF
        END FOR
    END FOR
END ALGORITHM
~~~

## BINARY SEARCH

~~~text
ALGORITHM BinarySearch(a, n, key)
    first ← 0
    last ← n - 1

    WHILE first ≤ last
        mid ← (first + last) / 2

        IF a[mid] = key THEN
            RETURN mid
        ELSE IF a[mid] > key THEN
            last ← mid - 1
        ELSE
            first ← mid + 1
        END IF
    END WHILE

    RETURN -1
END ALGORITHM
~~~

## MAIN

~~~text
READ n
READ n array elements
CALL BubbleSort(a, n)
READ key
position ← BinarySearch(a, n, key)

IF position ≠ -1 THEN
    OUTPUT "Element found at position", position + 1
ELSE
    OUTPUT "Element not found"
END IF
~~~

**Time:** Bubble sort takes O(n²). Binary search takes O(log n) after sorting. The complete program is dominated by the sorting step, so its overall time complexity is O(n²). Binary search uses O(1) extra space.
