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

## C implementation

~~~c
#include <stdio.h>

int main(void)
{
    int a[20], i, j, loc, min, n, temp;

    printf("Enter the size of the array: ");
    scanf("%d", &n);

    printf("Enter the %d elements: ", n);

    for (i = 0; i < n; i++)
    {
        scanf("%d", &a[i]);
    }

    for (i = 0; i < n; i++)
    {
        min = a[i];
        loc = i;

        for (j = i + 1; j < n; j++)
        {
            if (a[j] < min)
            {
                min = a[j];
                loc = j;
            }
        }

        temp = a[i];
        a[i] = min;
        a[loc] = temp;
    }

    printf("The sorted array is:\n");

    for (i = 0; i < n; i++)
    {
        printf("%d\t", a[i]);
    }

    printf("\n");

    return 0;
}

~~~
