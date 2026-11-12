# Pseudocode: Infix to Postfix Conversion

Uses a character stack for operators and parentheses. Operands are single letters or digits. Operator priority: `^` = 3, `*` and `/` = 2, `+` and `-` = 1, anything else (including `(`) = 0.

## HELPER: PRIORITY

~~~text
ALGORITHM Priority(ch)
    IF ch = '^' THEN
        RETURN 3
    ELSE IF ch = '*' OR ch = '/' THEN
        RETURN 2
    ELSE IF ch = '+' OR ch = '-' THEN
        RETURN 1
    ELSE
        RETURN 0
    END IF
END ALGORITHM
~~~

## MAIN ALGORITHM

~~~text
ALGORITHM InfixToPostfix
    top ← -1
    j ← 0
    READ infix

    FOR i ← 0 TO LENGTH(infix) - 1
        ch ← infix[i]

        IF ch is a letter or digit THEN
            postfix[j] ← ch
            j ← j + 1
        ELSE IF ch = '(' THEN
            PUSH(ch)
        ELSE IF ch = ')' THEN
            WHILE stack[top] ≠ '('
                postfix[j] ← POP()
                j ← j + 1
            END WHILE
            POP()                              // discard '('
        ELSE                                   // operator
            WHILE top ≠ -1 AND Priority(stack[top]) ≥ Priority(ch)
                postfix[j] ← POP()
                j ← j + 1
            END WHILE
            PUSH(ch)
        END IF
    END FOR

    WHILE top ≠ -1                             // pop remaining operators
        postfix[j] ← POP()
        j ← j + 1
    END WHILE

    OUTPUT "Postfix expression:", postfix
END ALGORITHM
~~~

**Time:** O(n). **Space:** O(n).

## C implementation

~~~c
#include <stdio.h>
#include <ctype.h> /* isalnum = is alpha numeric*/
#define MAX 100

char stack[MAX];
int top = -1;

             void push(char ch) /* first function */
                {
                 stack[++top] = ch;
                }
                
                  char pop() /* second function */
                    {
                      return stack[top--];
                    }
                    
                      int priority(char ch) /* third function */
                        {
                         if (ch == '^')
                          return 3;
                         else if (ch == '*' || ch == '/')
                          return 2;
                         else if (ch == '+' || ch == '-')
                          return 1;
                         else
                          return 0;
                        }
                        
 int main()
 {
  char infix[MAX], postfix[MAX];
  int i, j = 0;
  char ch;
  
  printf("Enter the infix expression: ");
  scanf("%s", infix);
  
        for (i = 0; infix[i] != '\0'; i++)
           {
            ch = infix[i];
                /* If operand, add to postfix */
                      if (isalnum(ch))
                       {
                        postfix[j++] = ch;
                       }
                       
                   /* If '(', push into stack */
                      else if (ch == '(')
                       {
                        push(ch);
                       }
                       
                   /* If ')', pop until '(' */
                      else if (ch == ')')
                       {
                        while (stack[top] != '(')
                         {
                          postfix[j++] = pop();
                         }
                          pop(); // Remove '('
                       }
                  /* If operator */
                      else
                       {
                        while (top != -1 && priority(stack[top]) >= priority(ch))
                           {
                            postfix[j++] = pop();
                           }
                            push(ch);
                       }
             }

                                               /* Pop remaining operators */
                                                   while (top != -1)
                                                     {
                                                       postfix[j++] = pop();
                                                     }
                                                       postfix[j] = '\0';
                                                       printf("Postfix expression: %s\n", postfix);
                                                       return 0;
} 
~~~
