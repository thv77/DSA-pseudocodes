# Pseudocode: Merge Sort

Merge sort uses divide and conquer: recursively sort each half, then merge the sorted halves. A global array `b` is used as the temporary storage while merging.

## MAIN

~~~text
ALGORITHM Main
    READ n
    IF n < 1 OR n > 20 THEN
        OUTPUT "Invalid number of elements"
        STOP
    END IF

    READ a[0 ... n - 1]
    CALL MergeSort(a, 0, n - 1)

    OUTPUT "The sorted elements are:"
    OUTPUT a[0 ... n - 1]
END ALGORITHM
~~~

## MERGE SORT

~~~text
ALGORITHM MergeSort(a, low, high)
    IF low < high THEN
        mid ← (low + high) / 2
        MergeSort(a, low, mid)
        MergeSort(a, mid + 1, high)
        Merge(a, low, mid, high)
    END IF
END ALGORITHM
~~~

## MERGE TWO SORTED PARTS

~~~text
ALGORITHM Merge(a, low, mid, high)
    i ← low
    j ← mid + 1
    k ← low

    WHILE i ≤ mid AND j ≤ high
        IF a[i] < a[j] THEN
            b[k] ← a[i]
            i ← i + 1
        ELSE
            b[k] ← a[j]
            j ← j + 1
        END IF
        k ← k + 1
    END WHILE

    WHILE i ≤ mid
        b[k] ← a[i]
        i ← i + 1
        k ← k + 1
    END WHILE

    WHILE j ≤ high
        b[k] ← a[j]
        j ← j + 1
        k ← k + 1
    END WHILE

    FOR i ← low TO high
        a[i] ← b[i]
    END FOR
END ALGORITHM
~~~

**Initial call:** MergeSort(a, 0, n - 1)  
**Time:** O(n log n) in all cases. **Auxiliary space:** O(n).

## C implementation

~~~c
#include <stdio.h>

int b[20];

void mergesort(int a[], int low, int high);
void merge(int a[], int low, int mid, int high);

int main(void)
{
    int i, n, a[20];

    printf("Enter the number of elements: ");
    scanf("%d", &n);

    if (n < 1 || n > 20)
    {
        printf("Invalid number of elements\n");
        return 1;
    }

    printf("Enter the %d numbers: ", n);

    for (i = 0; i < n; i++)
    {
        scanf("%d", &a[i]);
    }

    mergesort(a, 0, n - 1);

    printf("The sorted elements are:\n");

    for (i = 0; i < n; i++)
    {
        printf("%d\t", a[i]);
    }

    printf("\n");

    return 0;
}

void mergesort(int a[], int low, int high)
{
    int mid;

    if (low < high)
    {
        mid = (low + high) / 2;

        mergesort(a, low, mid);
        mergesort(a, mid + 1, high);

        merge(a, low, mid, high);
    }
}

void merge(int a[], int low, int mid, int high)
{
    int i, j, k;

    i = low;
    j = mid + 1;
    k = low;

    while (i <= mid && j <= high)
    {
        if (a[i] < a[j])
        {
            b[k] = a[i];
            i++;
            k++;
        }
        else
        {
            b[k] = a[j];
            j++;
            k++;
        }
    }

    while (i <= mid)
    {
        b[k] = a[i];
        i++;
        k++;
    }

    while (j <= high)
    {
        b[k] = a[j];
        j++;
        k++;
    }

    for (i = low; i <= high; i++)
    {
        a[i] = b[i];
    }
}

~~~
