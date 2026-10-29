# Pseudocode: Breadth-First Search (BFS)

BFS visits graph vertices level by level using a queue. G is an adjacency matrix; vertices are numbered from 0 to V - 1.

~~~text
ALGORITHM BFS(G, V, start)
    CREATE visited[0 ... V - 1], initialized to FALSE
    CREATE empty queue Q
    visited[start] ← TRUE
    ENQUEUE(Q, start)

    WHILE Q is not empty
        u ← DEQUEUE(Q)
        OUTPUT u

        FOR v ← 0 TO V - 1
            IF G[u][v] ≠ 0 AND visited[v] = FALSE THEN
                visited[v] ← TRUE
                ENQUEUE(Q, v)
            END IF
        END FOR
    END WHILE
END ALGORITHM
~~~

This visits only vertices reachable from start. To traverse a disconnected graph, start BFS again at each unvisited vertex.

**Time:** O(V²) with an adjacency matrix. **Extra space:** O(V).
