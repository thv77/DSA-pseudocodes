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
