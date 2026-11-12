# Pseudocode: Postfix Expression Evaluation

Use a stack to evaluate postfix expressions. Assume single-digit operands and operators +, -, *, and /.

~~~text
ALGORITHM EvaluatePostfix(expression)
    CREATE empty stack S

    FOR each token x from left to right
        IF x is an operand THEN
            PUSH numeric value of x ONTO S
        ELSE IF x is an operator THEN
            IF SIZE(S) < 2 THEN
                OUTPUT "Invalid postfix expression"
                RETURN ERROR
            END IF

            right ← POP(S)
            left ← POP(S)

            IF x = '+' THEN
                result ← left + right
            ELSE IF x = '-' THEN
                result ← left - right
            ELSE IF x = '*' THEN
                result ← left * right
            ELSE IF x = '/' THEN
                IF right = 0 THEN
                    OUTPUT "Division by zero"
                    RETURN ERROR
                END IF
                result ← left / right
            END IF

            PUSH result ONTO S
        END IF
    END FOR

    IF SIZE(S) ≠ 1 THEN
        OUTPUT "Invalid postfix expression"
        RETURN ERROR
    END IF
    RETURN POP(S)
END ALGORITHM
~~~

Pop the right operand first and then the left operand; this matters for subtraction and division.

**Time:** O(n). **Space:** O(n).

## C implementation

~~~c
#include <stdio.h>
#include <ctype.h> /* isdigit */
#define MAX 100

int stack[MAX];
int top = -1;

      void push(int value)
       {
        stack[++top] = value;
       }
          int pop()
           {
             return stack[top--];
           }
 int main()
 {
  char postfix[MAX];
  int i, a, b, result;
  
  printf("Enter the postfix expression: ");
  scanf("%s", postfix);
  
  
       for (i = 0; postfix[i] != '\0'; i++)
        {
          /* If operand, push it into stack */
           if (isdigit(postfix[i]))
            {
             push(postfix[i] - '0');
            }
            
           /* If operator, perform operation */
           else
            {
             b = pop();
             a = pop();
             
                         switch (postfix[i])
                          {
                           case '+':
                           result = a + b;
                           break;

                           case '-':
                           result = a - b;
                           break;
                           
                           case '*':
                           result = a * b;
                           break;
                           
                           case '/':
                           result = a / b;
                           break;
                          }
                           push(result);
             }
         }
          printf("Result = %d\n", pop());
          return 0;
}
~~~
