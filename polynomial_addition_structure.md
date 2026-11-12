# Pseudocode: Polynomial Addition Using an Array of Structures

A structure `poly` holds two arrays: `coeff[]` and `exp[]`. Three structures are used: x[0] for the first polynomial, x[1] for the second, and x[2] for the sum. Terms of each polynomial are entered in descending order of exponent.

~~~text
ALGORITHM AddPolynomialsUsingStructures
    READ n1                              // highest order of first polynomial
    FOR i ← 0 TO n1
        READ x[0].coeff[i], x[0].exp[i]
    END FOR

    READ n2                              // highest order of second polynomial
    FOR j ← 0 TO n2
        READ x[1].coeff[j], x[1].exp[j]
    END FOR

    i ← 0
    j ← 0
    k ← 0

    WHILE i ≤ n1 AND j ≤ n2
        IF x[0].exp[i] > x[1].exp[j] THEN
            x[2].exp[k] ← x[0].exp[i]
            x[2].coeff[k] ← x[0].coeff[i]
            i ← i + 1
        ELSE IF x[0].exp[i] < x[1].exp[j] THEN
            x[2].exp[k] ← x[1].exp[j]
            x[2].coeff[k] ← x[1].coeff[j]
            j ← j + 1
        ELSE
            x[2].exp[k] ← x[1].exp[j]
            x[2].coeff[k] ← x[0].coeff[i] + x[1].coeff[j]
            i ← i + 1
            j ← j + 1
        END IF
        k ← k + 1
    END WHILE

    WHILE i ≤ n1                         // remaining terms of first polynomial
        x[2].exp[k] ← x[0].exp[i]
        x[2].coeff[k] ← x[0].coeff[i]
        i ← i + 1
        k ← k + 1
    END WHILE

    WHILE j ≤ n2                         // remaining terms of second polynomial
        x[2].exp[k] ← x[1].exp[j]
        x[2].coeff[k] ← x[1].coeff[j]
        j ← j + 1
        k ← k + 1
    END WHILE

    OUTPUT "The sum:"
    FOR t ← 0 TO k - 1
        IF x[2].coeff[t] ≠ 0 THEN
            IF x[2].exp[t] = 0 THEN
                OUTPUT x[2].coeff[t]
            ELSE
                OUTPUT x[2].coeff[t] "x^" x[2].exp[t]
            END IF
        END IF
        IF t < k - 1 THEN
            OUTPUT "+"
        END IF
    END FOR
END ALGORITHM
~~~

**Time:** O(n1 + n2). **Space:** O(n1 + n2) for the result.

## C implementation

~~~c
#include<stdio.h>
void main()
{
  struct poly
  {
    int exp[10];
    int coeff[10];
   }x[3];
     
      int n1,n2,m,i,j,k;
       
      printf("Enter the highest order of first polynomial: " );
      scanf("%d",&n1);
      printf("Enter the first polynomial: ");
      for(i=0;i<=n1;i++)
      {
       scanf("%d%d",&x[0].coeff[i],&x[0].exp[i]);
       }
       
           printf("Enter the highest order of second polynomial: " );
           scanf("%d",&n2);
           printf("Enter the second polynomial: ");
           for(j=0;j<=n2;j++)
           {
            scanf("%d%d",&x[1].coeff[j],&x[1].exp[j]);
           }
               
                   if(n1>n2)
                   {
                     m=n1;
                    }
                   else if(n1==n2)
                   {
                    m=n2;
                   }
                   else
                    {
                    m=n2;
                    }
                    
                          for(i=0,j=0,k=0;k<=m;k++)
                          {
                           if(x[0].exp[i]>x[1].exp[j])
                            {
                             x[2].exp[k]=x[0].exp[i];
                             x[2].coeff[k]=x[0].coeff[i];
                             i++;
                             }
                            else if(x[0].exp[i]<x[1].exp[j]) 
                            {
                              x[2].exp[k]=x[1].exp[j];
                              x[2].coeff[k]=x[1].coeff[j];
                              j++;
                             }
                              
                             else if(x[0].exp[i]==x[1].exp[j]) 
                            {
                              x[2].exp[k]=x[1].exp[j];
                              x[2].coeff[k]=x[1].coeff[j]+x[0].coeff[i];
                              i++;
                              j++;
                             }
                              else if(i>j)
                              {
                                x[2].exp[k]=x[0].exp[i];
                                x[2].coeff[k]=x[0].coeff[i];
                                i++
                               }
                               
                              else
                              {
                               x[2].exp[k]=x[1].exp[j];
                               x[2].coeff[k]=x[1].coeff[j];
                               j++;
                               }
                             }
                             
                                    
                                    printf("The sum: \n");
                                    for(k=0;k<=m;k++)
                                    {
                                      if(x[2].coeff[k]!=0)
                                      {
                                       if(x[2].exp[k]==0)
                                       {
                                        printf("%d",x[2].coeff[k]);
                                       }
                                        else
                                        {
                                         printf("%dx^%d",x[2].coeff[k],x[2].exp[k]);
                                         }
                                      }
                                         
                                         if(k<m)
                                         {
                                          printf("+");
                                          }
                                      }
}
                              
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             
                             

~~~
