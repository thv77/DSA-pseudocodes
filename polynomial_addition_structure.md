# Pseudocode: Polynomial Addition Using an Array of Structures

Each term is a record with coefficient and exponent. Assume each polynomial's terms are sorted by descending exponent.

~~~text
ALGORITHM AddPolynomialsUsingTerms(P, Q)
    i ← 0
    j ← 0
    R ← empty list

    WHILE i < LENGTH(P) AND j < LENGTH(Q)
        IF P[i].exponent = Q[j].exponent THEN
            sum ← P[i].coefficient + Q[j].coefficient
            IF sum ≠ 0 THEN
                APPEND (sum, P[i].exponent) TO R
            END IF
            i ← i + 1
            j ← j + 1
        ELSE IF P[i].exponent > Q[j].exponent THEN
            APPEND P[i] TO R
            i ← i + 1
        ELSE
            APPEND Q[j] TO R
            j ← j + 1
        END IF
    END WHILE

    APPEND all remaining terms of P to R
    APPEND all remaining terms of Q to R
    OUTPUT R
    RETURN R
END ALGORITHM
~~~

**Time:** O(m + n), where m and n are the numbers of terms. **Space:** O(m + n) for the result.
