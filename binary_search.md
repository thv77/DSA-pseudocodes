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

## C implementation

~~~c
#include <stdio.h>

int main(void)
{
    int n, i, a[10], key, flag = 0;
    int j, temp, first, last, mid;

    printf("Enter the limit of the array: ");
    scanf("%d", &n);

    printf("Enter the %d elements: ", n);

    for (i = 0; i < n; i++)
    {
        scanf("%d", &a[i]);
    }

    for (j = 1; j < n; j++)
    {
        for (i = 0; i < n - j; i++)
        {
            if (a[i] > a[i + 1])
            {
                temp = a[i];
                a[i] = a[i + 1];
                a[i + 1] = temp;
            }
        }
    }

    printf("Enter the key: ");
    scanf("%d", &key);

    first = 0;
    last = n - 1;

    while (first <= last)
    {
        mid = (first + last) / 2;

        if (a[mid] == key)
        {
            printf("The element is found in %d", mid + 1);
            flag = 1;
            break;
        }
        else if (a[mid] > key)
        {
            last = mid - 1;
        }
        else
        {
            first = mid + 1;
        }
    }

    if (flag == 0)
    {
        printf("The element is not found");
    }

    return 0;
}

~~~
