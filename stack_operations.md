# Pseudocode: Stack Operations Using an Array

A stack follows **LIFO** (Last In, First Out). Initialize top ← -1 for an array of capacity MAX.

## PUSH

~~~text
ALGORITHM Push(stack, top, MAX, item)
    IF top = MAX - 1 THEN
        OUTPUT "Stack Overflow"
        RETURN top
    END IF
    top ← top + 1
    stack[top] ← item
    RETURN top
END ALGORITHM
~~~

## POP

~~~text
ALGORITHM Pop(stack, top)
    IF top = -1 THEN
        OUTPUT "Stack Underflow"
        RETURN (top, EMPTY)
    END IF
    item ← stack[top]
    top ← top - 1
    RETURN (top, item)
END ALGORITHM
~~~

## DISPLAY

~~~text
ALGORITHM DisplayStack(stack, top)
    IF top = -1 THEN
        OUTPUT "Stack is empty"
        RETURN
    END IF
    FOR i ← top DOWNTO 0
        OUTPUT stack[i]
    END FOR
END ALGORITHM
~~~

**Time:** Push O(1), Pop O(1), Display O(n). **Space:** O(MAX).

## C implementation

~~~c
#include<stdio.h>
#define max 5
int main()
{
   int stack[max],choice,item,i;
   int top=-1;
   
       while(1)
       {
         printf("\n STACK \n");
         printf("\n 1.PUSH \n");
         printf("\n 2.POP \n");
         printf("\n 3.DISPLAY \n");
         printf("\n 4.EXIT \n");
         
         printf("\n Enter your choice: \n");
         scanf("%d",&choice);
         
                 if(choice==1)
                 { 
                  if(top=max-1)
                  {
                   printf("Stack overflow");
                  }
                  else
                  {
                   printf("Enter the element: ");
                   scanf("%d",&item);
                   top=top+1;
                   stack[top]=item;
                   printf("The element %d pushed into the stack",item);
                   }
                  }
                  
                  else if(choice==2)
                  {
                   if(top=-1)
                   {
                    printf("Stack Underflow");
                   }
                   else 
                   {
                    item=stack[top];
                    top=top-1;
                    printf("The element %d poped from the stack",item);
                   }
                  }
                  
                  else if(choice==3)
                  {
                   if(top==-1)
                   {
                    printf("Stack is empty");
                   }
                   else
                   {
                    printf("The stack elements are: ");
                     for(i=top;i>=0;i--)
                      {
                       printf("%d",stack[i]);
                       }
                    }
                    }
                    else if(choice==4)
                    break;
                    
                    else
                    {
                     printf("Invalid Choice");
                    }
                    return 0;
               }
            
  }                  
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                   
   
   
~~~
