# Pseudocode: Postfix Expression Evaluation

Uses an integer stack. The expression contains single-digit operands and the operators +, -, *, and /.

~~~text
ALGORITHM EvaluatePostfix
    top ← -1
    READ postfix

    FOR i ← 0 TO LENGTH(postfix) - 1
        IF postfix[i] is a digit THEN
            PUSH(postfix[i] - '0')             // numeric value of the digit
        ELSE                                   // operator
            b ← POP()                          // right operand
            a ← POP()                          // left operand

            IF postfix[i] = '+' THEN
                result ← a + b
            ELSE IF postfix[i] = '-' THEN
                result ← a - b
            ELSE IF postfix[i] = '*' THEN
                result ← a * b
            ELSE IF postfix[i] = '/' THEN
                result ← a / b
            END IF

            PUSH(result)
        END IF
    END FOR

    OUTPUT "Result =", POP()
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
