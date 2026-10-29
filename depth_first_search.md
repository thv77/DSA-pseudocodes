# Pseudocode: Depth-First Search (DFS)

DFS explores as far as possible along each branch before backtracking. This iterative version uses a stack and an adjacency matrix G; vertices are numbered from 0 to V - 1.

~~~text
ALGORITHM DFS(G, V, start)
    CREATE visited[0 ... V - 1], initialized to FALSE
    CREATE empty stack S
    PUSH(S, start)

    WHILE S is not empty
        u ← POP(S)
        IF visited[u] = FALSE THEN
            visited[u] ← TRUE
            OUTPUT u

            FOR v ← V - 1 DOWNTO 0
                IF G[u][v] ≠ 0 AND visited[v] = FALSE THEN
                    PUSH(S, v)
                END IF
            END FOR
        END IF
    END WHILE
END ALGORITHM
~~~

The order of neighbors pushed affects traversal order. This visits only vertices reachable from start; repeat from unvisited vertices to cover a disconnected graph.

**Time:** O(V²) with an adjacency matrix. **Extra space:** O(V).
