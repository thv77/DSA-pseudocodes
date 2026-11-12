# Pseudocode: Polynomial Addition Using Arrays

Both polynomials have the same highest order n. Each array holds n + 1 coefficients, written from the highest power down to the constant term, so index k holds the coefficient of x^(n - k).

~~~text
ALGORITHM AddPolynomialsUsingArrays
    READ n
    READ a[0 ... n]          // first polynomial, highest power first
    READ b[0 ... n]          // second polynomial, highest power first

    FOR k ← 0 TO n
        c[k] ← a[k] + b[k]
    END FOR

    OUTPUT "The resultant polynomial is"
    FOR k ← 0 TO n
        IF c[k] ≠ 0 THEN
            OUTPUT c[k] "x^" (n - k)
        END IF
        IF k < n THEN
            OUTPUT "+"
        END IF
    END FOR
END ALGORITHM
~~~

Terms whose resulting coefficient is zero are not displayed.

**Time:** O(n). **Space:** O(n).

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
