# Pseudocode: Sparse Matrix Using Triplet Representation

Store only non-zero entries as triples (row, column, value). The first triple records the number of rows, columns, and non-zero values.

~~~text
ALGORITHM ConvertToTriplet(M, rows, cols)
    count ← 0

    FOR i ← 0 TO rows - 1
        FOR j ← 0 TO cols - 1
            IF M[i][j] ≠ 0 THEN
                count ← count + 1
            END IF
        END FOR
    END FOR

    CREATE triplet[0 ... count]
    triplet[0] ← (rows, cols, count)
    k ← 1

    FOR i ← 0 TO rows - 1
        FOR j ← 0 TO cols - 1
            IF M[i][j] ≠ 0 THEN
                triplet[k] ← (i, j, M[i][j])
                k ← k + 1
            END IF
        END FOR
    END FOR

    OUTPUT triplet
    RETURN triplet
END ALGORITHM
~~~

**Time:** O(rows × cols). **Space:** O(k), where k is the number of non-zero entries, plus the header.

## C implementation

~~~c
#include<stdio.h>
void main()
{
 int m,n,i,j,a[10][10],b[10][3],c=0,k=1;
  
   printf("enter the matrix rows");
   scanf("%d",&m);
   printf("enter the matrix column");
   scanf("%d",&n);
   
        printf("enter the elements of %dx%d matrix",m,n);
        for(i=0;i<m;i++)
        {
         for(j=0;j<n;j++)
            {
              scanf("%d",&a[i][j]);
             }
         }
             
                
                    for(i=0;i<m;i++)
                      {
                       for(j=0;j<n;j++)
                         {
                           if(a[i][j]!=0)
                           {
                            c++;
                            }
                         }
                      }
                      
b[0][0]=m;
b[0][1]=n;
b[0][2]=c;
             printf("sparse matrix:/n "); 
            for(i=0;i<m;i++)
                      {
                       for(j=0;j<n;j++)
                         {
                           if(a[i][j]!=0)
                           {
                            b[k][0]=i;
                            b[k][1]=j;
                            b[k][2]=a[i][j];
                            k++;
                            }
                          }
                        }
                        
                        
                        printf("the resultant sparse matrix in triplet: \n");
                        for(i=0;i<=c;i++)
                          {
                            for(j=0;j<3;j++)
                            {
                              printf("%d\t",b[i][j]);
                              }
                                printf("\n");
                           }
}                  
                        
                        
                        
                        
                        
                        
                        
                        
                        
                        
                       
~~~
