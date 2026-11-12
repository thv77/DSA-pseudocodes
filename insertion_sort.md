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

## C implementation

~~~c
#include <stdio.h>

int main(void)
{
    int a[20], n, i, j, key, temp;

    printf("Enter the limit of the array: ");
    scanf("%d", &n);

    printf("Enter the %d elements: ", n);

    for (i = 0; i < n; i++)
    {
        scanf("%d", &a[i]);
    }

    for (i = 1; i < n; i++)
    {
        key = a[i];
        j = i - 1;

        while (j > -1 && a[j] > key)
        {
            a[j + 1] = a[j];
            j--;
        }

        a[j + 1] = key;
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
