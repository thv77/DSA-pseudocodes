# Pseudocode: Selection Sort

Selection sort repeatedly finds the smallest element in the unsorted section and swaps it into the next position.

~~~text
ALGORITHM SelectionSort
    READ n
    READ a[0 ... n - 1]

    FOR i ← 0 TO n - 1
        min ← a[i]
        loc ← i

        FOR j ← i + 1 TO n - 1
            IF a[j] < min THEN
                min ← a[j]
                loc ← j
            END IF
        END FOR

        temp ← a[i]
        a[i] ← min
        a[loc] ← temp
    END FOR

    OUTPUT "The sorted array is:"
    OUTPUT a[0 ... n - 1]
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
