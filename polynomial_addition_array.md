# Pseudocode: Polynomial Addition Using Arrays

Each array index represents a power of x; index i stores the coefficient of x^i. The arrays can have different lengths.

~~~text
ALGORITHM AddPolynomialsUsingArrays(P, m, Q, n)
    size ← MAX(m, n)
    CREATE array R[0 ... size - 1]

    FOR i ← 0 TO size - 1
        coefficientP ← 0
        coefficientQ ← 0

        IF i < m THEN
            coefficientP ← P[i]
        END IF
        IF i < n THEN
            coefficientQ ← Q[i]
        END IF

        R[i] ← coefficientP + coefficientQ
    END FOR

    OUTPUT R as a polynomial from highest power to lowest
    RETURN R
END ALGORITHM
~~~

Do not display terms whose resulting coefficient is zero.

**Time:** O(max(m, n)). **Space:** O(max(m, n)) for the result.

## C implementation

~~~c
#include<stdio.h>
void main()
{
  int n,i,j,k,a[10],b[10],c[10];
  printf("Enter the highest order of the polynomial: ");
  scanf("%d",&n);
        
        printf("\n Enter the first polynomial: ");
        for(i=0;i<=n;i++)
        {
         scanf("%d",&a[i]);
        }
        
             printf("\n Enter the second polynomial: ");
             for(j=0;j<=n;j++);
             {
              scanf("%d",&b[j]);
             }
                 
                   for(i=0,j=0,k=0;k<=n;k++,j++,i++)
                   {
                     c[k]=b[j]+a[i];
                   }
                   
                      printf("\n The resultant polynomial is ");
                      {
                        for(k=0;k<=n;k++)
                         {
                           if(c[k]!=0)
                            {
                              printf("%dx^%d",c[k],n-k);
                             }
                            if(k<n)
                            {
                             printf("+");
                            }
                         }
                      } 
                            
                         
   }                
             
~~~
