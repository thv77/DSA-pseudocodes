# Pseudocode: Sparse Matrix Using Triplet Representation

Store only non-zero entries as triples (row, column, value). The first triple records the number of rows, columns, and non-zero values.

~~~text
ALGORITHM ConvertToTriplet(M, rows, cols)
    count ← 0

    FOR i ← 0 TO rows - 1
        FOR j ← 0 TO cols - 1
            IF M[i][j] ≠ 0 THEN
                count ← count + 1
            END IF
        END FOR
    END FOR

    CREATE triplet[0 ... count]
    triplet[0] ← (rows, cols, count)
    k ← 1

    FOR i ← 0 TO rows - 1
        FOR j ← 0 TO cols - 1
            IF M[i][j] ≠ 0 THEN
                triplet[k] ← (i, j, M[i][j])
                k ← k + 1
            END IF
        END FOR
    END FOR

    OUTPUT triplet
    RETURN triplet
END ALGORITHM
~~~

**Time:** O(rows × cols). **Space:** O(k), where k is the number of non-zero entries, plus the header.
