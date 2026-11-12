# Pseudocode: Stack Operations Using an Array

A stack follows **LIFO** (Last In, First Out). The program keeps an array `stack` of capacity MAX (5) and `top ← -1`, and repeats a menu until the user chooses EXIT.

## MAIN MENU

~~~text
ALGORITHM StackMenu
    top ← -1
    LOOP
        OUTPUT "1.PUSH  2.POP  3.DISPLAY  4.EXIT"
        READ choice

        IF choice = 1 THEN
            CALL Push
        ELSE IF choice = 2 THEN
            CALL Pop
        ELSE IF choice = 3 THEN
            CALL DisplayStack
        ELSE IF choice = 4 THEN
            EXIT LOOP
        ELSE
            OUTPUT "Invalid Choice"
        END IF
    END LOOP
END ALGORITHM
~~~

## PUSH

~~~text
ALGORITHM Push
    IF top = MAX - 1 THEN
        OUTPUT "Stack overflow"
    ELSE
        READ item
        top ← top + 1
        stack[top] ← item
        OUTPUT "The element", item, "pushed into the stack"
    END IF
END ALGORITHM
~~~

## POP

~~~text
ALGORITHM Pop
    IF top = -1 THEN
        OUTPUT "Stack Underflow"
    ELSE
        item ← stack[top]
        top ← top - 1
        OUTPUT "The element", item, "popped from the stack"
    END IF
END ALGORITHM
~~~

## DISPLAY

~~~text
ALGORITHM DisplayStack
    IF top = -1 THEN
        OUTPUT "Stack is empty"
    ELSE
        OUTPUT "The stack elements are:"
        FOR i ← top DOWNTO 0
            OUTPUT stack[i]
        END FOR
    END IF
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
