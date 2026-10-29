# Pseudocode: Polynomial Addition Using Arrays

Each array index represents a power of x; index i stores the coefficient of x^i. The arrays can have different lengths.

~~~text
ALGORITHM AddPolynomialsUsingArrays(P, m, Q, n)
    size ← MAX(m, n)
    CREATE array R[0 ... size - 1]

    FOR i ← 0 TO size - 1
        coefficientP ← 0
        coefficientQ ← 0

        IF i < m THEN
            coefficientP ← P[i]
        END IF
        IF i < n THEN
            coefficientQ ← Q[i]
        END IF

        R[i] ← coefficientP + coefficientQ
    END FOR

    OUTPUT R as a polynomial from highest power to lowest
    RETURN R
END ALGORITHM
~~~

Do not display terms whose resulting coefficient is zero.

**Time:** O(max(m, n)). **Space:** O(max(m, n)) for the result.
