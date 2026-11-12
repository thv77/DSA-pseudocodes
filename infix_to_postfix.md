# Pseudocode: Infix to Postfix Conversion

Use a stack for operators and parentheses. Assume single-character operands and operators +, -, *, /, and ^. Precedence: ^ above * and / above + and -. Exponentiation is right-associative.

~~~text
ALGORITHM InfixToPostfix(expression)
    CREATE empty stack S
    postfix ← empty sequence

    FOR each token x from left to right
        IF x is an operand THEN
            APPEND x TO postfix
        ELSE IF x = '(' THEN
            PUSH x ONTO S
        ELSE IF x = ')' THEN
            WHILE S is not empty AND TOP(S) ≠ '('
                APPEND POP(S) TO postfix
            END WHILE
            IF S is empty THEN
                OUTPUT "Mismatched parentheses"
                RETURN ERROR
            END IF
            POP(S)
        ELSE IF x is an operator THEN
            WHILE S is not empty AND TOP(S) is an operator AND
                  (precedence(TOP(S)) > precedence(x) OR
                  (precedence(TOP(S)) = precedence(x) AND x ≠ '^'))
                APPEND POP(S) TO postfix
            END WHILE
            PUSH x ONTO S
        END IF
    END FOR

    WHILE S is not empty
        IF TOP(S) = '(' THEN
            OUTPUT "Mismatched parentheses"
            RETURN ERROR
        END IF
        APPEND POP(S) TO postfix
    END WHILE

    OUTPUT postfix
    RETURN postfix
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
