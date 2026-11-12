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
