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
