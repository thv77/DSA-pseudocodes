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

## C implementation

~~~c
#include<stdio.h>
void main()
{

 int a[100],i,n,elm,found=0;
 printf("enter the size of array: ");
 scanf("%d",&n);

 printf("enter the elements: ");

      for(i=0;i<n;i++)
      {
        scanf("%d",&a[i]);
      }
   
   printf("enter the element to search: ");
   scanf("%d",&elm);
   
                   for(i=0;i<n;i++)
                   {
                     if(a[i]==elm)
                     {
                       found=1;
                       break;
                       }
                    }
                    
                            if(found==1)
                             {
                               printf("the element %d found at position %d",elm, i);
                             }
                            else
                             {
                               printf("element not found");
                             }
}
~~~
